# liri-node-app | LIRI Bot

## OVERVIEW:
Make LIRI. LIRI is like iPhone's SIRI. 

### Notes to Consider: 
However, while SIRI is a Speech Interpretation and Recognition Interface, LIRI is a Language Interpretation and Recognition Interface. LIRI will be a command line node app that takes in parameters and gives you back data.

## BEFORE YOU BEGIN:
    LIRI will display your latest tweets. As we do not want to display your personal account, or its keys, please make an alias account and add a few tweets to it!
    Make a new GitHub repository called liri-node-app and clone it to your computer.
    To retrieve the data that will power this app, you'll need to send requests to the Twitter, Spotify and OMDB APIs. 
    
### You'll find these Node packages crucial for your assignment:
- [x] Twitter
- [x] Node-Spotify-API
- [x] Request [grab data from the OMDB API]
- [x] DotEnv

## SET UP STEPS

1. Navigate to the root of your project and run npm init -y — this will initialize a package.json file for your project. The package.json file is required for installing third party npm packages and saving their version numbers. If you fail to initialize a package.json file, it will be troublesome, and at times almost impossible for anyone else to run your code after cloning your project.

2. Make a .gitignore file and add the following lines to it. This will tell git not to track these files, and thus they won't be committed to Github.
    * node_modules
    * .DS_Store
    * .env
    
3. Make a JavaScript file named keys.js.
    
4. Inside keys.js your file will look like this:
    ```javascript
        console.log('this is loaded');

        exports.twitter = {
        consumer_key: process.env.TWITTER_CONSUMER_KEY,
        consumer_secret: process.env.TWITTER_CONSUMER_SECRET,
        access_token_key: process.env.TWITTER_ACCESS_TOKEN_KEY,
        access_token_secret: process.env.TWITTER_ACCESS_TOKEN_SECRET
        };

        exports.spotify = {
        id: process.env.SPOTIFY_ID,
        secret: process.env.SPOTIFY_SECRET
        };
    ```

5. Next, create a file named .env, add the following to it, replacing the values with your API keys (no quotes) once you have them:

**Spotify API keys**
    SPOTIFY_ID=your-spotify-id
    SPOTIFY_SECRET=your-spotify-secret

**Twitter API keys**
    TWITTER_CONSUMER_KEY=your-twitter-consumer-key
    TWITTER_CONSUMER_SECRET=your-twitter-consumer-secret
    TWITTER_ACCESS_TOKEN_KEY=your-access-token-key
    TWITTER_ACCESS_TOKEN_SECRET=your-twitter-access-token-secret

6. Get your Twitter API keys

7.  Make a file called random.txt.

8.  Inside of random.txt put the following in with no extra characters or white space:
    spotify-this-song,"I Want it That Way"

9.  Make a JavaScript file named liri.js.

10. At the top of the liri.js file, add code to read and set any environment variables with the dotenv package:
    require("dotenv").config();

11. Add the code required to import the keys.js file and store it in a variable.
    You should then be able to access your keys information like so
        var spotify = new Spotify(keys.spotify);
        var client = new Twitter(keys.twitter);

12. Make it so liri.js can take in one of the following commands:
    * `my-tweets`

    * `spotify-this-song`

    * `movie-this`

    * `do-what-it-says`

NOTE: Like the Twitter API, the Spotify API requires you sign up as a developer to generate the necessary credentials. 
    
13. You can follow these steps in order to generate a client id and client secret:
        Step One: Visit (https://developer.spotify.com/my-applications/#!/)
        Step Two: Either login to your existing Spotify account or create a new one (a free account is fine) and log in.
        Step Three: Once logged in, navigate to (https://developer.spotify.com/my-applications/#!/applications/create) to register a new application to be used with the Spotify API. You can fill in whatever you'd like for these fields. When finished, click the "complete" button.
        Step Four: On the next screen, scroll down to where you see your client id and client secret. Copy these values down somewhere, you'll need them to use the Spotify API and the node-spotify-api package.

14. What each command should do:
    *node liri.js my-tweets
        * This will show your last 20 tweets and when they were created at in your terminal/bash window.

15. You will utilize the node-spotify-api package in order to retrieve song information from the Spotify API.
    * node liri.js spotify-this-song '<song name here>'
        * This will show the following information about the song in your terminal/bash window
            * Artist(s)
            * The song's name
            * A preview link of the song from Spotify
            * The album that the song is from
        * If no song is provided then your program will default to "The Sign" by Ace of Base.

16. You'll use the request package to retrieve data from the OMDB API. Like all of the in-class activities, the OMDB API requires an API key. You may use trilogy.
    * node liri.js movie-this '<movie name here>'
        * This will output the following information to your terminal/bash window:
            * Title of the movie.
            * Year the movie came out.
            * IMDB Rating of the movie.
            * Rotten Tomatoes Rating of the movie.
            * Country where the movie was produced.
            * Language of the movie.
            * Plot of the movie.
            * Actors in the movie.
        * If the user doesn't type a movie in, the program will output data for the movie 'Mr. Nobody.'

17. Using the fs Node package, LIRI will take the text inside of random.txt and then use it to call one of LIRI's commands.
    * node liri.js do-what-it-says
        * It should run spotify-this-song for "I Want it That Way," as follows the text in random.txt.