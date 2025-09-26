The Campus Course & Records Manager (CCRM) is a console-based Java SE application designed to manage student records, courses, enrollment, and grades for an educational institute. It is structured with clear packages and demonstrates core Object-Oriented Programming (OOP) principles, robust exception handling, modern I/O with NIO.2, Streams, the Date/Time API, and design patterns (Singleton & Builder).

 Evolution of Java (Short Timeline Bullets)
1995 (JDK 1.0 - Oak): Initial public release, establishing the "Write Once, Run Anywhere" (WORA) principle.
1998 (J2SE 1.2 - Playground): Introduced the Collections Framework and the three distinct editions (SE, EE, ME).
2004 (J2SE 5.0 - Tiger): Major update introducing Generics, the Enhanced for loop, Enums, and Autoboxing.
2014 (Java SE 8 - Lambda): Revolutionized Java with Lambda Expressions , the 
Stream API , and the 
Date/Time API (JSR-310).
2017 (Java SE 9 - Jigsaw): Introduced the Java Platform Module System (JPMS).
2021 (Java SE 17): Latest Long-Term Support (LTS) release, focusing on stability and modern language features.




 3 Java ME vs Java SE vs Java EE Comparison
Feature	Java ME (Micro Edition)	Java SE (Standard Edition)	Java EE (Enterprise Edition)
Target Platform	
Embedded devices, IoT, feature phones.


Desktop/Console Applications, Applets.

Large-scale, multi-tier, server-side enterprise systems.


Typical Use	Resource-constrained environments.		
This CCRM Project, general desktop tools.

Web services, Servlets, EJB, large-scale database interaction.
Key APIs	Small footprint libraries.		
Core APIs, Streams, NIO.2.

Jakarta EE specifications (JPA, Servlets, RESTful services).

JDK, JRE, and JVM Explanation
The Java architecture is built on these three components:





JVM (Java Virtual Machine): The abstract machine that executes Java bytecode (.class files). It is responsible for the WORA principle by interpreting bytecode into the native machine instructions of the host operating system.

JRE (Java Runtime Environment): The environment required to run a compiled Java program. It includes the JVM and the Java core class libraries (all the standard APIs).

JDK (Java Development Kit): The complete toolset for developing and compiling Java programs. It includes the JRE plus development tools like the compiler (javac) and the debugger (jdb). The JDK is mandatory for building the CCRM application.


5. Setup & Configuration Steps
(Insert your own screenshots for these steps)

A. Windows JDK Install & Configuration
Download and Install: Download the Java SE JDK installer (e.g., from Oracle or Adoptium).

Verify Installation: Open a command-line interface and execute java -version.


Screenshot: JDK installation verification (java -version) output here. 


Configure PATH: Ensure the path to the JDK's bin directory is correctly added to the system's PATH environment variable.

B. Eclipse IDE Setup
New Project Creation: Use the Eclipse IDE for Java Developers to create a new Java Project. Set the JRE to the installed JDK 17+.


Screenshot: Eclipse project setup & run screenshot here. 

Run Configuration for Assertions: To ensure assertions work, configure the run arguments:

Go to Run > Run Configurations....

Select your CCRMApplication launch configuration.

Navigate to the 

Arguments tab and add -ea to the VM Arguments box.






6. Notes on Enabling Assertions and Sample Commands
Enabling Assertions
The CCRM project uses 

assertions (e.g., assert courseCode != null : "...")  to check invariants—conditions that should 

always be true—like ensuring object IDs are not null or credit totals are within bounds. Assertions are disabled by default.

To enable them, the JVM must be launched with the -ea flag


Syllabus Topic → Implementation Mapping Table
This table maps mandatory technical requirements to the specific class or method where the feature is demonstrated.


Syllabus Topic	File/Class/Package	Method/Concept Demonstrated
Encapsulation 

Person.java, Student.java	Private fields (id, regNo) with public getter methods.
Inheritance 


Student.java, Instructor.java	Both extend the abstract base class Person. Uses super() in constructors.
Abstraction 

Person.java	Defined as abstract class with abstract String getRole() method.
Polymorphism 

Student.java, Transcript.java	Overriding toString()/getDetails(); using Person reference to Student object.
Singleton Pattern 

AppConfig.java (edu.ccrm.config)	Private constructor and a static getInstance() method (thread-safe).
Builder Pattern 

CourseBuilder.java (edu.ccrm.config)	Inner static class for step-by-step construction of Course objects.
Enums with fields 

Grade.java, Semester.java (edu.ccrm.domain)	Grade has a constructor and gradePoint field (e.g., S(10.0)).
Custom Unchecked Exception 


MaxCreditLimitExceededException.java	Extends RuntimeException. Thrown in EnrollmentService.
Assertions 

Student.enroll()	Checks for non-null course code (assert courseCode != null).
Date/Time API 

Student.java, BackupService.java	Uses LocalDate for enrollmentDate; LocalDateTime for backup timestamps.
Streams API (Aggregation) 

TranscriptService.computeGpa()	Uses .stream().mapToDouble().average() to calculate GPA.
Functional Interfaces/Lambdas 

StudentService.filterStudents()	Uses Predicate<Student> with a lambda for filtering students.
Recursion Utility 

RecurseUtility.java (edu.ccrm.util)	Method to calculate and print the total size of the backup directory recursively.
NIO.2 (File Ops) 

BackupService.java (edu.ccrm.io)	Uses Path, Files.copy(), and Files.walk() for backup functionality.
Immutability 

CourseCode.java (edu.ccrm.domain)	Value class with all final fields.
Interface with Default 

Persistable.java (edu.ccrm.io)	Defines methods like toCSV() and uses a default method for pa