# Software Architecture: The Hard Parts : BooksSummary
 ##### Chapter 2 :
   - Trade-off analysis :
      - analyzing what parts are coupled to one another and what impact that coupling has on change 
   - Coupling : 
     - Static : 
       - dependencies include operating system, frameworks and/or libraries delivered via transitive dependency management
       - “ describes how services are wired together”
       - “service must contain dependent components such as a database, representing static coupling”
     - Dynamic : 
       - "quanta communicate at runtime, either synchronously or asynchronously"
       - “describes how services call one another at runtime”
     - High Functional Cohesive : 
       - “refers structurally to the proximity of related elements: classes, components, services, and so on”
       - “in a microservices architecture, each service models a single domain or workflow, and therefore exhibits high functional cohesion.”
     - Single architecture quantum
       - Even Separate services with same/common DB can have single quorum
       - If services with different DB but console is same where these API's are integrated , then its single quorum 