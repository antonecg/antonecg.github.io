With all the flashy marketing around analytics, companies convince you that their latest product can do the work itself. The implication is that you can create powerful analytics without having to become a software developer. I disagree. As analytics projects grow complex, Business Intelligence(BI) consultants need to adopt practices from software development. An analytics project incorporating SQL, Analysis Services, and PowerBI, has more in common with a project at Facebook or Google than with the old Excel/Access way of doing BI.



In this article, I will go through one of the most important concepts that will take you from old-school BI to the new paradigm: Source Control. I will first explain the paradigm shift in BI before going through the basics of source control. I will then walk through how I use the tools in a project.



What separates the old BI mentality from the new software development influenced one? The old school BI consultant would rely on custom scripts that only they have access too. There would be logic baked into reports and lots of coexisting versions. Bad code would get deployed into production and it would become impossible to fix because there weren't any backups. When an old-school BI left a company, large parts of their systems would have to be rewritten because necessary knowledge would leave with them.



Compare this to software development. For a software developer, a report is not just a report. A database is not just a database. The software developer sees each of these tools as pieces of a larger codebase. There is one organized codebase for an analytics project that uses Analysis Services, SQL, PowerBI, and Data Factory. Each team member has an identical copy of the project and can propose changes. A project manager can decide which changes should be adopted by the project. Software developers have traditionally handled this through version control mechanisms like git. 



Git is an open-source tool created by Linus Torvalds (who also created Linux). Git powers development platforms such as Github, Bitbucket, and Azure DevOps. 



If you want to learn the basics of source control, there are plenty of great tutorials: https://try.github.io/ 



I use Azure DevOps to set up my source control for every project that I'm on. Setting up a codebase is easy: https://docs.microsoft.com/en-us/azure/devops/user-guide/services?view=azure-devops . Azure Devops also allows you to plan and track work, set up automated testing, and configure continuous integration.



For illustration, I'll walk through how I would handle a small analytics project. This project will contain databases, analysis services, and PowerBI reports. 



I start by setting up a code repository in DevOps and connecting Visual Studio to the repository (https://docs.microsoft.com/en-us/visualstudio/get-started/tutorial-open-project-from-repo?view=vs-2019). I add all of my SQL code and analysis services code in Visual Studio as separate solutions in the same project. I will typically commit the state of the project to master and create a new branch in the repository with a brief name and description that describe how I am changing the existing codebase. This local branch can be used as a sandbox where mistakes can be made without consequences. As I check off subtasks towards my goals I commit my changes with messages of what changes I have made since the last commit. Once I am satisfied and would like to allow my team to access the code, I push my changes to our shared remote repository with DevOps. I create a pull request with a description outlining how my set of changes improve upon the existing functionality. https://docs.microsoft.com/en-us/azure/devops/repos/git/pull-requests?view=azure-devops . 



The project lead can visit the page for a pull request and see the differences between my code and the current state of the master branch to ensure that my changes are to their liking. Even when I am the project lead, I always have someone else look at the code. In the workplace accountability is key. If you do not have an appointed member who swears by the pull requests that they merge you end up with a finger pointing contest rather than a functional and cohesive team. Even if you are working alone, splitting your tasks into logical subunits (a collection of pull request process) offers you the ability to review each of your tasks as you start to assemble you tack them onto your master branch.



I recommend that you start using source control immediately. However, this is only one step towards using Azure DevOps effectively. In my next posts, I will cover work planning, testing, and continuous integration.



If you embrace your role as a BI/Software Developer, you will develop behaviors that allow you to compartmentalize complexity and reduce hassle. You will be able to sleep soundly knowing that your production code is solid and that if there are any issues, you can fix them quickly. 



I hope that you found this article useful and I will keep writing more.

