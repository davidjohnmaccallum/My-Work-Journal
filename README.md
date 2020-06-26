# Software development is an young engineering discipline

15 November 2018

Software development is a new field. As a software developer I love reading design patterns and architecture books. I love the way they look at the problems I face day to day objectively. Grouping them into categories of problems. Identifying alternative solutions with pros and cons. As our profession develops into a mature engineering discipline, training can be standardised producing engineers with a common language and set of principles. We can spend less time fussing with semantics and more time on solving problems.

# My problem is, I think I am right

9 November 2018

I remember a gifted Enterprise Architect saying to me once, "my problem is, I think I am right". In his case I think the problem was that other people did not realise that he was right.

I think there is a principle about pragmatism here. Businesses do not seek ideal solutions. They "satisfice" or follow the 80/20 rule. To find a perfect solution simply costs too much money. While your architects are debating the pros and cons of NodeJS vs .Net Core your competition has knocked together a Java Servlets product that does what the customer requires. Don't get me wrong, a bad architecture has consequences. My point is, get yourself a good architect and then give him or her the authority to make design decisions. If you seek consensus, you will move very slowly and can end up with a patchwork of compromises.

# Getting the Pyramid Right

3 November 2018

We were chatting a few months back about resource planning for a startup. I was arguing for hiring the most skilled people we could find. The more skills the better right? My colleague disagreed. He argued for more junior resources. He reasoned that senior resources will all want to be involved in the design and decision making process. They don't want to be told what to do. This results in design debates around each design decision. A more junior resource on the other hand is eager to absorb the skills of the designer and appreciates being told what to do.

This reminded me of something we used to talk about on consulting projects: getting the resource pyramid right. Hiring too much skill and experience in the team can make the pyramid top heavy. Besides pushing up cost it also affects the ability to promote people within the organisation. If everyone is near the top there is not much space for juniors to move up.

Update 26 June 2020

In hindsight, simply being junior does not make a person more amenable to being told what to do. Nor does being senior make a person less able to collaborate and reach a good consensus. I think what we are looking for is a temperament that collaborates well. I think this includes humility and competence.

# The Importance of a Governance Mandate

2 November 2018

IT governance is important, especially in the area of security, architecture and design. Governance can also be unwelcome. Staff may not see the need for governance and may see it as an unwelcome intrusion into their projects. While governance teams should work hard to explain the reasons behind the requirements they put on project teams, there is a need for a clear executive mandate that gives governance the necessary level of authority to carry out their function.

Update 26 June 2020

I think tool making (think CLI) is an important skill for an IT governance function. Delivery teams don't want to create insecure or poor quality solutions. The problem is they are under pressure. Create great tools to make it easier for them to meet the standards you set.

# Obsession with NFRs

30 October 2018

Developers can fall in the trap of treating Non-Functional Requirements (eg program efficiency, elegant code, excellent documentation, smooth build pipeline, zero errors) as more important than Functional Requirements. NFRs and FRs need to be prioritised against Business Outcomes.

# Making work visible

30 October 2018

Make it as easy as possible for team members to make their work visible. If you can hook into their existing workflow (eg git commits) this is ideal. If they need to create tickets give them a tool that makes this as easy as possible. They will have to use it continually. If there is friction in the process it will wear them down.

# UI Scaffolding Saves Time

29 October 2018

Back office user interfaces are an important way of transferring system ownership from developers to business staff. The problem is, custom UIs take a lot of time to build and to maintain. A UI scaffolding tool like Grails makes this task much easier.

# Interview Questions

29 October 2018

- Have you ever taken over the development of a large complex system?
- Have you ever had to get up to speed on a large existing code base? How long did it take you before you could start making changes to the system?
- Have you ever had to work with code other people had written?
- Describe several software development patters. When would you use them?

# Security Hardening Our Network

23 October 2018

1. Restrict internal firewall rules to least access
1. Consolidate log files
1. Keep everything very neat and tidy

# Separating container from config is a good idea

19 October 2018

When you have to make infrastructure changes that change micro service config you will be thankful that you kept your micro service and its deployment config separate. In the past few weeks I have had to move our database twice and our message broker once. In all of these cases the micro services have not changed, only the infrastructure they run on. In this case what we want is to redeploy our micro services with new configuration (eg DB connection string) but keep the micro service versions unchanged. If a change in your config causes a new version of your micro service to be built you cannot do this.

# Two things you should get right from the start

30 April 2019

1. The domain model. This is the conceptual skeleton of your software. Your team will use this skeleton to guide their work. Designers will design off this skeleton. Developers will code off the skeleton. Processes will grow around the skeleton. If a few months down the line you realise the skeleton is way off, then you have trouble.
1. Your documentation repository. This is a reflection of your business operating model. Decide what documentation your business needs based on your operating model and create a folder structure that is unlikely to change. Documentation is best laid down fresh. For example, an Incident Report is best written up immediately after the incident has been resolved. Minutes of a meeting are best written up during the meeting. The implication of this is that people will only do the documentation that is implied by your documentation repositories folder structure. If you make fundamental changes to the folder structure it will be very difficult to retroactively produce the new documentation.

# The tragedy of the commons

30 April 2019

> The tragedy of the commons is a situation in a shared-resource system where individual users acting independently according to their own self-interest behave contrary to the common good of all users by depleting or spoiling that resource through their collective action. [Wikipedia](https://en.wikipedia.org/wiki/Tragedy_of_the_commons)

Hence, private ownership. The same applies in a business. If I own the document/component/team/department and it is in a mess that says something about me. If, as a leader, you fail to delegate ownership. Everything is a reflection of you.

# Data lifecycle hooks

15 May 2019

Very useful to have a beforeCreate, afterCreate, beforeUpdate, afterUpdate, beforeDelete, afterDelete hook for your data. I am thinking specifically of data you would store in a database. Ideally the hooks should give you the data value before and after the change and the before hooks should allow you to cancel the change.

Update 26 June 2020

My concern about this is how these hooks might be abused. If these hooks are used to change the data, this can lead to confusion. I prefer publishing events like customer-created, customer-updated, customer-deleted with the assumption that microservices cannot access one another's data directly.

# Mind your own protocol

29 May 2019

I think REST web services have encouraged me to make a mistake. REST web services use the HTTP protocol verbs GET, POST, PUT and DELETE to represent read, create, update and delete in your application. This creates a coupling between your application and the underlying protocol. This can be fine for simple CRUD operations but very often I find myself creating a read operation, for example a search operation, where I would like to include complex parameters in a JSON request body. In this case I break the read/GET convention and use a POST.

Here is another example of this mistake. I am logging to a central log server using syslog. Syslog output includes the log time, program name and log message. So I decided to use syslog log time and program name in my application logs. Only later did I realise that the syslog time was not millisecond precision and sometimes I don't want the program name to be the executable name used by syslog. Also, what if want to swap out syslog for a different logger. The coupling to the syslog fields makes this more difficult.

The moral of the story, create loose couplings into the underlying protocol layers on which your application runs.

# Detailed plans make context switching easier to deal with

2 July 2019

I am restarting a piece of half finished work today. The work had to be parked because a piece of billable work came in and we needed the money. So my first task this morning is "Where was I when I stopped this work?". If the work has been parked for a longer period the question might be "What was the reason for this work in the first place?". This is where having a detailed plan really helps. At the time the detailed plan might have seemed like overkill, but it makes picking up the pieces days, weeks or months later much easier.

# Dev vs Ops

23 July 2019

> So I find this law at work: Although I want to do good, evil is right there with me. (Romans 7:21)

There are fascinating tensions between dev and ops.

Dev wants to build cool new features. They want high velocity of change. But ops want a secure and stable product. "A high velocity of change? That's unwieldy!"

Once a feature is developed dev wants it to be immutable. "It's working, don't touch it." But ops wants to do across the board security patching.

I love the idea of DevOps. Let ops empower dev with the tools to build secure and stable products quickly.

# Division of labour

30 July 2019

> Division of labour: the assignment of different parts of a manufacturing process or task to different people in order to improve efficiency.

I had just joined a new team dev team. There were four of us devs. Before I joined each developer worked on a separate application. Now they tried to have two developers working on the same app. A mobile app written in Ionic. This experiment was not successful. I would like to examine why.

The first frustration was trying to get the Ionic app to build on my laptop. `npm i`, oh my. The next thing I noticed is that our coding styles were very different. My colleague valued implementation simplicity whereas I valued interface simplicity ([The Rise of ``Worse is Better''](https://www.jwz.org/doc/worse-is-better.html)). I like my software to have a domain model and a layer of services. He preferred his software to have a simple, flat structure. He is an ENTP. His style of collaboration is immediate, passionate and flexible. I am an INTJ. I like to consider things in my own time and settle on the best way forward. The project ran way over schedule and the pressure mounted. Our relationship suffered. He felt that I was slowing him down. And he was right.

Don't get me wrong. I really value team work and diversity within teams. Some of my best friendships have come through working with people in teams. Especially in the trenches on a tough project. But I definitely prefer teams with a clear division of labour. I think this is why we value loose coupling and separation of concerns in software design. Good fences make good neighbors. Dividing responsibilities in such a way that people can get on with their work and make the hundreds of small decisions required independently rather than having a discussion just makes work flow much better. Defining touch points clearly means team members know which decisions will affect other members of the team and therefore require a discussion.
