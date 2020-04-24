# Spotify-playlists-backend

This service logs in to Spotify and redirects the user to a given frontend application with a valid access_token as a parameter in the url.

## Getting Started

To run this application locally have sure that you had the [NodeJs](https://nodejs.org) installed on your machine first (also as [Git](https://git-scm.com/downloads) optionaly to help clone this repo), then follow the workflow to the initial setup:

1. Fork & clone this repository;

   ```terminal
       git clone git@github.com/<my-username>/spotify-playlists-mm-backend.git my-api
   ```

2. Move inside to your cloned repo and then install the dependencies:

   ```terminal
       cd my-api && npm install
   ```

3. In development mode, it assumes you are running the frontend on localhost:3000, but the server itself will be running on localhost:8888. In order to start developing, register a Spotify Application [here](https://developer.spotify.com/my-applications). On that page, add http://localhost:8888 as a callback url. Write the below commands in your terminal:

   ```terminal
       export SPOTIFY_CLIENT_ID=PASTE_YOUR_CLIENT_ID_HERE
       export SPOTIFY_CLIENT_SECRET=PASTE_YOUR_CLIENT_SECRET_HERE
   ```

4. Start your application:
   `terminal npm start`
   Then go to http://localhost:8888/login in your browser. This will initiate the login flow and finally redirect to http://localhost:3000?access_token=ZZZZZ where ZZZZZ is a valid access token that you can use to do operations in the Spotify API.

## Deploying to production

This is intended to be deployed on Heroku. After installing the heroku CLI tools you can run the below commands in the same directory as server.js(replacing abc123, cba456, mybackend and myfrontend with your actual data - the below example assume that you already have your frontend running on http://myfrontend.herokuapp.com.

```terminal
heroku create my-backend --buildpack mars/create-react-app
heroku config:set SPOTIFY_CLIENT_ID=abc123
heroku config:set SPOTIFY_CLIENT_SECRET=cba456
heroku config:set REDIRECT_URI=https://mybackend.herokuapp.com/callback
heroku config:set FRONTEND_URI=https://myfrontend.herokuapp.com
git push heroku master
```

You should now be able to go to http://mybackend.herokuapp.com/login and it will eventually redirect to http://myfrontend.herokuapp.com?access_token=ZZZZZwhere ZZZZZ is a valid access token that you can use to do operations in the Spotify API.
