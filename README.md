# The Importance of a Governance Mandate

2 November 2018

IT governance is important, especially in the area of security, architecture and design. Governance can also be unwelcome. Staff may not see the need for governance and may see it as an unwelcome intrustion into their projects. While governance teams should work hard to explain the reasons the requirements they put on project teams there is a need for a clear executive mandate that gives governance the necessary level of authority to carry out their function.

# Obsession with NFRs

30 October 2018

Developers can fall in the trap of treating NFRs (eg program efficiency, elegant code, excellent documentation, smooth build pipeline, zero errors) as more important than FRs. NFRs and FRs need to be prioritised against Business Outcomes.

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


# Security Hardening Our Network

23 October 2018

1. Restrict Security Groups to least access
1. Consolidate log files in ElasticSearch using filebeat
1. Keep everything very neat and tidy

# Separating container from config is a good idea

19 October 2018

When you have to make infrastrcuture changes that change micro service config you will be thankful that you kept your micro service and its deployment config separate. In the past few weeks I have had to move our database twice and our message broker once. In all of these cases the micro services have not changed, only the infrastructure they run on. In this case what we want is to redeploy our micro services with new configuration (eg DB connection string) but keep the micro service versions unchanged. If a change in your config causes a new version of your micro service to be built you cannot do this.

