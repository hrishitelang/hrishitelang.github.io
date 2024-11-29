---
layout: project
title: STACKS - Social Media Tracker, Analyzer, & Collector Toolkit at Syracuse (v2.0)
subtitle: "A social media research toolkit for Twitter/X"
---
STACKS (v 2.0) is the updated version of the previous [STACKS interface](https://github.com/bitslabsyr/stack). As of April 2021, STACKS v2.0 has been leveraged with its latest Python v3.9, along with its updated Mongo and PyMongo dependencies. The social media research toolkit was originally designed to collect, process, and store data from online social networks, majorly from social media APIs such as Twitter and Facebook. The interface is an ongoing project via the Syracuse University iSchool, and the following repository supports the Twitter search and pagination API. Collecting from the Facebook search and pagination API is under development. The link to the code can be [found here](https://github.com/bitslabsyr/stack2)

**_This documentation assumes the following:_**
* You know how to use Ubuntu 20.04.
* You know how to use ssh.
* Your server has MongoDB, Docker and Docker Compose already installed.
* You understand how to edit files using vim (“vi”) or nano.
* You have rights and know how to install Python libraries.


## Installation

Prior to installing STACK, make sure you have MongoDB, Docker and Docker Compose installed and running on your server.

* Install MongoDB on Ubuntu 20.04: https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/
* Install Docker on Ubuntu 20.04: https://docs.docker.com/engine/install/
* Install Docker Compose on Ubuntu 20.04: https://docs.docker.com/compose/install/


## Steps on how to start the collector

The STACKS documentation contains a collector tool by the name of _abcd.py_. Upon opening it, we change the search the following query parameter:
```
"query_parameters": {
            "query": "from:<Insert the Twitter User ID here>",
            "expansions": "author_id",
            "tweet.fields": ["author_id", "conversation_id", "created_at", "geo", "id",
                             "public_metrics", "promoted_metrics", "organic_metrics",
                             "in_reply_to_user_id", "referenced_tweets", "source", "text"],
            "user.fields": ["created_at", "description", "entities", "id", "location",
                            "name", "pinned_tweet_id", "url", "username"],
            "media.fields": ["media_key", "preview_image_url", "type", "url",
                             "public_metrics", "organic_metrics", "promoted_metrics", "alt_text"]
        },
```
Hit run and keep the code running until desired time. The data starts getting stored in the MongoDB database accordingly. The collector keeps pulling in all the tweet information into ```data["filename"]``` and the log information into ```log["filename"]```.

{% 
	include image_with_caption.html 
	url="/assets/projects/2023_stacks/main.jpeg" 
	description="The intuition behind the toolkit"
	width="100%" 
%}