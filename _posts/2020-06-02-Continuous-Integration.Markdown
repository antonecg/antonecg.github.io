If you have been working in analytics, you've seen projects blow up. A small change, pushed by you, a partner, or a client can have huge unintended consequences. Users can be left without critical data and you will be stressed trying to figure out what went wrong.

If software development projects worked like that, our iPhones wouldn't work and LinkedIn would probably be down right now. In this article, I will show you a key practice that software developers use to keep project from going wrong: continuous integration. Then I will show you how to set up continuous integration for yourself on an SQL project using Azure DevOps.

What is Continuous Integration?

Continuous integration is the process in which team's code is automatically built, tested, and deployed. Continuous integration finds errors early and helps prevent bad code from ever reaching production.

The first step is for the team to be using source control. If you aren't familiar on how to use source control for analytics projects, read my earlier article. After developers check in their code, a tool automatically builds the whole solution and tests if there are any errors. If there are any errors, the developer is alerted to the errors. Otherwise, a package is written by the continuous integration tool that allows you to deploy your code at any time. You can schedule your deploys to be nightly, weekly, hourly, or even all the time. 









Add alt text
No alt text provided for this image
How Can I Use Continuous Integration for an Analytics Project?

At the heart of most analytics projects that I work on lies a SQL Data Warehouse. The traditional way of working on SQL projects is to work directly on the database and make lots of backups. Tables and procedures can have hidden dependencies and it is easy to break things. 

When I work on SQL projects, I develop the code using SQL Server Data Tools, which is a powerful Microsoft tool to build Sql databases. It uses Visual Studio and I highly recommend looking at the documentation.

https://docs.microsoft.com/en-us/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15

So what does it mean to build a SQL database project? With TSQL, the key to building a database project is the DACPAC File. DACPAC stands for  Data Tier AppliCation Package and contains a binary representation of all the files needed to generate and deploy your database. So with continuous integration, we are taking the database objects and building a DACPAC. You can do this easily with Azure DevOps Pipelines and here is a step by step guide by John Miner at MSSqlTips.com : https://www.mssqltips.com/sqlservertip/5985/continuous-database-deployments-with-azure-devops/

In the process of building the DACPAC, SQL will run all sorts of tests. For example it will check to make sure that everything is pointing to something that exists. If there are errors anywhere that stop code from being able to run, the DACPAC will not build successfully. I have found this step very useful. For example, earlier this week, my partner and I were working on tables that pointed to each other. I had renamed a table and this would have caused issues, had not the build process caught them. I set up automated builds for whenever a branch is being brought into master through a pull request.

After your code is built, it is ready to deploy. You can have it automatically deploy every successful build or you can schedule your deploys. The recipe that you need (the DACPAC) has already been built (in the previous step) and you are ready to roll.

Azure Devops has a powerful tool to set up deployments. The details are outside the scope of this post, but the article by John Miner has an in depth walkthrough. You can also take a look at the documentation below: https://www.mssqltips.com/sqlservertip/5985/continuous-database-deployments-with-azure-devops/

Having Continuous Integration is a given for any major software development project is a given and I think that it should be standard for any analytics project. I would be happy to help your team get set up if you'd like any help.

