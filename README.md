# GlutenGo

[GlutenGo][glutengo]

## Summary

More and more people are being diagnosed with [Celiac's disease](https://en.wikipedia.org/wiki/Coeliac_disease), which makes dining out a big headache. GlutenGo is a mobile app that makes it easier for people with Celiac's disease find gluten-free restaurants near a geographic location.

#### Frameworks/Libraries/External API's

GlutenGo uses:

- Django REST Framework
- PostgreSQL
- React Native (React Native Maps, React Navigation)
- Redux
- Google Places API
- Google Maps API
- Heroku for hosting the backend

## Implementation Details

### Overall Structure

#### Back end
The app was built using Django on the backend with a PostgreSQL database. It is a RESTful API endpoint that serves JSON responses to the front end. Associations are used to prefetch data in order to minimize SQL queries to the database.

#### Front end
The mobile app was built using the React Native framework to facilitate deployment to both Android and iOS. The Redux framework was used to manage data and state. Navigation and routing are handled using React Navigation.

### Authentication
It uses a token authentication system so the device can indefinitely access a valid, secure session.

```python
@receiver(post_save, sender=settings.AUTH_USER_MODEL)
def create_auth_token(sender, instance=None, created=False, **kwargs):
    if created:
        Token.objects.create(user=instance)
```

An access token is required to make calls to the API endpoint. A token is sent to the client upon authentication and stored in the device's local AsyncStorage, thereby persisting a secure user session. Upon logout, the access token is removed from AsyncStorage.

```javascript
APIUtil.login(user)
    .then((response) => response.json())
    .then((responseJson) => {
      if (responseJson.status >= 200 && responseJson.status < 300) {
        // Handle success
        const { token, user_id, username } = responseJson;
        // On success we will store the access_token in the AsyncStorage
        storeToken(token);
        dispatch(receiveCurrentUser({ user_id, username }));
      } else {
        //Handle error
        let error = responseJson;
        throw error;
      }
    })
    .catch((errors) => {
      dispatch(receiveErrors(errors));
    })
```
Fetching data from API endpoint:

```javascript
AsyncStorage.getItem(ACCESS_TOKEN)
  .then(token =>
    fetch('https://glutenbackend.herokuapp.com/api/restaurants/', {
      method: 'GET',
      headers: {
        'Accept': 'application/json',
        'Content-Type': 'application/json',
        'Authorization': 'Token ' + token
      }
    })
  )
```
Logging out:

```javascript
onLogoutPressed() {
  AsyncStorage.removeItem("access_token")
  .then(result => this.setState({ result: "" }))
  .then(() => this.props.navigation.navigate('Auth'));
}
```

### Maps

![map](/docs/images/map.png)

### Likes/Dislikes
Liking/disliking a restaurant will toggle your preference for that restaurant. When we receive a like, we query our database for the corresponding dislike (and vice versa), and removes it if it exists.

```python
@api_view(['POST'])
def create_like(request):

    dislike_list = Dislike.objects.filter(user=request.data['user']).filter(restaurant=request.data['restaurant'])
    for dislike in dislike_list:
        dislike.delete()

    if request.method == 'POST':
        serializer = LikeSerializer(data=request.data)
        if serializer.is_valid():
            serializer.save()
            return Response(serializer.data, status=201)
        return Response(serializer.errors, status=400)
```
## Future features
- Allow users to have their own list of favorite restaurants
- Allow users to upload pictures
- Online ordering
