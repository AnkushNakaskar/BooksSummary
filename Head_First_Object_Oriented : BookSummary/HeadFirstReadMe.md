## Head First Object Oriented Design
#### Gathering requirements : (Use cases)
- Get the requirement in clean understanding before jump into solution
  - Get question and corner cases ready 
  - To make sure requirements are solid and well understood
  - To make it easy list down the steps or flows which will happen like interactions 
  - **most people expect things to work even if problems occur.** 
    - So you’ve got to anticipate what might go wrong, 
    - and add requirements to take care of those problems as well. 
  - That means you’ve got to really understand what the system has to do, and how your customers are going to use it.
  - **_You have to come up with all the BAD things that might come up and solve those_**
    - To picture these, follow steps and ask 
    - does this step happen like this only what if he does not follow happy path , what are the other paths/option he has. 
      - like person is going to upload file, does he is doing to upload any file
  - Use Case : 
    - one of the key points about a use case is that it is focused on accomplishing one particular goal. 
    - If your system does more than one thing—
      - like let File upload and track how many times upload activity occurred an entire day—then you’ll need more than one use case.
  - All the BAD use cases /alternate path need to be setup and check with Unit tests and integration tests
#### Requirement Change
- In real world, requirement always change as previous product delivered is used
- Sometimes a change in requirements reveals problems with your system that you didn’t even know were there.

#### Software into real world
- Software will be given in real world, has to think from their lenses, it can have multiple scenarios and different type of users
- **Analysis** : 
  - Identify the problem
  - your use cases let you show customers, managers, and other developers how your system works in a real world context.
- To design loosely couple application :
  - Need to delegate the functionality to respective classes like UploadValidator etc.
  - Think from object perspective , 
    - don't go for single fields or working around it, ask yourself , 
      - does this fall into separate functionality , 
      - shall i make it separate class ?
- **_Really important: the nouns in a use case are usually the classes you need to write and focus on in your system._**
  - Like in File Upload use case, File is very important, you can ask many questions around it like 
    - Type of File, Size of File etc.
    - Design application around that.
    - You really don’t need to focus too much on grammar. 
      - Just write your use cases in conversational English (or whatever language you speak and write in). 
      - Then figure out what the “things” are in your use case—those are generally the nouns. For each noun, think about if you need a class to represent it, 
      - and you’ve got a good start on a real-world analysis of your system
  - **_Entity class/Object Class : Almost every noun in use case is the classes in application_**
- Correct Requirements/Use cases make the application useful to customer and cover all the path, so always try to get requirement clear
- When you write your use case, reread it, and make sure that it makes sense to you. You might even want to let a couple of friends or co-workers read through it, too, and make sure it will work in the real world, not just in a controlled environment.
- UML diagrams of class are important : 
  - Rewriting code takes a lot more time than rewriting a use case or redrawing a class diagram...
  - Arrow from one class to another , mention that target is field in calling class, 
    - like Arrow can be from Employee -> Address
- Each use case should focus on only one customer goal. If you have multiple goals, you will need to write multiple use cases.
- It gives us a way to avoid multiple classes just for different behaviour , 
  - like in Type of instrument, we were extending classes, which can be delay as subclass of specification
  - ```
    Banjo extends Instrument{
     public Banjo(String name, InstrumentSpec)
    }
    ```
  - To have separate concrete class of Instrument as a one , dont have separate classes for each and every instrument 
    - You can structure it as below
    ![](MultipleClassesOfInstrumentToOnlyOne.png)
    - As the above image explain , how we made Instrument class as a concrete class and extends the behaviour to specific class
    - Now, we dont need to create new class of every Instrument since every details are given to SpecificClass
    - Whenever someone want to search instruments or do some filters, they just have to invoke ``matches(InstrumentSpec)`` method
      - Since every spec is concrete class, we will pass that in matches method, it will behave it respectively 

#### Solving Really Big Problem
  - Every big problem is solved once you solve the small problems of this big problem
  - **_Points to be considered_**
    - By encapsulating what varies, you make your application more flexible, and easier to change.
    - Coding to an interface, rather than to an implementation, makes your software easier to extend.
    - The best way to get good requirements is to understand what a system is supposed to do.
    - Analysis helps you ensure your system works in a real-world context.
  - **Use case diagrams**
    - Sometimes you need to know what a system does, but don’t want to get into all the detail that use cases require. When you’re in a situation like this, a use case diagram could be just what you need:
    - Take your use case diagram, and make sure that all the use cases you listed will cover all the features you got from the customer like below
     ![](usecase.png)
    - **Domain analysis**
      - Once use cases are completed, check for domain analysis of every use cases like responsibility of every class/module
      - To be specific : 
        - Have all the feature list of every use cases
        - Explain how they are solving big problem, make sure all use cases are covered
      - Once every requirement is covered , now use
      - **_Divide and Conquer_**
    - Don’t forget who your customer really is
      - Solve for those people only and their perspective and use cases are covered
      - Always ask yourself if this use cases belong to your module or application

#### Architecture: Bringing Order to Chaos
  - Architecture is the organizational structure of a system, including its decomposition into parts, their connectivity, interaction mechanisms, and the guiding principles and decisions that you use in the design of a system.
  - Even if we know to start by focusing on functionality, we still need to figure out which pieces are the most important. Those are the pieces we want to focus on first.
  - **The three Qs of architecture**
    - Is it part of the essence of the system?
      - Is the feature really core to what a system actually is? Think about it this way: can you imagine the system without that feature? If not, then you’ve probably found a feature that is part of the essence of a system.
    - What the heck does it mean?
      - If you are not sure what this particular feature mean or works , get it first clear on priority
    - How the “heck” do I do it? 
      - features that seem really hard to implement, or are totally new programming tasks for you. If you have no idea how you’re going to tackle a particular problem, you better spend some time up front looking at that feature, 
      - so it doesn’t create lots of problems down the road.
    - All the Q's answer are basically the solving the RISK for project, hence you can work on parallel to solve those all Q's
      - The reason that these features are architecturally significant is that they all introduce RISK to your project. It doesn’t matter which one you start with—as long as you are working towards reducing the RISKS in succeeding.
    - Reducing risk : 
      - Since three Q's are here to help you with Reducing RISK,
      - But you also need to find all the scenario's, like designing Board for GAME, think of scenario's using board for playing game.



