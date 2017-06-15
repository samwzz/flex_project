# Gluteno

### Background

This app helps people with Celiac’s disease find restaurants they trust.

Celiac’s disease is a serious autoimmune disease, for which a 100% gluten-free diet is the only existing treatment. It can be time-consuming and expensive process to experiment with restaurants. We want to create a an app for people with celiac’s based on a thumbs-up thumbs-down system to help others determine if the establishment is safe for those with Celiac’s.

### Functionality & MVP

Using this app, users will be able to:

- [ ] Create new account, login (user authentication)
- [ ] See all gluten free restaurants
- [ ] Search for restaurants on Google Places
- [ ] Add restaurants to database
- [ ] Restaurant rating (thumbs up/ thumbs down) via swiping

### Wireframes

Screens

![screens](/docs/wireframes/Screens.png)

Login

![login](/docs/wireframes/1.login.png)

Sign up

![signup](/docs/wireframes/2.signUp.png)

Home View

![chat](/docs/wireframes/3.homeView.png)

Search Results

![settings](/docs/wireframes/4.searchResults.png)

Restaurant Show

![groups](/docs/wireframes/5.restaurantShow.png)

Restaurant Add

![users](/docs/wireframes/6.restaurantAdd.png)


### Technologies & Technical Challenges

This app will utilize React Native on the frontend and Django on the backend. In addition, it will integrate Google Maps and Google Places API.

The primary technical challenges will be:

- Using React Native to create an attractive user interface and a fluid navigation experience
- Integrating a React Native frontend with Django backend

### Things we accomplished this weekend.

1. Yong and Allen learned Python and Django fundamentals, completed tutorials online, and set up a Django server
2. Sam and Vu learned React Native, completed the Facebook React Native tutorial, and converted past React projects to React Native

### Group Members & Work Breakdown

Our group consists of four members, Yong Lin, Allen Chen, Vu Pham, and Sam Wang.

Yong's primary responsibilities will be:

- Learning Python/Django and implementing user authentication
- Researching Google Places API and  integrating retrieved data with the app database
- Architecting a database model that fits the app's needs

Allen's primary responsiblities will be:

- Learning Python/Django and implementing user authentication
- Architecting a database model that fits the app's needs
- Researching Google Places API

Vu's Primary responsiblities will be:

- Learning React Native and the Ignite architecture
- Design user interface and set up style guide to ensure cohesive color scheme and font
- Building authentication page with styling and functioning redux cycles
- Building landing and search results page

Sam's Primary responsiblities will be:

- Learning React Native and the Ignite architecture
- Understanding the Google Places API and integrating response data with restaurant form
- Building restaurant form page
- Building restaurant show page and integrate Google Maps API

### Implementation Timeline

**Day 1**: Set up the framework upon which to build the app. By the end of the day, we will have:
- Configured authentication on Django framework for user creation and session management (Yong)
- Research Google Maps/Places API for implementation (Allen)
- Two styled authentication pages without associated Redux cycle (Vu)
- Become familiar with Google Places API and start working on a landing page (Sam)

**Day 2**: Finish authentication and prepare for restaurant search. By the end of the day, we will have:

- Prepared the backend for new restaurant creation and retrieval of database restaurants (Allen)
- Format JSON response to be received by the frontend for views and create restaurant seed data (Yong)
- A functioning Redux cycle for authentication (Vu)
- Landing page with associated Redux cycle (Sam)

**Day 3**: Finish restaurant search. Get started on likes and dislikes. By the end of the day, we will have:

- Create joins table for likes and dislikes (Yong)
- Compile data on businesses offering gluten-free options (Allen)
- Search results page with associated Redux cycle (Sam)
- Create one styled restaurant form page without associated Redux cycle (Vu)

**Day 4**: Finish restaurant creation and show page.By the end of the day, we will have:

- A detailed README (Allen)
- Get started on single page website that explains the purpose of the app and links to download (Yong)
- A functioning Redux cycle for adding new restaurants (Vu)
- A styled restaurant show page and associated Redux cycle (Sam)

**Day 5**: Create website to demo project. By the end of the day, we will have:

- Finish making website (Yong)
- Add gifs and screenshots to README, seed database (Allen)
- Add emulator to demo app (Sam)
- Finish styling any pages (Vu)

### Future Features

- [ ] Restaurant reviews
- [ ] Contact via phone/text
- [ ] Map view on search results page
- [ ] User profile for favorites list
- [ ] Learn user preferences and offer recommendations (explore restaurant)
