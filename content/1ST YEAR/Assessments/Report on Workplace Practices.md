---
tags:
  - How_to_Learn_a_New_Language
---

Overview of Projects
---

The software developed at Wood Mackenzie provides a service for viewing and comparison of assets and metrics related to the energy sector. Within the Power Rangers team, we work within the Power section of the platform, focusing mainly on front end development and use TypeScript as it provides improved type security over plain JavaScript. Commonly, the IDE of choice for this team is VS Code combined with various extensions to assist development. During development the software is run locally on a Linux virtual machine and docker - a platform which serves as a common environment to run the application.

Critical Evaluation of Programming Practices
---

Coding practices and organisation of the repository appear to be cleanly organised in a logical, modular manner which greatly assists navigation. Module, variable and method names follow standard naming conventions utilising pascal case for files , components, and types; and camel case for variables and methods. This practice allows for easy discernment between the two thus improving readability.
<INSERT SCREENSHOT NAMINGCONVENTION>

Furthermore, consistent style is imposed across the entire repository via linting checks with non-compliant pull requests rejected from merging to the master branch. This improves readability by ensuring all files follow the same formatting regardless of author(s).

ERROR HANDLING AND TYPES

While error handling is often handled using try-catch blocks, this is mostly limited to code involving API resolvers and queries. The reasoning for this appears to be due to heavy reliance on type checking combined with extensive use of custom types. Since many such custom types declare object structures which themselves are based on custom types, such reliance on type checking to prevent (rather than handle) errors appears not to be misplaced. This approach highlights the utility and benefits of using a typed language for development as it constrains the developer into writing code which can safely be run.
<INSERT SCREENSHOT CUSTOMTYPE>

Custom types also commonly utilise enums as opposed to strings in order to further utilise the benefits of type checking.
<INSERT SCREENSHOT ENUM>

It’s worth noting that consideration is given to occasions where it may not be possible to prevent errors entirely, in which case it’s necessary to throw errors.
<INSERT SCREENSHOT THROWERROR>

Considering the end-user's perspective, the above approach appears to be the favourable solution as revealing errors to users would be undesirable. Preventing such ensures a more streamlined solution to continuous development as it prevents formation of numerous bug tickets and speeds up quality assurance testing. Ultimately, undesirable (yet usable) behaviour is preferred over broken software.

DATA STRUCTURES

The most commonly used data structures within this repository are objects and arrays - often with the former converted to/from JSON format. As most data structures utilise custom types, this allows a set framework for the developers to work within to ensure cross-repository compatibility and a framework regarding the shape of data in various contexts such that the codebase becomes somewhat self-documenting. Required types can be seen for a particular case to ensure data is passed of the same type; In doing so type definitions can be used to ensure the data structure built has the correct contents organised in the correct fashion. This puts the developer, IDE/compiler and codebase in a collaborative relationship, thus preventing time lost and frustration involved in investigating how code changes must be built to reduce errors or undesirable outputs.

<INSERT SCREENSHOT Interface>

It’s very common within map modules to import or export data via GeoJSON format which allows data to be passed between the mapbox and geoserver APIs. Much of the repository's custom objects are therefore defined with this in mind to facilitate communication between the software and its dependencies.
<INSERT SCREENSHOT toJSON>

Arrays are also used, particularly when aggregating multiple objects or elements thereof. Such usage maintains the object-oriented approach implemented across the repository while allowing built-in array methods to be used. 

<INSERT SCREENSHOT getIntersected>

VARIABLES AND METHODS

Commonly, variables are defined using arrow functions. While this can be beneficial for style and controlling scope, it can result in a few issues regarding debugging and readability (particularly where variable names don't clearly indicate it is a function). Since arrow functions are anonymous, problems may be difficult to track when looking at error stack traces. This can however be mitigated in various ways for example by using arrow functions to wrap a specific series of named functions, calling them within classic functions, and ensuring they are not overly complex (thus reducing the chance of bugs).


<INSERT SCREENSHOT arrowFunction>

CONTROL

Means of controlling the flow logic are used extensively and show clear preference for a readable, optimised, and well considered approach. This is evidenced throughout the repository such as in the below example which uses switch cases inside of if statements - an approach which is both readable and more performant than nesting ifs or switches as well as exemplifying best practices regarding the use of either option. 


<INSERT SCREENSHOT ifVsSwitch>

Consideration for specific use cases can further be shown below regarding loops. In this example, 'for each' has been chosen for iteration through a finite set which is preferable for performance and readability over constructing a regular for loop. Conversely, typical for loop construction can be seen inside and has been chosen as the start and end integers are defined by data other than the length of the data structure. Preference is therefore to use 'for each' when possible, thus improving readability of the code, particularly when nesting loops.


<INSERT SCREENSHOT forInForEach>


Personal Contribution

My own contribution towards the codebase aims to fix a bug related to a discrepancy in the coordinate system used for selections. This required translating geographical coordinates to a Cartesian system for the process of determining which assets lie within a given selection.

The main part of this code was to create a method which takes the original data structure of either the selection or asset and converts the coordinates within. Since the shape of such data structure varies, I implemented an overloaded method which will accept any of the possible nested depths and recursively finds and converts each coordinate. 


<INSERT SCREENSHOT PersonalContribution0v2>

The notable aspects of this are that an (attempted) deep copy is made of the initial data structure so as to not modify the original data, and multiple overloads required to avoid reliance on '@ts-ignore'. Both of these aspects are somewhat problematic and were therefore later adjusted. While overloaded methods were a prominent feature in the course material on Object Oriented Programming, this was not common within our codebase as it often resulted in a messier file.

I also implemented a type guard to check if the position reached in the data structure was a coordinate position based on previously defined custom types. Such practice is necessary in this situation to avoid errors or reliance on ‘@ts-ignore’. Surprisingly, type guards aren’t common elsewhere in the codebase thus making this contribution somewhat different in approach.

Changes were made in another file which handled adding the assets within the boundaries of the selection to an array for later use. This addition features the method call defined in the previous figure as well as another type guard and (attempted) deep copy.


<INSERT SCREENSHOT PersonalContribution2v2>

The two files should therefore be viewed in tandem as the approach of one informs the approach of the other. Since my approach within the above figure is one of minimal adjustments, the bulk of the logic and data manipulation is therefore contained within the other file (Fig-11). While this seemed preferable in order to maintain a separation of concern and maintain readability within the main file (Fig-12), it resulted in a less performant version of code and a particularly messy module for obtaining the adjusted coordinates.


CONCLUSION

Overall the programming practices seen within the repository show a high standard of knowledge and understanding within the subject. Comparison with my own contributions highlights the knowledge and experience divide between myself and the other developers, particularly after comparing with the reworked version of my contribution. Such comparison provided a valuable learning experience for myself particularly with relation to deep copies of nested data structures.

<INSERT SCREENSHOT PersonalContributionFINAL0>

The above figure shows a better alternative to spreading in a data structure when attempting to make a deep copy. While I worked under the assumption that spreading would work to deep copy nested values, this was revealed not to be the case, thus leading to undesired modifying in place of nested values. Converting to and from JSON format, on the other hand circumvents this to provide a true deep copy.

My approach also featured a for loop which was later replaced more elegantly with a for each method call.  After comparing the two approaches, I learned much regarding best practices for readability and performance - with the for each method proving the better choice on both accounts.

<INSERT SCREENSHOT PersonalContributionFINAL1>

Furthermore, my inclusion of a type guard was itself a learning experience as it was not something I had seen previously yet proved valuable in use as well as providing information regarding how custom types are handled in that they do not exist until compile time.

Overall, working on this particular contribution and subsequent comparisons with the reworked version and other code seen within the repository has been a valuable learning experience. This will serve as a stepping stone for future learning and assist in developing the decision making skills necessary to develop cleaner, performant code in line with best practices and established style within this codebase.
