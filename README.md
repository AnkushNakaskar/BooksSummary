# Software Architecture: The Hard Parts : BooksSummary
 ##### Chapter 2 :
   - Trade-off analysis :
      - analyzing what parts are coupled to one another and what impact that coupling has on change 
   - Coupling : “architecture quantum definition goes further by identifying types of coupling—that’s where the static and dynamic stuff comes in”
     - Static : 
       - dependencies include operating system, frameworks and/or libraries delivered via transitive dependency management
       - “ describes how services are wired together”
       - “service must contain dependent components such as a database, representing static coupling”
       - “We were performing a reliability analysis to determine: 
         - if I change this thing, what might break, where thing could be anything in our architecture or operations. 
         - They’re trying to do risk mitigation—if we change a service, they want to know what must be tested.”
         - Like if RMQ is removed, what are the parts which needs to be check or tested
     - Dynamic : 
       - "quanta communicate at runtime, either synchronously or asynchronously"
       - “describes how services call one another at runtime”
       - scalability is the ability to support a large number of concurrent users
       - elasticity is the ability to support a burst of user requests in a short time frame
       - Example : 
         - “ Ticketing is operating at ten times the elastic scale of Assignment, 
           - and we need to make a call between them. If we make a synchronous call, the whole workflow will bog down, as the caller waits for the slower service to process and return. 
           - If on the other hand we make an asynchronous call, using the message queue as a buffer, we can allow the two services to execute operationally independently, 
             - allowing the caller to add messages to the queue and continue working, receiving notification when the workflow is complete.”


Excerpt From
Software Architecture: The Hard Parts
Neal Ford
This material may be protected by copyright.
     - High Functional Cohesive : 
       - “refers structurally to the proximity of related elements: classes, components, services, and so on”
       - “in a microservices architecture, each service models a single domain or workflow, and therefore exhibits high functional cohesion.”
     - Single architecture quantum
       - Even Separate services with same/common DB can have single quorum
       - If services with different DB but console is same where these API's are integrated , then its single quorum
     - Dynamic Quantum : 
       - Consistency : general advice to try to avoid cross-service transactions
       - Co-ordination : coordination the workflow modeled by the communication requires. The two common generic patterns for microservices are orchestration and choreography 