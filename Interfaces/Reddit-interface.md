Reddit interface
================

OctoBot uses the Reddit interface to monitor reddit posts from
subreddits given in **RedditForumEvaluator.json**. This interface
enables the social evaluator **RedditForumEvaluator**

Configuration
---------------------------

![reddit config](https://raw.githubusercontent.com/Drakkar-Software/OctoBot/assets/wiki_resources/reddit_config.png)

Those information can be found after creating a Reddit App.

1. Login on your Reddit account if you already have one
2. [Generate a Reddit script App to your Reddit account if you don't
    already have one](https://www.reddit.com/prefs/apps/)
3. **client-id** is the 14 characters identifier under the App's name
4. **client-secret** is the **secret** identifier of the App
5. **username** and **password** are your usual Reddit username and
    password

user/confg.json configuration
-----------------------------

Add in **user/config.json** in the services key :

``` json
"reddit": {
       "client-id": "YOUR_CLIENT_ID",
       "client-secret": "YOUR_CLIENT_SECRET",
       "username": "YOUR_REDDIT_USERNAME",
       "password": "YOUR_REDDIT_PASSWORD"
   }
```

**Exemple:**

``` json
"services": {
   "a service": {

   },
   "reddit": {
       "client-id": "YOUR_CLIENT_ID",
       "client-secret": "YOUR_CLIENT_SECRET",
       "username": "YOUR_REDDIT_USERNAME",
       "password": "YOUR_REDDIT_PASSWORD"
   },
   "another service": {

   }
}
```
