---
layout:     post
title:      "Why do you need to know about GraphQL"
subtitle:   "because it does make sense"
date:       2017-08-24 12:00:00
author:     "HK"
header-img: ""
---

<p>There are several tutorials already available on this topic by several great people. My effort in writing this post is to provide some information on the fact that there are reasons as to why one has to look in to GraphQL.</p>

<p>We will not be discussing GraphQL in very much details, but rather want to understand the need of it at the first place. My effort is to ignite some curiosity in you for learning more about GraphQL. </p>

<p>So let us start our discussion. </p>

<p> There are several new and exciting front end technologies, focus is getting shifted to mobile first approach. Front end of the legacy application are getting rewritten. Businesses are trying to make the new features available to their channels as soon as it could. We are hearing much about DevOps, to reduce time to market. In short, we are talking about swift development and release. </p>

<p> Let’s see how a typical mobile application seems like, in terms of the components-  </p>

<a href="#">
    <img src="{{ site.baseurl }}/img/graphql-1.jpg" alt="fig-1">
</a>

<p>This is the traditional flow. Client makes a request to the server. Server mostly are having rest endpoints exposed. Server call the internal services, return the desired response to the client. </p>
<p>What is the UI is changing at the client side. May be we want to show more fields on the screen, or we redesigned the UI so that we are dividing the existing screen into multiple steps or removed some of the information from the UI. In all such cases the requirement of the information from the client side is changing. And server need to change accordingly. </p>
<p>It is clear that if the requirement at the client side is changing than sever should also change accordingly. And in the case of GraphQL also, it will need a change. So what we essentially talking here is that what is the – </p>

* Amount of changes required at the server side
* Impact of the changes at the server side
* Cost of the change at the server side
* Time taken for the change at the server side


<p>
It seems that GraphQL will be better than REST in the above scenario. So this is the first reason why we should be looking into GraphQL.  It makes it easy and faster to change the response with the change in the need from the Client side.
</p>
<p>Now let us consider another scenario. You have an application in which you have a screen which consists a lot of details. For example consider an employ management system, in which you have to show Employ’s personal data, Employ’s leave details, Compensation details and many other information. There are still couple of choices in this scenario: </p>

* Client make calls to multiple services (may be asynchronously)
* Server make the customized services available to the client


<p>Let us discuss both the options in some details.
When the client has to make several calls to the server, then it is not definitely efficient. It will increase the network traffic and data transition between client and server. This scenario may also come under “Over fetching”. Over fetching simply means that you are getting/fetching extra amount data which is essentially not required by you. </p>
<p> It seems that GraphQL can help us in this scenario as well. Where we get the data as per the client’s need and call only one service, means get all the data in one response.</p>

<p>Now let's talk about the other solution - Server make the customized services available to the client. While this looks to be a good fit in this case but consider that you have multiple clients and they have different needs. So you will be making customized API’s available for all such Clients and if there is any change in the requirement you will need to change the customized API. Differentiation here maybe that how easily and efficiently you can change the API's based on the client need. So I would not say that customized API is a bad option and GraphQL will change or improve it completely, but it seems that GraphQL will be much more efficient in this case as well. </p>

<p>Let's consider another scenario where you have a screen and you are displaying information about an employee. Suppose you want to display employ name, address and compensation. You have an API available which returns name and address but not compensation. So for getting only the compensation for an employee you will have to make a call to another API. Now extending this scenario, suppose you are displaying a list of employees so for each employee you'll have to make that extra call to get the compensation value. This scenario where you will have to make an extra call to an API just to get a small piece of information is also known as “under fetching”. </p>

<p>Probably you may already have understood that GraphQL can help us in this situation as well.</p>

<p>So let's summarize what we discussed so far-</p>

*  GraphQL can help with the changing requirements at the client side. By this we mean that we can easily respond to the changes and it will reduce the time to market.

*  GraphQL can handle the problems of over fetching and essentially minimize the data which should be transferred from the server to the client.

*  GraphQL you can handle the problem of under fetching.

<p> So I think we have some reasons as to why we should be looking for GraphQL. </p>

<p> I hope that what we discussed in this post make some sense to you and may be helpful to you in start learning GraphQL. </p>
