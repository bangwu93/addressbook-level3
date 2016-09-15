# Developer Guide

* [Setting Up](#setting-up)
* [Design](#design)
* [Testing](#testing)
* [Appendix A: User Stories](#appendix-a--user-stories)
* [Appendix B: Use Cases](#appendix-b--use-cases)
* [Appendix C: Non Functional Requirements](#appendix-c--non-functional-requirements)
* [Appendix D: Gloassary](#appendix-d--glossary)

## Setting up

#### Prerequisites

1. **JDK 8** or later 
2. **Eclipse** IDE
3. **e(fx)clipse** plugin for Eclipse (Do the steps 2 onwards given in 
   [this page](http://www.eclipse.org/efxclipse/install.html#for-the-ambitious))


#### Importing the project into Eclipse

0. Fork this repo, and clone the fork to your computer
1. Open Eclipse (Note: Ensure you have installed the **e(fx)clipse plugin** as given in the prerequisites above)
2. Click `File` > `Import`
3. Click `General` > `Existing Projects into Workspace` > `Next`
4. Click `Browse`, then locate the project's directory
5. Click `Finish`

## Design
<img src="images/mainClassDiagram.png"/>

## Testing

* In Eclipse, right-click on the `test/java` folder and choose `Run as` > `JUnit Test`

## Appendix A : User Stories

Priorities: High (must have) - `* * *`, Medium (nice to have)  - `* *`,  Low (unlikely to have) - `*`


Priority | As a ... | I want to ... | So that I can...
-------- | :-------- | :--------- | :-----------
`* * *` | new user | see usage instructions | refer to instructions when I forget how to use the App
`* * *` | user | add a new person | 
`* * *` | user | delete a person | can remove entries that I no longer need
`* * *` | user | find a person by name | locate details of persons without having to go through the entire list
`* * *` | secretive user | have a log-in system | have my personal privacy by not letting others see my contacts
`* *` | user | sort a person by category of contact | to help me find the contacts quicker and more easily
`* *` | user | hide [private contact details](#private-contact-detail) by default | to minimize chance of someone else seeing them by accident
`* *` | administrator | wipe out the contacts | so that when previous users data cannot be seen by subsequent users
`*` | user with many persons in the address book | sort persons by name | locate a person easily


## Appendix B : Use Cases

> do we have to state who are the actors in the system? eg. students, administrators, database etc.

(For all use cases below, the **System** is the `AddressBook` and the **Actor** is the `user`, unless specified otherwise)

#### Use case: Delete person

**MSS**

1. User requests to list persons
2. AddressBook shows a list of persons
3. User requests to delete a specific person in the list
4. AddressBook deletes the person <br>
Use case ends.

**Extensions**

2a. The list is empty

> Use case ends

3a. The given index is invalid

> 3a1. AddressBook shows an error message <br>
  Use case resumes at step 2

#### Use case: Rename Tags

**MSS**

1. User requests to rename tags
2. AddressBook ask user to input the tag name that user wants to change
3. User inputs the tag name that (s)he wants to change
4. AddressBook shows a list of persons with the tags affected and asks for user to confirm the change
5. User confirms the change by typing in "Yes"
6. AddressBook then requests user to input the new name of the tag.
7. AddressBook then searches for all the Taggings with the tag name, and rename the tag names for each of Taggings.

Use case ends.

**Extensions**

3a. There are no persons with the tag user typed in

> 3a1. AddressBook shows an error message: no persons with tag are found <br>
  3a2. AddressBook prompts user to either input tag name again.
  3a3. User enters new tag name.
  Steps 3a1 - 3a3 repeat until a tag name with with persons attached to is entered. Use case then resumes at step 4

3b. The input tag name is invalid

> 3b1. AddressBook shows an error message: input tag name is invalid <br>
  3b2. AddressBook prompts user to either input tag name again.
  3b3. User enters new tag name.
  Steps 3a1 - 3a3 repeat until a valid tag name is entered. Use case then resumes at step 4


## Appendix C : Non Functional Requirements

> Does these non-functional requirements have to include the how and the why? (eg. quick response time because users prefer a responsive system, by implementing log(n) efficiency algorithms)

1. Should work on any [mainstream OS](#mainstream-os) as long as it has Java 8 or higher installed.
2. Should be able to hold up to 1000 persons.
3. Should come with automated unit tests and open source code.
4. Should favor DOS style commands over Unix-style commands
5. Should be able to prevent unauthorised access.
6. Should be able to automatically backup data whenever changes have been made to the storage files.
7. Should have a quick response time of within 2 seconds for every command.

## Appendix D : Glossary

##### Mainstream OS

> Windows, Linux, Unix, OS-X

##### Private contact detail

> A contact detail that is not meant to be shared with others

