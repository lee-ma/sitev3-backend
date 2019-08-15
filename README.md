# Spotify Most Recently Played

This is a small express API that you can use to get your currently playing or most recently played song on Spotify without having to authenticate with Spotify OAuth. Currently, Spotify requires an OAuth login to occur, and then they have a public endpoint at `/me` which will get the authenticated user's information. If you only want your data, you'll have to continually ping with a websocket or timeout and refresh a login token. Or you can scrobble your data with lastFM, and use the Spotify search API to get spotify meta data, which is what this code does.

## Endpoints

`/recentlyPlayed`: This will return just the data about the most recent or current track played on spotify for the lastFM account associated with the spotify account that is being scrobbled.

`/spotifyTrack`: The parameters this accepts as a GET params is `title` and `artist`. This will get the actual spotify metadata including album art and spotify url.

## Getting Started

You will need to set up a lastFM account and an API key, and enable Spotify Scrobbling in your user account settings from lastFM. You will need to set up 4 environment variables and API keys from lastFM and Spotify.

1. `CORS_ORIGIN`: this will be the url that you plan to call the API from, for CORS
2. `LASTFM_URL`: this will be `http://ws.audioscrobbler.com/2.0/?method=user.getrecenttracks&user=<LASTFM_USERNAME>&api_key=<API_KEY>&format=json&limit=1`
3. `SPOTIFY_CLIENT_ID`: this will be your spotify client id that you get assigned from Spotify
4. `SPOTIFY_CLIENT_SECRET`: this will be your spotify client secret that you get assigned Spotify

To run locally:
1. Clone this repo
2. `cd spotify-most-recently-played`
3. `node server.js`
