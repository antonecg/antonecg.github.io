---
layout: post
title:  "Microsoft Analytics Projects That Won't Blow Up"
date:   2020-05-12 21:03:36 +0530
categories: Anlalytics Work PowerBI
---
Analytics Projects can blow up. Broken PowerBI reports. Broken pipelines. Broken databases. These can leave executives and employees skeptical of what proper analytics can bring to a company. 

We in the analytics world need to accept that complex analytics projects are software development projects. We need to be using source control, pull requests, and DevOps -even if we work alone. Furthermore, we need to be organized, using scrum or other tools to manage tasks.

**Source Control and Pull Requests**

Source Control and Pull Requests keep you from deploying bad code into production and allow you to track your changes. I love Azure DevOps to set up my source control and use it for every project that I'm on. If you aren't familiar with Source Control and Pull Requests, it is something that you could learn in 3 hours and will change how you approach project. If you want to learn, there are plenty of great tutorials : https://try.github.io/ 

Unfortunately, source control does not work with PowerBI. On my projects, I build measures and do transformations in Analysis Services. This allows me to throw up Power BI dashboards  with a robust data model. It also allows me to see the changes I have made before deploying to production. If there is something that I had not intended (like accidentally changing a measure) I can see the error and role back to an earlier version. I can also work on different branches. This allows me to work on multiple initiatives push different things into production at different times.

Pull Requests are an important part of using source control. The concept is simple - If you make changes, instead of immediately going live, you set a request in DevOps that goes to someone else on your team. That person can see your changes and approve or reject them. More than once, I've pushed up bad code that was caught by one of my teammates in the Pull Request process. If you are working alone, the Pull Request Process forces you to take another look at your code.

**Get Organized or Blow Up**

If your analytics project succeeds, people will come asking for more. One of the main reasons that I've seen projects run into trouble is that too many requests are coming in to deal with.

You need to have a good way to prioritize requests and to set expectations. Sometimes, you have to have difficult conversations, like having to tell users that you won't be able to work on their report for another two months because you are working on higher priority tasks.


At LBMC Data Insights, we use Scrum, but I have worked on projects that used an excel sheet to organize priorities. I like scrum because you are forced to look at all your tasks, and pick what you will do in the next sprint. If you'd like to learn more, here is a handy guide to Agile Scrum: https://www.atlassian.com/agile/scrum .

 Whatever yout method, you should be clear with your teammates and clients about how long things will take. People will ask you do do 12 things at once and the only way you'll get them done is by finishing one at a time. 


**Conclusion**

There is a lot of flashy marketing around analytics. Companies promise easy to use tools that do all the work for you. In reality, working on analytics projects is probably harder than it was 10 years ago, but the rewards are greater.  We can now bring together hundreds of streams of data, live.  We can create powerfull reports that use machine learning. But to build reports that dont break, we need to work like software developers. And to not get swamped by 30 tasks at once, we need to become effective project managers.