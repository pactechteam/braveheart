# braveheart

All social media involves a variation of the following elements:

* friends
* a newsfeed made up of content posted by friends
* and an algorithm to to sort that content for the user. 

While there are many new alternative social media sites popping up and promoted by various celebrities, they all still rely on a central server model. This is necessary to control ad space and monetize the project.

The Braveheart project is not about money in any way, it is about freedom. That is why the working title is named in honor of William Wallace, the great freedom fighter of Scotland. Power to the people!

There have been distributed social media apps before, most notably [https://diasporafoundation.org/](Diaspora). But Diaspora servers are not easy to setup and the system attempts, at least to my knowledge, to force people to connect to a central web. Braveheart is all about freedom, if you want to have an isolated social media network from other users, that will be totally acceptable in Braveheart, online, off line, whatever. 
Principles:
Social Media should be a protocol not an app
Be a universe of plugins
Reliability is a higher priority than privacy, though privacy is still very good. 

## backend facing
Each server will function like a Diaspora pod. That is it can host multiple users. Each user can have multiple friends. These friends have addresses. Those addresses correspond to contact plugins for using different methods to communicate. We will focus on the TOR method first. Hopefully this will allow for easy connection between servers without the need to register anything through a centralized DNS. Other methods of friend to friend communication we would like to see.
*	When friends are on the same server
*	When the friend is on another server that can be contacted through I2P
*	When the friend is on another server that can be contacted through Lokinet
*	When the friend is on another server that can be contacted through Clearnet
*	When the friend is a sqlitefile (or something) of updates that have been delivered via sneakernet 
*	When the friend is on another server that can be contacted via a wifi mesh net
*	…

The goal is to have these be plugins that can be built out by the community. If one plugin fails, the next one can be used. This will allow for a separation of concerns between coders who want to build deep, complex internet protocols and those who want to build user facing, beautiful, interfaces for social media. 

## user facing
The sever box will then expose another port for the user to connect to via a local wifi connection or Clearnet. They may have to accept a self signed certificate, but we can try to minimize this. The server will have a user interface (imagine a 2.5 inch screen on a Raspberry Pie) with a QR code that can be scanned by a phone on the same network. The result will be a link to the user facing web interface. Ideally this web interface will be an SPA (Single Page Application) that can be downloaded by the user as an app. I believe Gab uses a similar technique to get around the App Store censorship problem. 
When users add friends, they do so by opening the now offline app and displaying/scanning a QR code that includes the TOR address for the sever. Next time they are home, the app can sync this friend request using the server and they are off to the races. If they are connected to their home sever via Clearnet, this can go even faster. 
### user content
User content will be cached by the server from other servers throughout the day and night. When one browses the user facing Braveheart app, they are really browsing this cache. We will get more details as we build this out.
When one (the interactors) interacts with a friend’s content, the interaction is logged by both users. The friend who initially created the content, (the OP or Original Poster) can then broadcast this as an update to the content to other friends’ newsfeed caches. This interaction, be it a like, a dislike, or a comment, will have the address of the interactor and a UUID attached to it. Different servers, upon seeing this update, will then be able to verify (perhaps randomly to improve performance) that the interaction is indeed a genuine interaction. If the interaction claims to be from an interactor within the social sphere of the verifying user, the validity of the interactor can be achieved. If an OP is found to be cheating by creating false interactions, they can be punished in the newsfeed rankings by the algorithm. The algorithm may notify the user about this. Also, these ranking algorithms should be plugins. 

## Roadmap
1.	Proof of concept. If devs can get any kind of TOR hidden service going, let’s try to build an absolute barebones version of this thing. Let’s use Python as it seems to have good TOR support and is lingua franca for most of us. 
2.	Add dev build pipeline. We want to have multiple test instances running so we can test the app as we go. Somebody is going to need to figure out a tool like Jenkins and show the rest of us how to get it going on our servers. 
3.	Build out the user interface a little bit
4.	Dockerize it for easy deployment
5.	Come up with a good issue tracking system
6.	Upgrades and add users
7.	Dank memes

If somebody wants to just start writing some code, push it to this repository and let’s get this thing built! We’ll figure out the rest as we go. 
