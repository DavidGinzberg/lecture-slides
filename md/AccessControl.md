#Java Access Control

 
-
## Topics

- What are access modifiers
- What access types are possible
- how do they differ
- what are packages
- how are packages defined


-
-
# Access modifiers

Java keywords which change how broadly classes and their member variables and methods can be accessed.

-
## Four access types
- Package
- Public
- Protected
- Private

-
## Private

- Only accessible in the same class
- Strictest access type
- Modifier: `private` keyword


-
## Package

- Accessible to other members of the same package
- Default if no access modifier specified
- No modifier (The `package` keyword does something else)

-
## Protected

- Accessible to other members of the same package
- Accessible to subclasses regardless of their package
- Modifier: `protected` keyword

-
## Public

- Accessible anywhere
- Provides api-level access
- Modifier: `public` keyword

-
### Public classes

- one per compilation unit (file)
- Must match file name

-
### What can receive access modifiers?

- Fields (static and instance variables)
- Methods
- Classes* and nested classes


-
## Keep fields and functions as private as is sensible

- Often instance variables should be private with accessor and mutator methods (getters and setters) if necessary
- Implementation details shouldn't matter to API users


-
## Exercise: Getters and Setters

- Create a Point class, to store the `x`, `y`, and `z` coordinates of a point in space
- The x, y, and z coordinates should be private.
- Provide getters and setters for x, y, and z.
- Create an ImmutablePoint class whose instances cannot be changed once they have been initialized

-
-
# Packages

-
## Package Statement

- Specifies the package classes belong to
- Must be first line in a file (except comments and empty lines)
- Applies to the entire file

example:
`package io.zipcoder.unitcorn.tests;`

-
## Package name implies directory structure

- Java interpreter will look for classes in directories that match their package
- Normally will not run if these don't match (IntelliJ Circumvents this - do not rely on that)



-
## Default package behavior
- Unique to each directory
- Default package members have access to other members in the same directory
- No access to members of explicitly defined package-member classes in same directory

-
-
## A bit about APIs

-
## API Means:

- Application Programming Interface
- The set of functions and data members available to client code using your library
- Often also used to refer to the documentation of a particular API

-
## Public access is API access

- Any public members are accessible to client code
- Any changes to public members could break client code
- Changes should not impact the API unless absolutely necessary

