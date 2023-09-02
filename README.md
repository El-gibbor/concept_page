![Programming-Concepts-technology-gee](https://github.com/El-gibbor/concept_page/assets/107848793/42ff7704-788f-48fa-931c-a60d62ec269c)
# Concept Page 💫  
A dedicated page that serves as a comprehensive resource for understanding and engaging with the course materials and projects in Alx. This page typically includes explanations, overviews, and information about key concepts, Task exercises/projects, and related topics covered in the course. It is designed to offer guidance, context, and resources to help me learn, successfully complete projects and be a better engineer.  
  
**NB:** This page is regularly updated, you can check back for details to subsequent concepts!
## Tabe of contents🧠
|Concepts|Context|
|:-------:|:---------:|
|[1. Source code management](https://github.com/El-gibbor/concept_page/tree/main#source-code-management)|organize code iterations chronologically|
|[2. Technical Questioning](https://github.com/El-gibbor/concept_page/blob/main/README.md#2%EF%B8%8F%E2%83%A3-technical-questioning)|Why/how to ask or answer|
|[3. White-Boarding](https://github.com/El-gibbor/concept_page/blob/main/README.md#3%EF%B8%8F%E2%83%A3-white-boarding)|Understand, flowchart, pseducode, optimise|
|[4. Test Driven Development](https://github.com/El-gibbor/concept_page/blob/main/README.md#4%EF%B8%8F%E2%83%A3-never-forget-a-test)| Never forget a Test (doc and unit testing)|
|5. Documentation|Right-engineering, right-documenting|
|6. Alx Framework| How to approach and ace a project|
|7. Technical Writing|Articulate and share your Knowledge|
|8. Resources|Python Programming|
|9. Pair Programming|How to|
|10.Data Structures| What are they & how to select the appropriate one|
|11. Vagrant|installation, why and how to use it on your pc|
|12. Simple Shell|Everything you need to know to start coding your own shell|
|13. Malloc and Free|Automatic and Dynamic memory allocation|
|14. Shell|Commands, Shorcuts, manpage|  
  
=========================================================================================  
# 1️⃣ Source code management 
What is source code management?  
It allows a developer to organize code iterations chronologically, and version it for an application. The most powerful features of source code management systems are in how they allow teams of very diverse sizes to work together on the same application simultaneously.  
## Some terms that are common to all of them:  
- A project will be called repository, it’s representing the index/the filesystem root of your project.  
- Developers might create branches of the codebase, that they will iterate on separately to other developers. For instance, a branch can be meant to be used for a given feature, or a given bug fix. One can create however many branches they need.  
- Once a branch is ready for it (it’s been tested, peer-reviewed, etc.), it can be merged back to the main branch. The main branch may be called differently: in Git it’s called master , in SVN it’s called trunk.
While coding on their branch, developers are meant to work in small, atomic iterations, called commits. All commits have a commit message describing in one sentence what’s in there.  
- All commits together are called the history , and it’s a big deal to write meaningful commits and commit messages in order to keep the project’s history clean at a glance, to understand what has been going on and who did what. 
- Some people might be modifying the same pieces on the codebase on different branches, and this could create conflicts when one merges those branches together. Some of those conflicts can obviously only be fixed by a human, and each system has a different way to manage merge conflicts.  
## Which systems exist?
I’ll put each specific wording between quotes. The same words may be used for differing notions across the various products.  
- __SourceSafe__ was an early source code management system from Microsoft, which didn’t handle branches, merges, or conflicts. You could “check out” a file, which meant no one else was allowed to “check it out” and modify it at the same time. When you were done with it, you could “check in” the file, making it editable again to the others. Not very suitable for large teams that may work on the same file, and longer iterations in a given file. SourceSafe is discontinued today.  
- __CVS__ was among the first open-source source code management systems in the industry, and used to be wildly popular, but is barely seen anymore. It didn’t handle branches, but two people could modify the same file at the same time. People would “update” their whole directory to get everybody else’s work before starting, and “commit” their code to the server when they’re done. When they would “commit” a file that had been “committed” by someone else since last time they “updated”, the system was not able to merge, so it would consider it a conflict every time, that you would have to manually fix (even if the changes were not on the same lines, for instance).  
- __SVN__ was built upon CVS to handle branches, so a lot of terminology is the same. At some point, it was the most used system, and it is still seen in the industry, even though people are walking away from it. When you’d create a branch, it would actually copy-paste the whole codebase into another directory in the code repository; then, you’d try to merge, and it would massively compare each file one by one. Merging algorithms were smarter than the CVS ones, but you still had conflicts on most merges, even those that shouldn’t necessarily require a human. When you’d create a “tag” (which is a set version of your code, like “1.2.0”), then the whole codebase would simply be massively copy-pasted into another directory too, but without the intention to merge it back later.  
- __Git__ doesn’t copy-paste the whole codebase when branching and tagging, but stores each commit as a code iteration, in an organized structure that resembles a tree. This allows it to have a much smarter merging algorithm, and it almost never bothers you with conflicts, except for those that really need a human decision. As a result, the cost of branching/merging is very low, and people typically branch/merge a lot, therefore one should never directly work on the “master” branch, if they’re not the only developer on the project. Also: unlike its predecessors, Git allows to work and commit without needing to talk with a server, which allows to work on planes, for instance; and it also can work as a decentralized (peer-to-peer) system, although it’s very rarely done that way.  
- __Mercurial__ is very similar to Git in its concepts (although the syntax of its command-line tool is often different). It is more rarely seen in the industry than Git, but is still very relevant. It is the one used by Facebook, for instance, for its main application.
  
A particularity about Git, is that it’s designed to be useable without a central repository (you can **pull** code from your friend’s computer, and **push** you work back there, for instance), but not many people use it that way. There is usually a central Git server that the whole team **pushes** code to and **pulls** code from; however, that explains why it is often referred as a “decentralized” system.  
So that you can work without a server, the **commit** operation is local, no one other than your computer knows you committed something. You can make several commits however you want, but when you want the server to know about it, you must **push** them there.
You want to be **pulling** from the repository often if other people may be working on the same branch as you, because each pull performs a merge operation between the code you didn’t have, and the code you recently committed locally. Therefore, in order to let you push , Git will sometimes demand that you pull first, so that the merge can be done on your computer, and you take care of potential conflicts.

Sometimes, you may have modified 3 files, but there are only two that you wish to include in the commit you’re about the make. Therefore, Git has a notion of “ index”, in which you add your modified files so that they’re included in the next commit you register.

How to configure the remote servers your local repository is talking to? They’re called remotes , and you can configure however many you need. The main one is typically named origin (that’s the name that is setup by default when you clone a project from a remote location in the first place). You can also configure however many branches you need, and name them as you please, and the default one is usually called master.  
   
Some UI tools for Git exist, but Git is able to do so many things, that they don’t represent the magnitude of cases for which you need Git. You really want to learn to use it with the command line. Here are some commands:  
```shell
elgibbor@ubuntu~elgibbor@ubuntu~$ git clone url_of_your_remote_repository   # Clone a repository from a remote repository  
elgibbor@ubuntu~$ git add file1 file2    # will add those two files to the index if they were modified  
elgibbor@ubuntu~$ git commit -m "Meaningful commit message"   # will commit those two files (locally)  
elgibbor@ubuntu~$ git add .   # will add all of the modified files to the index at once  
elgibbor@ubuntu~$ git commit -m "Other meaningful commit message"   # will commit all of those files together  
elgibbor@ubuntu~$ git push origin master   # send all commit to the remote server
```
Now, let’d do this again, but by on a branch:  
```shell
elgibbor@ubuntu~$ git branch my_feature   # Creating the branch  
elgibbor@ubuntu~$ git checkout my_feature   # Changing the codebase so that we're on that branch now  
elgibbor@ubuntu~$ git checkout -b my_feature   # This does the two previous operations in one ;)  
elgibbor@ubuntu~$ git add file1 file2  
elgibbor@ubuntu~$ git commit -m "Meaningful commit message"   # We didn't just commit this on the master branch like last time, but on the my_feature one  
elgibbor@ubuntu~$ git add .  
elgibbor@ubuntu~$ git commit -m "Other meaningful commit message"  
elgibbor@ubuntu~$ git push origin my_feature   # Notice: we're not pushing master anymore, you just create a new remote branch
```
Next time you want to work on that branch, you should probably do this first:  
```shell
elgibbor@ubuntu~$ git checkout my_feature   # Just making sure you're currently on the right branch!  
elgibbor@ubuntu~$ git pull origin my_feature   # Pulling what your coworkers have done so far.
```
And when you’re done with the whole feature and want to merge it to master:  
```shell
elgibbor@ubuntu~$ git checkout master  
elgibbor@ubuntu~$ git merge my_feature
``` 
One other pretty neat thing: if you have a non-Git directory in your computer, and you want to turn it into a Git repository, it’s that easy:  
```shell
elgibbor@ubuntu~$ git init   # You're done!  
elgibbor@ubuntu~$ git remote add origin url_of_your_git_server   # So that you can push your code somewhere.
```
When you’re in a Git repository, and want to know which files are modified but not in the index, and those that are modified and are in the index, you can run:  
```shell
elgibbor@ubuntu~$ git status
```
Git provides many more abilities, such as rewriting pieces of the history of the project if you feel the commits were not meaningful enough, displaying the history in visually meaningful ways, …  
  
**For instance, you should run this right now, and see how a complex history can be viewed really nicely:**  
```shell
elgibbor@ubuntu~$ git clone [https://github.com/loverajoel/jstips.git](https://github.com/loverajoel/jstips.git)   # You will need a GitHub account for this to work  
elgibbor@ubuntu~$ cd jstips   # changing your directory into the one you just downloaded  
elgibbor@ubuntu~$ git log --graph --pretty=tformat:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%an %cr)%Creset' --abbrev-commit --date=relative
```
Cool, right?  
## What is the difference between Git and GitHub?
Git is everything we’ve covered so far: a source code management tool, that comes with a command-line tool for its users.  
GitHub is one of many services that provide at the same time:  
- a Git repository server to push your code to
- a web UI to that view your repositories, with their files and commits
- a number of extra features (managing your team and accesses, …) Two GitHub features you have to get familiarized with are:  
- **Forks:** you can fork any repository on GitHub, and it will duplicate the repository’s codebase into repository that you own. For instance, if you fork twbs/bootstrap, and your GitHub username is “my_username”, then it will create the my_username/bootstrap repository, and it will remember where it was forked from. Usually, you aren’t allowed to push on other people’s repositories, so that will give you a repository that you can push to, since you own it.  
- **Pull requests:** once you’ve pushed your code to your repository (or sometimes to a branch of the main repository, if you’re allowed), then you can create a pull request towards the main repository’s master branch. Somebody in charge of the main repository will review your pull request (potentially asking you to change a couple of things), and merge it if it’s suitable to be in the main product.

GitHub has many competitors, two of the main ones being GitLab and BitBucket (which provide very similar services). We chose to make you use GitHub because that’s where most of the industry is (that way, you’ll be able to interact with them on their open-source projects), and it’s also where tech recruiters typically go check out to see what you’ve been up to.  
## Some interesting links about Git  
[Interactive tutorial for beginners](https://intranet.alxswe.com/rltoken/Yo5sfG-qfPTQ5wkJ3mh4TA) - try.github.io  
[list of resources about Git](https://intranet.alxswe.com/rltoken/qaMLmt-Ly9w4b63v68I94g) - Curated by Github  
[Git from the inside out](https://intranet.alxswe.com/rltoken/AGmLa9Evzc9MI8dP9SFOcQ) - Graph structure that underpins Git  
[Learning git branching](https://intranet.alxswe.com/rltoken/OAvUt-4nF_R3xb_cC20fqw) - Practice with a game  
[Successful git branching model](https://intranet.alxswe.com/rltoken/Xv4OUmdgaAqZc6xNIbj5Qw) - once you master the technical tool, you have many ways to organize your branches according to your project. This very notorious article from 2010 introduces git-flow , a detailed proposal for organizing collective work with Git that is still the most common today. You should talk about that each time you start a collaborative project using Git.  
http://semver.org: - now that you can give version numbers to your code iterations, how should you number them? Semantic versioning is the most used versioning scheme.  

=========================================================================================  
# 2️⃣ Technical Questioning   
Being a software engineer means constant learning and questioning. Whether you’re a newbie developer or an experienced one, you are bound to find yourself banging your head against a wall, trying to figure out why the program you just wrote is not working the way you want.  
To become a better developer, there are two essential skills you need:  
- **Find answers to your questions:** Manual pages and documentation usually contain apt explanations. posting a question without doing your homework is disrespectful to the community, and other developers will instantly see whether you really need their help or are just fishing for somebody to do the heavy lifting for you;  
- **Ask good technical questions:** The better you express your inquiry to others, the more effective they will respond to you.  
## How to ask good technical questions  
- **Sum up your question in a title:** this will act as a heading for your question.  
- **Provide context:** this helps people understand your question better because they’ll know what situation you’re dealing with and any parameters that might affect how they answer. It would also help to mention the project and task number that you need assistance with.
- **Provide code sample:** include a minimal reproducible example if your question depends on code. It should be minimal and have no irrelevant bits of code. Only show code that directly affects the example’s completion and the issue at hand.  
- **Avoid using screenshots:** typing the question builds your confidence to explain yourself in text, a very important soft-skill.  
- **Share what you’ve already tried:** Your last attempt may be one tiny step away from fixing the problem. Without listing what you’ve tried, people will have to debug the problem from the very start.
- **Format, Lint, and Document Your Code:** No one wants to read code that is all on the same line with bad indentation, variable naming inconsistencies, or bad style in general. Follow popular conventions if possible. Document your code. When sending code in slack, format it to appear as code.  
- **Grammar-Check Your Question:** questions with grammatical errors are hard to decipher. This makes it hard to read and limits the number of people that can help you.  
- **Keep track of your question:** Once you ask a question and you get an answer, don’t just desert the whole thing. Don’t just ghost the people that are trying to help you. Provide feedback. Tell them what worked, what didn’t work, and why. When your question has been answered, edit the original message and add: ✅ Solved  
- **Be humble:** you won’t always get cheerful, welcoming, or happy responses. People have lives in which they could be facing problems. If you push people too much, they may start to ignore you or delete their responses altogether. Respect people’s privacy, and give them space.  
## Why you should ask and answer technical questions  
- **You learn how to ask questions:** A well-crafted question that ignites a helpful discussion and uncovers brilliant answers is often rated as highly as the best-given answer.  
- **You will gain a better understanding of the problem:** when you pose a question, you will be asked to think and explain your reasoning. As a result, you will examine and assess your issue while asking questions, which may lead to you discovering the solution.  
- **You learn by answering questions:** Explaining something that you already know to others makes your knowledge stronger and often uncovers new knowledge. When you write an answer to a question, you try to make it as clear and comprehensive as possible. Because of this attention to detail, you will often get back to something you did not pay initial attention to, totally forgot, or never knew in the first place.  
=========================================================================================   
# 3️⃣ White boarding  
In real-world projects, your brain should be able to write a quick efficient solution for complicated stuff and you can only do that when you practice a lot of coding questions. Understand that language and frameworks are just tools, they won’t teach you problem-solving skills. You develop problem-solving skills when you practice a lot of coding questions.  
  
Every developer has their own tricks and they follow their own pattern to solve coding problems but when it comes to new developers they are always uncertain about where to start. A lot of them understand the problems, the logic, and the basics of syntax, they also understand someone else codes and they can follow along with them but when it comes to solving the questions on their own, they get stuck. They don’t understand how to turn their thoughts into code even though they understand the syntax or logic. This article is a result of mass research of how programmers effectively approach a coding problem.  
## Step 1: Understand and Analyze the Problem  
It doesn’t matter if you have seen the question in the past or not, read the question several times and understand it completely. Now, think about the question and analyze it carefully. Sometimes we read a few lines and assume the rest of the things on our own but a slight change in your question can change a lot of things in your code so be careful about that. Now take a paper and write down everything. What is given (input) and what you need to find out (output)? While going through the problem you need to ask a few questions yourself…  
  
Did you understand the problem fully? Would you be able to explain this question to someone else? What and how many inputs are required? What would be the output for those inputs Do you need to separate out some modules or parts from the problem? Do you have enough information to solve that question?  
## Step 2: Go Through The Sample Data And Examples Thoroughly  
When you try to understand the problem take some sample inputs and try to analyze the output. The sample inputs will help you to understand the problem in a better way. You will also get clarity that how many cases your code can handle and what all can be the possible output or output range. Consider some simple inputs or data and analyze the output. Consider some complex and bigger input and identify what will be the output and how many cases you need to take for the problem. Consider the edge cases as well. Analyze what would be the output if there is no input or if you give some invalid input. Step 3: Break Down The Problem When you see a coding question that is complex or big, instead of being afraid and getting confused that how to solve that question, break down the problem into smaller chunks and then try to solve each part of the problem. Below are some steps you should follow in order to solve the complex coding questions…   
## Make a flow chart for the problem at hand.  
Divide the problem into sub-problems or smaller chunks. Solve the subproblems. Make independent functions for each subproblem. Connect the solutions of each subproblem by calling them in the required order, or as necessary. Wherever it’s required use classes and objects while handling questions (for real-world problems like management systems, etc.)  
## Step 4: Write Pseudocode, make a flowchart  
Before you jump into the solution it’s always good to write pseudocode for your problem. Basically, pseudocode defines the structure of your code and it will help you to write every line of code that you need in order to solve the problem. Reading pseudocode gives a clear idea that what your code is supposed to do. A lot of people or experienced programmers skip this step but when you write pseudocode the process of writing the final code becomes easier for you. In the end, you will have to only translate each line of pseudocode into actual code. So write down every step and logic in your pseudocode. Step 5: Replace Pseudocode With Real Code Once you have written the pseudocode it’s time to translate this into actual code. Replace each line of your pseudocode into real code in the language you are working on. If you have divided your problem into subproblems then write down the code for each subproblem. While writing the code keep in mind three things…  
  
The point where you started * Where are you right now? * What is your destination (end result)?  
## Step 6: Simplify and Optimize your Code  
Always try to improve your code. Look back, analyze it once again and try to find a better or alternate solution. We have mentioned earlier that you should always try to write the right amount of good code so always look for the alternate solution which is more efficient than the previous one. Writing the correct solution to your problem is not the final thing you should do. Explore the problem completely with all possible solutions and then write down the most efficient or optimized solution for your code. So once you are done with writing the solution for your code below are some questions you should ask yourself.  

=========================================================================================  
# 4️⃣ Never forget a test  
Testing is the process of evaluating a system or its component(s) with the intent to find whether it satisfies the specified requirements or not. Testing is executing a system in order to identify any gaps, errors, or missing requirements contrary to the actual requirements. This tutorial will give you a basic understanding of software testing, its types, methods, levels, and other related terminologies.  
  
*__Code that is not tested can’t be trusted!__*

## Bad reputation  
- __“Testing is Too Expensive”:__ Pay less for testing during software development => pay more for maintenance or correction later. Early testing saves both time and cost in many aspects. However, reducing the cost without testing may result in improper design of a software application, rendering the product useless.  
- **“Testing is Time-Consuming”:** Testing is never a time-consuming process. However diagnosing and fixing the errors identified during proper testing is a time-consuming but productive activity.
“Only Fully Developed Products are Tested”: No doubt, testing depends on the source code but reviewing requirements and developing test cases is independent from the developed code. However, iterative or incremental approaches to a development life cycle model may reduce the requirement of testing on the fully developed software.  
- **“Complete Testing is Possible”:** It becomes an issue when a client or tester thinks that complete testing is possible. It is possible that all paths have been tested by the team but occurrence of complete testing is never possible. There might be some scenarios that are never executed by the test team or the client during the software development life cycle and may be executed once the project has been deployed.  
- **“A Tested Software is Bug-Free”:** No one can claim with absolute certainty that a software application is 100% bug-free even if a tester with superb testing skills has tested the application.
“Testers are Responsible for Quality of Product”: It is a very common misinterpretation that only testers or the testing team should be responsible for product quality. Testers’ responsibilities include the identification of bugs to the stakeholders and then it is their decision whether they will fix the bug or release the software. Releasing the software at the time puts more pressure on the testers, as they will be blamed for any error.  
- **“Test Automation should be used wherever possible to Reduce Time”:** Yes, it is true that Test Automation reduces the testing time, but it is not possible to start test automation at any time during software development. Test automaton should be started when the software has been manually tested and is stable to some extent. Moreover, test automation can never be used if requirements keep changing.  
## Basic  
This standard deals with the following aspects to determine the quality of a software application:  
- Quality model  
- External metrics  
- Internal metrics  
- Quality in use metrics
  
This standard presents some set of quality attributes for any software such as:  
- Functionality  
- Reliability  
- Usability  
- Efficiency  
- Maintainability  
- Portability  
## Functional Testing    
This is a type of black-box testing that is based on the specifications of the software that is to be tested. The application is tested by providing input and then the results are examined that need to conform to the functionality it was intended for. Functional testing of a software is conducted on a complete, integrated system to evaluate the system’s compliance with its specified requirements.  

There are five steps that are involved while testing an application for functionality:  
- The determination of the functionality that the intended application is meant to perform.  
- The creation of test data based on the specifications of the application.  
- The output based on the test data and the specifications of the application.  
- The writing of test scenarios and the execution of test cases.  
- The comparison of actual and expected results based on the executed test cases.
  
An effective testing practice will see the above steps applied to the testing policies of every organization and hence it will make sure that the organization maintains the strictest of standards when it comes to software quality.  
## Unit Testing  
This type of testing is performed by developers before the setup is handed over to the testing team to formally execute the test cases. Unit testing is performed by the respective developers on the individual units of source code assigned areas. The developers use test data that is different from the test data of the quality assurance team.   
  
The goal of unit testing is to isolate each part of the program and show that individual parts are correct in terms of requirements and functionality.  
  
Limitations of Unit Testing:  
  
- Testing cannot catch each and every bug in an application. It is impossible to evaluate every execution path in every software application. The same is the case with unit testing.  
- There is a limit to the number of scenarios and test data that a developer can use to verify a source code. After having exhausted all the options, there is no choice but to stop unit testing and merge the code segment with other units.  
## Integration Testing  
Integration testing is defined as the testing of combined parts of an application to determine if they function correctly. Integration testing can be done in two ways: Bottom-up integration testing and Top-down integration testing.  
- **Bottom-up integration:** This testing begins with unit testing, followed by tests of progressively higher-level combinations of units called modules or builds.  
- **Top-down integration:** In this testing, the highest-level modules are tested first and progressively, lower-level modules are tested thereafter.  
In a comprehensive software development environment, bottom-up testing is usually done first, followed by top-down testing. The process concludes with multiple tests of the complete application, preferably in scenarios designed to mimic actual situations.  
## System Testing  
System testing tests the system as a whole. Once all the components are integrated, the application as a whole is tested rigorously to see that it meets the specified Quality Standards. This type of testing is performed by a specialized testing team.  
  
System testing is important because of the following reasons:  
- System testing is the first step in the Software Development Life Cycle, where the application is tested as a whole.  
- The application is tested thoroughly to verify that it meets the functional and technical specifications.
- The application is tested in an environment that is very close to the production environment where the application will be deployed.  
- System testing enables us to test, verify, and validate both the business requirements as well as the application architecture.  
## Regression Testing  
Whenever a change in a software application is made, it is quite possible that other areas within the application have been affected by this change. Regression testing is performed to verify that a fixed bug hasn’t resulted in another functionality or business rule violation. The intent of regression testing is to ensure that a change, such as a bug fix should not result in another fault being uncovered in the application.  
  
Regression testing is important because of the following reasons:  
- Minimize the gaps in testing when an application with changes made has to be tested.  
- Testing the new changes to verify that the changes made did not affect any other area of the application.  
- Mitigates risks when regression testing is performed on the application.  
- Test coverage is increased without compromising timelines.  
- Increase speed to market the product.  
## Acceptance Testing 
This is arguably the most important type of testing, as it is conducted by the Quality Assurance Team who will gauge whether the application meets the intended specifications and satisfies the client’s requirement. The QA team will have a set of pre-written scenarios and test cases that will be used to test the application.  
  
More ideas will be shared about the application and more tests can be performed on it to gauge its accuracy and the reasons why the project was initiated. Acceptance tests are not only intended to point out simple spelling mistakes, cosmetic errors, or interface gaps, but also to point out any bugs in the application that will result in system crashes or major errors in the application.  
  
By performing acceptance tests on an application, the testing team will deduce how the application will perform in production. There are also legal and contractual requirements for acceptance of the system.  
## Alpha Testing  
This test is the first stage of testing and will be performed amongst the teams (developer and QA teams). Unit testing, integration testing and system testing when combined together is known as alpha testing. During this phase, the following aspects will be tested in the application:  
- Spelling Mistakes  
- Broken Links  
- Cloudy Directions  
- The Application will be tested on machines with the lowest specification to test loading times and any latency problems.  
## Beta Testing  
This test is performed after alpha testing has been successfully performed. In beta testing, a sample of the intended audience tests the application. Beta testing is also known as pre-release testing. Beta test versions of software are ideally distributed to a wide audience on the Web, partly to give the program a “real-world” test and partly to provide a preview of the next release. In this phase, the audience will be testing the following:  
- Users will install, run the application and send their feedback to the project team.  
- Typographical errors, confusing application flow, and even crashes.  
- Getting the feedback, the project team can fix the problems before releasing the software to the actual users.  
- The more issues you fix that solve real user problems, the higher the quality of your application will be.  
- Having a higher-quality application when you release it to the general public will increase customer satisfaction.  
## Non-Functional Testing   
This section is based upon testing an application from its non-functional attributes. Non-functional testing involves testing a software from the requirements which are nonfunctional in nature but important such as performance, security, user interface, etc.  
  
Some of the important and commonly used non-functional testing types are discussed below.  
## Performance Testing
It is mostly used to identify any bottlenecks or performance issues rather than finding bugs in a software. There are different causes that contribute in lowering the performance of a software:  
- Network delay  
- Client-side pro  cessing
- Database transaction processing  
- Load balancing between servers  
- Data rendering  
Performance testing is considered as one of the important and mandatory testing type in terms of the following aspects:  
- Speed (i.e. Response Time, data rendering and accessing)  
- Capacity  
- Stability  
- Scalability  
Performance testing can be either qualitative or quantitative and can be divided into different sub-types such as Load testing and Stress testing.  
## Load Testing  
It is a process of testing the behavior of a software by applying maximum load in terms of software accessing and manipulating large input data. It can be done at both normal and peak load conditions. This type of testing identifies the maximum capacity of software and its behavior at peak time.  
  
Most of the time, load testing is performed with the help of automated tools such as Load Runner, AppLoader, IBM Rational Performance Tester, Apache JMeter, Silk Performer, Visual Studio Load Test, etc.  
  
Virtual users (VUsers) are defined in the automated testing tool and the script is executed to verify the load testing for the software. The number of users can be increased or decreased concurrently or incrementally based upon the requirements.  
## Stress Testing  
Stress testing includes testing the behavior of a software under abnormal conditions. For example, it may include taking away some resources or applying a load beyond the actual load limit.  
  
The aim of stress testing is to test the software by applying the load to the system and taking over the resources used by the software to identify the breaking point. This testing can be performed by testing different scenarios such as:  
- Shutdown or restart of network ports randomly  
- Turning the database on or off  
- Running different processes that consume resources such as CPU, memory, server, etc.  
## Usability Testing  
Usability testing is a black-box technique and is used to identify any error(s) and improvements in the software by observing the users through their usage and operation.  
  
According to Nielsen, usability can be defined in terms of five factors, i.e. efficiency of use, learn-ability, memory-ability, errors/safety, and satisfaction. According to him, the usability of a product will be good and the system is usable if it possesses the above factors.    
  
Nigel Bevan and Macleod considered that usability is the quality requirement that can be measured as the outcome of interactions with a computer system. This requirement can be fulfilled and the end-user will be satisfied if the intended goals are achieved effectively with the use of proper resources.  
  
Molich in 2000 stated that a user-friendly system should fulfill the following five goals, i.e., easy to Learn, easy to remember, efficient to use, satisfactory to use, and easy to understand.  
  
In addition to the different definitions of usability, there are some standards and quality models and methods that define usability in the form of attributes and sub-attributes such as ISO-9126, ISO-9241-11, ISO-13407, and IEEE std.610.12, etc.  
## UI vs Usability Testing 
UI testing involves testing the Graphical User Interface of the Software. UI testing ensures that the GUI functions according to the requirements and tested in terms of color, alignment, size, and other properties.  
  
On the other hand, usability testing ensures a good and user-friendly GUI that can be easily handled. UI testing can be considered as a sub-part of usability testing.
  
## Security Testing  
Security testing involves testing a software in order to identify any flaws and gaps from security and vulnerability point of view. Listed below are the main aspects that security testing should ensure:  
- Confidentiality  
- Integrity  
- Authentication  
- Availability  
- Authorization  
- Non-repudiation  
- Software is secure against known and unknown vulnerabilities  
- Software data is secure  
- Software is according to all security regulations  
- Input checking and validation  
- SQL insertion attacks  
- Injection flaws  
- Session management issues  
- Cross-site scripting attacks  
- Buffer overflows vulnerabilities  
- Directory traversal attacks  
## Portability Testing  
Portability testing includes testing a software with the aim to ensure its reusability and that it can be moved from another software as well. Following are the strategies that can be used for portability testing:  
- Transferring an installed software from one computer to another.  
- Building executable (.exe) to run the software on different platforms.  
Portability testing can be considered as one of the sub-parts of system testing, as this testing type includes overall testing of a software with respect to its usage over different environments. Computer hardware, operating systems, and browsers are the major focus of portability testing. Some of the pre-conditions for portability testing are as follows:  
- Software should be designed and coded, keeping in mind the portability requirements.  
- Unit testing has been performed on the associated components.  
- Integration testing has been performed.  
- Test environment has been established.  
## Test Plan  
A test plan outlines the strategy that will be used to test an application, the resources that will be used, the test environment in which testing will be performed, and the limitations of the testing and the schedule of testing activities. Typically the Quality Assurance Team Lead will be responsible for writing a Test Plan.  
  
A test plan includes the following:  
- Introduction to the Test Plan document  
- Assumptions while testing the application  
- List of test cases included in testing the application  
- List of features to be tested  
- What sort of approach to use while testing the software  
- List of deliverables that need to be tested  
- The resources allocated for testing the application  
- Any risks involved during the testing process  
- A schedule of tasks and milestones to be achieved
## Test Scenario   
It is a one line statement that notifies what area in the application will be tested. Test scenarios are used to ensure that all process flows are tested from end to end. A particular area of an application can have as little as one test scenario to a few hundred scenarios depending on the magnitude and complexity of the application.  
  
The terms ‘test scenario’ and ‘test cases’ are used interchangeably, however a test scenario has several steps, whereas a test case has a single step. Viewed from this perspective, test scenarios are test cases, but they include several test cases and the sequence that they should be executed. Apart from this, each test is dependent on the output from the previous test.  
## Test Case  
Test cases involve a set of steps, conditions, and inputs that can be used while performing testing tasks. The main intent of this activity is to ensure whether a software passes or fails in terms of its functionality and other aspects. There are many types of test cases such as functional, negative, error, logical test cases, physical test cases, UI test cases, etc.  
  
Furthermore, test cases are written to keep track of the testing coverage of a software. Generally, there are no formal templates that can be used during test case writing. However, the following components are always available and included in every test case:  
- Test case ID  
- Product module  
- Product version  
- Revision history  
- Purpose  
- Assumptions  
- Pre-conditions  
- Steps  
- Expected outcome  
- Actual outcome  
- Post-conditions
  
Many test cases can be derived from a single test scenario. In addition, sometimes multiple test cases are written for a single software which are collectively known as test suites.  

=========================================================================================  
