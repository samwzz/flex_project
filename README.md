# GlutenGo

[GlutenGo][glutengo]

## Summary

More and more people are being diagnosed with [Celiac's disease](https://en.wikipedia.org/wiki/Coeliac_disease), which makes dining out a big headache. GlutenGo is a mobile app that allows people with Celiac's disease find gluten-free restaurants near their current location.

#### Frameworks/Libraries/External API's

GlutenGo uses:

- Django REST Framework
- PostgreSQL
- React Native
- Redux
- Google Places API
- Google Maps API
- Heroku for hosting the backend

## Implementation Details

### Overall Structure

#### Back end
The app was built using Django on the backend with a postgreSQL database. It is an RESTful API endpoint that serves JSON responses to the front end. Associations are used to prefetch data in order to minimize SQL queries to the database.

#### Front end
We utilized React Native to build the mobile front end.

### Authentication
It uses a token authentication system so the device can indefinitely access a valid, secure session.

```python
@receiver(post_save, sender=settings.AUTH_USER_MODEL)
def create_auth_token(sender, instance=None, created=False, **kwargs):
    if created:
        Token.objects.create(user=instance)
```
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
- Allows users to have their own list of favorite restaurants
- Allows users to upload pictures
- Online ordering
