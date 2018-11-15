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

1. Restrict Security Groups to least access
1. Consolidate log files in ElasticSearch using filebeat
1. Keep everything very neat and tidy

# Separating container from config is a good idea

19 October 2018

When you have to make infrastrcuture changes that change micro service config you will be thankful that you kept your micro service and its deployment config separate. In the past few weeks I have had to move our database twice and our message broker once. In all of these cases the micro services have not changed, only the infrastructure they run on. In this case what we want is to redeploy our micro services with new configuration (eg DB connection string) but keep the micro service versions unchanged. If a change in your config causes a new version of your micro service to be built you cannot do this.

