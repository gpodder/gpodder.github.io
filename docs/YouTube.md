These are instructions to subscribe to user channels in YouTube - post June 2015.

Why do I need to do this?
-------------------------

There is no more transparent relation between user name and RSS feed. gPodder needs to use the google YouTube API to convert the user name (e.g. *Pentadact*) to an RSS feed (e.g. <https://www.youtube.com/feeds/videos.xml?channel_id=UCQ-twzO6v-PBgckhkrXVaDQ>). To do so, it must provide an API key to google to be granted access to the API. There are quotas in place for each key, so the gPodder devs can't simply give a key for everyone to use. Everyone has to get his own.

How do I do it ?
----------------

We will follow <https://developers.google.com/youtube/v3/getting-started?hl=fr>

1. You need a google account (your gmail address).

2. Go to <https://console.developers.google.com/>

  *  Login with your google account.

3. Click the button *Create a project*

  *  Name it whatever you want (e.g. gPodderAPI)

4. Go to *API & auth* &gt; *APIs*

  *  Search for / click on YouTube Data API
  *  Click *Enable*

5. Go to *API & auth* &gt; *Credentials*

  *  In the *Public API access* section, click on the *create new key* button
  *  Choose *Browser key*
  *  Don't enter anything in the HTTP referers text area
  *  Click the *Create* button

6. Your API key appears.

  *  Copy the long string of letters and numbers

7. Open gPodder 3.8.4 or later

  *  Activate the *Extras* > *Update YouTube subscriptions* menu item
  *  Click YES to enter your API key
  *  Paste your API key in the *Youtube api key (v3)* field.
  *  Close the settings window.
  *  Activate the *Extras* > *Update YouTube subscriptions* menu item again.

8. You're done