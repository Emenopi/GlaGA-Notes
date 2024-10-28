---
tags:
  - Foundations_of_Professional_Software_Dev
---
# INTRODUCTION

I am a Graduate Apprentice Software Developer at Wood Mackenzie working within the Power Rangers Team. As part of this role, I am involved in the development process in much the same manner as other developers on the team albeit with a heavier concentration on learning and development.

# DEVELOPMENT PROCESS

Our development process follows the Agile methodology, focusing on flexibility and practicality. The life cycle is circular and organised into individual sprints, which allows the company to remain flexible enough to feasibly pivot the product quickly should business' needs require. Such flexibility contrasts with alternative methodologies such as the Waterfall model which takes a more rigid approach.

The development process is end-to-end, incorporating pre-development and post-production release stages. The sprint's tickets therefore result from thorough communication and deliberation upstream. For most developers, involvement begins with sprint planning sessions before working on tickets, pushing changes to production, and ending with retrospective meetings.

Sprint tickets are monitored via kanban board which developers to view and assign themselves tickets and facilitates communications during standups. Wood Mackenzie adopts the philosophy that all developers, regardless of experience should be able to work on any ticket thus encouraging T-Shaped development to the benefit of both the business and individuals. Developers will therefore pick up tickets based on priority and discuss during stand up regarding what they will be working on and if assistance such as pairing or knowledge sharing is required. More complex tickets may require mob programming which pools knowledge and experience from the whole team to ensure the best solution possible. As Power rangers is a mature, self-organising team in line with Agile principles, communication and working with other team members freely is encouraged. It is common, therefore, to time-box a problem and later request assistance. In cases where the team cannot fully satisfy the acceptance criteria, they will discuss with the Product Owner regarding alternatives or request assistance from another team.

Tickets are written such that they include acceptance criteria, technical analysis, and test requirements. A developer will then assign themselves the ticket and commence programming and test writing. After development, they will move the ticket to the 'Ready for Review' column where others must then review their code to approve or suggest changes.

During the review stage, each ticket is required to have at least two approvals before progressing to the QA process. This means that tickets may be passed back and forth between review and development stages until an acceptable solution is found. This process ensures that code changes which reach the QA stage are already of high quality.

Within Power Rangers there are two standup meetings per day, with the morning concentrating on work plans and pairing requrests, while the afternoon standup involves a 'board walk' with the Product Owner. The 'board walk' allows each person the opportunity to update the product owner regarding how tickets are progressing, and request later discussion with her if necessary.

# UPSTREAM & DOWNSTREAM


Creating tickets and decisions surrounding prioritisation and allocating tickets to particular sprints involves the Product Owner collaborating with other stakeholders and customers. Stakeholders then decide upon a 'PR Road Map' consisting of Epics which are broken into individual issues or user stories. This is informed by commercially driven interests, customer insight, and feedback gained by the Product Owner, UX researchers, and the customer research team. Information gained from these enables the company to define quarterly objectives to facilitate prioritisation as per the MoSCoW framework.

After setting quarterly objectives, they are further broken down into sprints which are planned based on prioritisation and consideration for how epics involving multiple teams should be handled. This leads into creation of tickets and organisation into sprints.

Sprint planning spans multiple sessions to allow time for discussion of all tickets nominated by the product owner. As the product owner must ensure the amount of work per sprint strikes a good balance between productivity and upholding the Agile principle of promoting sustainable efforts, each ticket is discussed in depth regarding acceptance criteria and technical analysis. The team then votes on the size, roughly equivalent to days required for development, thus allowing the Product Owner to determine which tickets to include. Sprint planning sessions provide the opportunity to understand tickets prior to development and ask clarifying questions. This is of particular value to junior developers and helps us to contribute productively regardless of experience. Conversely, it also provides feedback to senior colleagues regarding how to more effectively communicate the details and analysis such that it can be understood by any team member. 

After development and review, tickets undergo quality assurance to ensure they meet acceptance criteria and exploratory testing. Tickets failing QA will repeat each stage until the code change is able to successfully pass all three initial stages. Prior to reaching production, the Product Owner must approve each ticket. This is discussed during the afternoon standup and ensures all tickets reaching production are approved by her.

Releasing to production is done via Jenkins - a job runner which  automatically builds and tests changes. Using Jenkins allows the company to ensure Continuous Integration and Development despite numerous teams working on the software. Any test failures or problems result in failure to build, therefore providing an additional layer of assurance. Such failures are highlighted to the assigned developer to be rectified and may result in tickets repeating the development process again.

While many companies continue to monitor post-production changes to determine how a change is performing, this is not something that generally occurs at Wood Mackenzie. However, they do make heavy use of feature flags to determine what a particular user has access to and allow changes to be available to only certain users. This technique of A/B testing is often used to gain customer feedback, particularly regarding more significant changes, to determine if further work is required. Ultimately, the post-production stage in Wood Mackenzie is minimal as the aim is to continuously move forward in response to feedback and business interests.

# SECURITY

Within Wood Mackenzie, there is a duty for everyone to protect the security of the software and associated systems. This means that anyone who identifies a possible weakness or security concern must raise the matter to the relevant person(s) so that it can be dealt with promptly. However, this particular aspect contributes only a small part to maintaining adequate security and is in no way relied upon.

More proactive measures involve security and package scanning tools as well as web app firewalls - each with their own use cases and are thus employed appropriately. Of these, package scanning tools and web app firewalls provide more of a first-line defence in terms of security, while security scanning is run less frequently, dependant on architecture changes.

Package scanning tools ensure each package pulled in to the codebase is scanned for any potential security concerns, thus mitigating risks associated with including external packages. This process is of particular importance in such a large codebase as is used in Wood Mackenzie. Similarly, web app firewalls provide similar seacurity measures for protecting the software when using external web apps. These firewalls protect against common exploits and are preferred over more proprietary alternatives as they are better placed informed on zero-day vulnerabilities.

In addition to the above, Wood Mackenzie implements various security measures regarding developer access. All access is via HTTPS protocol and the zScaler security service to ensure a secure, encrypted connection which utilises sign-in authorisation tokens for multi-factor authentication. Admin access on company devices is also restricted to ensure rogue software cannot be installed, thus protecting each device from data or other security breaches.

# QUALITY ASSURANCE

All tickets must go through peer review and obtain at least two approvals before progressing to the quality assurance stage of the development process. This ensures changes are of the highest quality attainable to the particular team's combined knowledge and experience. Therefore it's not sufficient to simply implement a change which meets acceptance criteria, but rather to implement a solution which is clean and efficient.

After satisfying review requirements, changes must then pass the QA stage. Within Power Rangers there are two dedicated QA testers who will pick up tickets "ready for QA" and carry out relevant testing. The code changes are run locally using a feature branch and tested against the acceptance criteria and additional exploratory testing. Often QA team members will pair with the developer for writing playwright tests so may therefore be involved in the development process beyond specifically QA tasks. QA testers are therefore important in ensuring ticket specification is non-ambiguous and that developers also consider non-functional requirements.

In terms of test requirements, Wood Mackenzie does not enforce any strict test coverage criteria as it is understood that KPIs can easily be misleading and strong reliance on strict KPIs such as test coverage easily leads to bloating and unsatisfactory tests. To circumvent this, Wood Mackenzie prefers to ensure changes are well reviewed and tested through QA, with details of necessary tests included within the ticket itself.

While developers commonly run unit tests as a matter of good practice, a more comprehensive run is automated using Jenkins during the build and integration process. This allows testing to incorporate cross-repository integration prior to merging code changes, thus aiding in the continuous integration/continuous development process.

Additionally, Wood Mackenzie utilises multiple environments such as development, user acceptance testing, and integration testing to ensure changes can be tested outside of the production environment. Any code changes which reach the production environment have therefore been thoroughly tested, thus mitigating any risk to the existing working software.


# CONCLUSION

The development process employed at Wood Mackenzie, specifically within Power Rangers has great emphasis on producing quality code changes while protecting the production environment. This is facilitated by encouraging communication and collaboration between the developers, QA and product owner; ensuring thorough checks and testing throughout the development and integration process; and utilising sufficient security measures.
