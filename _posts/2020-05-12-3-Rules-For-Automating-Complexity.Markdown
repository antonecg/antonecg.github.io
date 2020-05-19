---
layout: post
title:  "3 Rules for Automating Complexity"
date:   2020-05-12 21:03:36 +0530
categories: Theory Work Complexity
---
At work, we are paid to make decisions and accomplish complex tasks. However, there is a limit to the complexity that one woman or man can handle. Each of the decisions takes mental energy and after a certain point your choices become worse (Tierney, 2011).

I work at LBMC Data insights. While the final product I develop is usually a dashboard or an app, the hard part of the job is automating business complexity. By programming in rules and business logic, we only have to recall them once, instead of remembering them every day. I use the Microsoft BI Stack, normally a combination of SQL, Analysis Services, and PowerBI.

Having worked with dozens of clients, I have learned a few rules to live by. I learned through both mentorship, but also trial and error. I have to fix my mistakes and fixing my mistakes means I end up working late or over weekends.

1. You can automate complexity, but you can't reduce it. 

In their marketing materials, many companies (including Microsoft) heavily imply that by using their latest and most expensive tools, you will be able to turn messy databases and a complex tangle of business logic into insights or dashboards seamlessly. The truth is, that the rules always have to be programmed and that is the hard part of my job. Building dashboards is easy and anyone can learn how in 6 months. What takes skill is working with clients to capture all of their logic. Usually, when clients see Version 1, they realize that they had been using a lot of rules and logic that they hadn't thought to document. What takes more skill is finding the most efficient way to store and recreate the logic.

2. Know your tools.

When I started, I relied heavily on PowerBI for dealing with complexity. I would pull in a simple sql model and basic DAX measures, bringing in most of the logic as filters in PowerBI. This gets to be a slow mess very quickly and the filters start interacting with each other in unanticipated ways.

I then moved to doing more work in Analysis Services, relying on Power Query and Dax measures for complex transformations. Unfortunately, this can be slow on the end user and is very difficult to debug. Very few people have extensive experience with Power Query and Dax and I would often find myself swamped by problems which only I knew how to fix.

I have now moved to an SQL-first methodology. Ancient, un-sexy, SQL. While everyone talks about big data, I think that most companies' data actually doesn't require big data solutions. If you are OK with a 30 minute lag on data (from point of collection to dashboard), and you aren't taking in more than a billion data points, a well thought out relational SQL model can solve your problems effectively. Furthermore, there are tens of thousands of experienced SQL engineers in the world. At my office, almost everyone is experienced with SQL. If I get swamped with projects, I am able to offload SQL-heavy work to almost anyone.

3. Put Your Logic in 1 Place.

The projects that have kept me working late and over the weekends got messy because I had logic in many different places. I would have PowerBI filters, Dax measures, and SQL views affecting each other in complex ways. 

By putting the logic in one place, you don't have to think about the interactions between systems and it is far easier to debug. Right now, my favourite place to build in logic is in a view that is called by a Stored Procedure and loaded into a Table. It makes changes easy to make and test.


My examples were Microsoft-heavy, because those are the tools I use every day, but the same 3 rules would hold true if you were using Amazon, Tableau, Books, or even Stone Tablets.

As a species, we are able to advance because we can offload and record complexity, and then not have to worry about it. With our extra headspace, we go on to take more decisions and then onward to ever increasing complexity. By handling this complexity we are able to create functioning states, and put people in space.



Sahakian, B. J.; Labuzetta, J. N. (2013). Bad moves: how decision making goes
wrong, and the ethics of smart drugs. London: Oxford University Press.

(Tierney, 2011) https://www.nytimes.com/2011/08/21/magazine/do-you-suffer-from-decision-fatigue.html