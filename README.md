# Software development is an adolescent engineering discapline

15 November 2018

Software development is a new field. As a software developer I love reading design patterns and architecture books. I love the way they look at the problems I face day to day objectively. Grouping them into categories of problems. Identifying alternative solutions with pros and cons. As our profession develops into a mature engineering discapline, training can be standardised producing engineers with a common language and set of principles. We can spend less time fussing with semantics and more time on solving problems.

# My problem is, I think I am right

9 November 2018

I remember a gifted Enterprise Architect saying to me once, "my problem is, I think I am right". In his case I think the problem was that other people did not realise that he was right.

I think there is a principle about pragmatism here. Businesses do not seek ideal solutions. They "satisfice" or follow the 80/20 rule. To find a perfect solution simply costs too much money. While your architects are debating the pros and cons of NodeJS vs .Net Core your competition has knocked together a Java Servlets product that does what the customer requires. Don't get me wrong, a bad architecture has consequences. My point is, get yourself a good architect and then give him or her the authority to make design decisions. If you seek consensus, you will move very slowly and end up with a patchwork of compromises.

# Getting the Pyramid Right

3 November 2018

We were chatting a few months back about resource planning for a startup. I was arguing for hiring the most skilled people we could find. The more skills the better right? My colleague disagreed. He argued for more juniour resources. He reasoned that senior resources will all want to be involved in the design and decision making process. They don't want to be told what to do. This results in design debates around each design decision. A more junior resource on the other hand is eager to absorb the skills of the designer and appreciates being told what to do. 

This reminded me of something we used to talk about on consulting projects: getting the resource pyramid right. Hiring too much skill and experience in the team can make the pyramid top heavy. Besides pushing up cost it also affects the ability to promote people within the organisation. If everyone is near the top there is not much space for juniors to move up.

# The Importance of a Governance Mandate

2 November 2018

IT governance is important, especially in the area of security, architecture and design. Governance can also be unwelcome. Staff may not see the need for governance and may see it as an unwelcome intrustion into their projects. While governance teams should work hard to explain the reasons behind the requirements they put on project teams, there is a need for a clear executive mandate that gives governance the necessary level of authority to carry out their function.

# Obsession with NFRs

30 October 2018

Developers can fall in the trap of treating Non-Functional Requirements (eg program efficiency, elegant code, excellent documentation, smooth build pipeline, zero errors) as more important than Functional  Reuqirements. NFRs and FRs need to be prioritised against Business Outcomes.

# Making work visible

30 October 2018

Make it as easy as possible for team members to make their work visible. If you can hook into their existing workflow (eg git commits) this is ideal. If they need to create tickets give them a tool that makes this as easy as possible. They will have to use it continually. If there is friction in the process it will wear them down.

# UI Scaffolding Saves Time

29 October 2018

Back office user interfaces are an important way of transferring system ownership from developers to business staff. The problem is, custom UIs take a lot of time to build and to maintain. A UI scaffolding tool like Gails makes this task much easier.

# Interview Questions

29 October 2018

* Have you ever taken over the development of a large complex system?
* Have you ever had to get up to speed on a large existing code base? How long did it take you before you could start making changes to the system?
* Have you ever had to work with code other people had written?
* Describe several software development patters. When would you use them?

# Security Hardening Our Network

23 October 2018

1. Restrict internal firewall rules to least access
1. Consolidate log files
1. Keep everything very neat and tidy

# Separating container from config is a good idea

19 October 2018

When you have to make infrastrcuture changes that change micro service config you will be thankful that you kept your micro service and its deployment config separate. In the past few weeks I have had to move our database twice and our message broker once. In all of these cases the micro services have not changed, only the infrastructure they run on. In this case what we want is to redeploy our micro services with new configuration (eg DB connection string) but keep the micro service versions unchanged. If a change in your config causes a new version of your micro service to be built you cannot do this.

# Two things you should get right from the start

30 April 2019

1. The domain model. This is the conceptual skeleton of your software. It links your software to the world in which it is expected to deliver value. Your team will use this skeleton to guide their work. Designers will design off this skeleton. Developers will code off the skeleton. Processes will grow around the skeleton. If a few months down the line you realise that your lovely quadruped skeleton should actually be a biped this will have a massive ripple effect.
1. Your documentation repository. This is a reflection of your business operating model. Decide what documentation your business needs based on your operating model and create a folder structure that is unlikely to change. Documentation is best laid down fresh. For example, an Incident Report is best written up immediately after the incident has been resolved. Minutes of a meeting are best written up during the meeting. The implication of this is that people will only do the documentation that is implied by your documentation repositories folder structure. If you make fundamental changes to the folder structure it will be very difficult to retroactively produce the new documentation.

# The tradgedy of the commons

30 April 2019

> The tragedy of the commons is a situation in a shared-resource system where individual users acting independently according to their own self-interest behave contrary to the common good of all users by depleting or spoiling that resource through their collective action. [Wikipedia](https://en.wikipedia.org/wiki/Tragedy_of_the_commons)

Hence, private ownership. The same applies in a business. If I own the document/component/team/department and it is in a mess that says something about me. If, as a leader, you fail to delegate ownership. Everything is a reflection of you.

# Data lifecycle hooks

15 May 2019

Very useful to have a beforeCreate, afterCreate, beforeUpdate, afterUpdate, beforeDelete, afterDelete hook for your data. I am thinking specifically of data you would store in a database. Ideally the hooks should give you the data value before and after the change and the before hooks should allow you to cancel the change.

# Mind your own protocol

29 May 2019

I think REST web services have encouraged me to make a mistake. REST web services use the HTTP protocol verbs GET, POST, PUT and DELETE to represent read, create, update and delete in your application. This creates a coupling between your application and the underlying protocol. This can be fine for simple CRUD operations but very often I find myself writing a read operation, for example a search operation, where I would like to include complex parameters in a JSON request body. In this case I break the read/GET convention and use a POST.

Here is another example of this mistake. I am logging to a central log server using syslog. Syslog output includes the log time, program name and log message. So I decided to use syslog log time and program name in my application logs. Only later did I realise that the syslog time was not millisecond precision and sometimes I don't want the program name to be the executable name used by syslog. Also, what if want to swap out syslog for a different logger. The coupling to the syslog fields makes this more difficult.

The moral of the story, don't create couplings into the underlying protocol layers on which your application runs.

# Detailed plans make context switching easier to deal with

2 July 2019

I am restarting a piece of half finished work today. The work had to be parked because a piece of billable work came in and we needed the money. So my first task this morning is "Where was I when I stopped this work?". If the work has been parked for a longer period the question might be "What was the reason for this work in the first place?". This is where having a detailed plan really helps. At the time the detailed plan might have seemed like overkill, but it makes picking up the pieces days, weeks or months later much easier.  
