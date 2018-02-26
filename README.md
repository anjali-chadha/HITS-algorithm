# HITS-algorithm
Implementation of Hyperlink-Induced Topic Search algorithms.
Read more about this alogorithm [here](https://nlp.stanford.edu/IR-book/html/htmledition/hubs-and-authorities-1.html)

## A re-Tweet Graph

This project adapts the classic HITS approach to allow us to find not the most authoritative web pages, but rather to find significant Twitter users. So, instead of viewing the world as web pages with hyperlinks (where pages = nodes, hyperlinks = edges), we're going to construct a graph of Twitter users and their retweets of other Twitter users (so user = node, retweet of another user = edge). Over this Twitter-user graph, we can apply the HITS approach to order the users by their hub-ness and their authority-ness.

Here is a toy example. Suppose you are given the following four retweets:

* **userID**: diane, **text**: "RT ", **sourceID**: bob
* **userID**: charlie, **text**: "RT Welcome", **sourceID**: alice
* **userID**: bob, **text**: "RT Hi ", **sourceID**: diane
* **userID**: alice, **text**: "RT Howdy!", **sourceID**: parisa

There are four short tweets retweeted by four users. The retweet between users form a directed graph with five nodes and four edges. E.g., the "diane" node has a directed edge to the "bob" node.

This project builds a graph by parsing the tweets in the file provided called *HITS.json*.

**Notes:**. 
* The edges are weighted and directed. If Bob retweets Alice's tweets 10 times, there is an edge from Bob to Alice with weight 10, but there is not an edge from Alice to Bob.
* If a user retweets herself, ignore it.
* Correctly parsing screen_name in a tweet is error-prone. Use the id of the user (this is the user who is re-tweeting) and the id of the user in the retweeted_status field (this is the user who is being re-tweeted; that is, this user created the original tweet).

## HITS Implementation
This program will return the top 10 users with highest hub and authority scores. The **output** is like:

Hub Scores

* user1 - score1
* user2 - score2
* ...
* user10 - score10

Authority Scores

* user1 - score1
* user2 - score2
* ...
* user10 - score10

