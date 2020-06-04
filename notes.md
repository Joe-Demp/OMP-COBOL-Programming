# Advantages of COBOL
* Handles vast amounts of critical data stored in the largest servers e.g. the IBM Z Mainframe

# How is it used?
* 95% of ATM swipes
* 80% of in person transactions
* $3 trillion in commerce

* 200 times more COBOL transactions executed per day than Google searches
* 220 billion lines of COBOL running today - 80% of the world's actively used code
* 1.5 billion lines of new COBOL code written each year

# Why should I care?
* How the business works is found in the code
* over 50 years of refinement as a language
* COBOL is there, a lot of it works, and works very well


# VSCode with Zowe Explorer
Zowe Explorer - and open-source extension for VSCode that lets developers and sysadmins interact with z/OS mainframes using VSCode.

## Introduction
* Modern approach to z/OS mainframe development
  * Create, modify, rename, copy and upload data to a z/OS
  * do the same with USS files
  * streamlined process to access data sets, USS files and jobs
  * Create and use Zowe CLI `zosmf` compatible profiles

## Profiles in Zowe Explorer
* The URL for the API services to connect to and credentials
* main profile info needed: z/OSMF Connection

### Secure Credentials
* Possible to secure credentials using the plugin

_Further sections ommitted - just instructions for working with Zowe_

# VSCode with Z Open Editor

## Introduction

### What is it?
* fee extension to VSC
* Support for COBOL, PL/I and JCL languages
  * PL/I - Programming Language 1, a procedural, imperative computer programming language
  * JCL - Job Control Language, scripting languages used on the IBM mainframe OSs
* Also content assistance for apps that call CICS, MQ, IMS and DB2 APIs
* Code can reside in a source code repo, locally in file or on z/OS

### Role of the Language Server Protocol
* LSP - a common description of how features of the code editor should be implemented for spoecific languages
* Languages with an LSP server can be used inside any code editor

## Basic Editing

### Known File Extensions
* possible options: .COBOL .CBL .COB .COBCOPY .COPYBOOK .COPY
* Applied to both local files and files held in a Partitioned Data Set (PDS), like a folder on the mainframe

### Margins
* 5 columns: sequence numbers, comment / continuation characters, area A and area B

_much ommitted from this section_


# VSCode with Code4z Extension
* includes a debugger for COBOL programs running on a CICS (Customer Information Control System) region
* also tools to enable developers to access mainframe data sets and CA Endevor code repos (like git)

## Copybook Support
* Copybook - pieces of code stored in seperate data sets, referenced in a program
* Set up and configure a ZOWE CLI `zosmf` profile to be able to download all copybooks referenced in a program from the mainframe to a local directory

# Zowe CLI and Plugins
* An open source CLI for the mainframe
* Provides: Remote interaction with z/OS data sets and jobs, Unix System Services files, TSO [Time Sharing Option, allows user sessions] and Console commands, and provisioning services.
* A bridge tool between distributed systems and the mainframe (e.g. allows multiple languages to run on the mainframe)
* Help automate the build deployment and testing for COBOL

* command structure: `zowe <group> <action> <object>`, followed by parameters and command options
  * e.g. `zowe files list data-set "HLQ.*"  
  Lists data-sets matching a pattern of "HLQ.*"
* append `-h`, `--help-web` or `--hw` to any command to find out more

### Profiles
* Where connection information is stored

# Basic COBOL

* "Enterprise COBOL" - the name for the COBOL programming language compiled an dexecuted on IBM Z Operating Systems, z/OS
* Native support for JSON, XML and Java

## What must a novice COBOL programmer know to be an experienced COBOL programmer?

### What are the coding rules and the reference format?

* source code is column dependent (5 columns)
* **Sequence Number Area** - (1 to 6) - blank or reserved for line sequence numbers
* **Indicator Area** - (7) -
  * Comment line (usually with '*')
  * Continuation line (usually '-')
  * Debugging line ('D' or 'd')
  * Source listing formatting ('/')
* **Area A** - (8 to 11) -
  * Level indicators
  * Declarative items
  * Division, Section or Paragraph headers
  * Paragraph names
* **Area B** - (12 to 72) -
  * Entries, sentences, statements and clauses
  * Continuation lines
* **Identification Area** - (73 to 80) -
  * Ignored by the compiler
  * Can be used by the programmer for any purpose

### What is the structure of COBOL?
* COBOL is a hierarchy structure consisting and in the top-down order of:
  * Divisions
  * Sections
  * Paragraphs
  * Sentences
  * Statements

### What are COBOL reserved words?
*  PERFORM, MOVE, COMPUTE, IF, THEN, ELSE, EVALUATE, PICTURE, etc..
* https://www.ibm.com/support/knowledgecenter/zh/SSZJPZ_9.1.0/com.ibm.swg.im.iis.ds.mfjob.dev.doc/topics/r_dmnjbref_COBOL_Reserved_Words.html

### What is a COBOL statement?
* Also called *verbs*
* Control flow, I/O, data manipulation, report writer
* Statements exist only within the Procedure Division - The program processing logic

### What is the meaning of a scope terminator?
* Explicit - marks the end of certain Procedure Division statements with "END-" COBOL reserved word
* For COBOL verbs that are always conditional (IF, EVALUATE) or that have a conditional clause (COMPUTE, PERFORM, READ) e.g. "END-PERFORM", "END-READ"
* Implicit - '.' character, ends the scope of all previous statements that have not been ended

### What is a COBOL sentence?
* one or more “Statements” followed by a period (.), scope terminator

### What is a COBOL paragraph?
* A user-defined or predefined name followed by a period
* Consists of zero or more sentences
* the subdivision of a “Section” or “Division”

### What is a COBOL section?
* A user-defined or a predefined name followed by a period
* consists of zero or more sentences
* a collection of paragraphs

e.g.

*-------------------------
 PROCEDURE DIVISION                 # Division / Section
*-------------------------
 OPEN-FILES.                        # Paragraph
     OPEN INPUT  ACCT-REC.          # Sentence
     OPEN OUTPUT PRINT-LINE.        # Sentence


## COBOL Divisions

* Divisions are subdivided into Sections
* Sections are subdivided into Paragraphs
* Paragraphs are subdivided into Sentences
* Sentences consist of Statements
* Statements begin with COBOL reserved words and can be subdivided into "Phrases"

###  What are the four Divisions of COBOL?

#### IDENTIFICATION DIVISION
* Identifies the program with a name
* Optionally gives other idenntifying information
* Author name, program compiled date, etc.

#### ENVIRONMENT DIVISION
* Describes the aspects of the program that depend on the computing environment
* Computer configuration, inputs and outputs

#### DATA DIVISION
* Where data characteristics are defined in one of the following
  * **FILE SECTION** Defines data used in Input-Output operations
  * **LINKAGE SECTION** Describes data from another program. When defining data developed for internal processing.
  * **WORKING-STORAGE SECTION** Storage allocated and remaining for the life of the program.
  * **LOCAL-STORAGE SECTION** Storage allocated each time a program is called and de-allocated when the program ends

#### PROCEDURE DIVISION
* Instructions related to manipulation of data
* Sub-routines etc.

## The PROCEDURE division explained
* Statements in the prcedure division -> actions to be taken by the program
* **Section** - logical subdivision of processing logic
  * header + 1 or more paragraphs.
  * Can be the subject of a `PERFORM` statement
  * e.g. section for declaratives, a set of one or more special purpose instructions
  * e.g. description of inputs and outputs
  * At the beginning of the procedure division, `DECLARATIVES` and `END DECLARATIVES`
* **Paragraph** - subdivision of a section, procedure or program, can be the subject of a statement
* **Sentence** - a series of one or more COBOL statements ending with a period
* **Statement** - an action to be taken by the program e.g. adding 2 numbers
* **Phrase** - a small part of a statement (like an adjective or preposition in English)

## Lab - Zowe Explorer VSCode, Zowe CLI
* Note, I changed my password using Zih in Slack and managed to connect to the server
* Saving work in .\Mainframe Files\...

### Zowe CLI Commands
* `zowe profiles set zosmf COBOL-Tutorial`
* `zowe zosmf check status`
* `zowe files list ds "Z81547.*` - list files in the dataset of the given pattern
* `zowe files list am "Z81547.CBL"` - list all members of the given dataset
* `zowe files download am "Z81547.CBL" -e ".cbl"` - download members of the given dataset. -e = --extension, save the local files with the specified file extension
* `zowe jobs submit ds "Z81547.JCL(HELLO)" --vasc` - submit a job (as JCL) contained in a dataset (Z81547.JCL), wait for the job to complete and print all output from the job (--vasc, --view-all-spool-content)
* `zowe jobs submit ds "Z81547.JCL(HELLO)" --wfo` - submit job and wait for OUTPUT status before completing the command
* `zowe jobs list sfbj JOB08291` - Given a z/OS job JOBID, list the spool files (DDs) for a z/OS job on the JES/spool queues.
* `zowe jobs view sfbi JOB08291 105` - View the contents of a spool file from a z/OS job, given a jobid and fileid
* `zowe jobs submit ds "Z81547.JCL(HELLO)" -d` - Do the job and download the spool content

### Zowe CLI - Programatic Usage
* Automate submitting the JCL to compile, link and run the COBOL program and downloading the spool output
* done - see '.\zowe-cli-automation\package.json'

# Data division

# Variables / Data-items

* Variable or Data-item, a name chosen by the COBOL programmer.
* The variable name also known as the data-name
* Restrictions:
  * Must not be a COBOL reserved word
  * Must not contain a space
  * Contains letters (A-Z), digits(0-9), underscores and hyphens
  * Maximum length of 30 characters
  * hyphen can't be the first or last character
  * underscore can't be the first character

* When COBOL is compiled, the compiler expects a named COBOL variable to possess attributes length and data type.
* A variable, at runtime, represents a defined area of processing memory where the memory location has a maximum length and designated data type.

* Common COBOL data types:
  * Numeric (0-9)
  * Alphabetic (A-Z), (a-z), or a space
  * Alphanumeric Numeric and Alphabetic Combination

## PICTURE Clause

* COBOL reserved word `PICTURE` , determines the length and data type of a programmer selected variable name.
* Data types described by `PIC`, commonly referred to as `PIC` clauses.
* e.g.
  * `PIC 9` - single numeric value where length is one
  * `PIC 9(4)` - four numeric values where length is four
  * `PIC X` - single alphanumeric (character) value where length is one 
  * `PIC X(4)` - four alphanumeric values where length is four

### PIC clause symbols and data types

* max length determined by data type and compiler options
* Alphabetic only data type described by `PIC A`.

Other symbols:
```
B E G N P S U V Z 0 / + - , . * CR DB cs
```
where `cs` is any valid currency symbol e.g. $

* All described here: https://www.ibm.com/support/knowledgecenter/SS6SG3_4.2.0/com.ibm.entcobol.doc_4.2/PGandLR/igy3lr50.pdf

### Coding COBOL variable / data-item names

* Done in the DATA DIVISION
* Code describing a variable name is accomplished using a level number and a picture clause
* **Level Number** - A hierarchy of fields in a record
* **Variable name / Data-item name** - Assigns a name to each field to be referenced in the program and must be unique within the program
* **Picture Clause** - For data type checking

### PICTURE clause character-string representation

* e.g.
  * `PIC 9(4)V99` - a clause to hold value `1123.45`. `V` represents the decimal position
  * `PIC $9,999V99` - a clause to hold a value like `$1,123.45`.

## Literals
* A constant data value
* e.g. `DISPLAY "HELLO WORLD!"` is a COBOL reserved word followed by a literal

### Figurative constants
* Reserved words that name and refer to specific constant values
* e.g.
  * ZERO, ZEROS, ZEROES
  * SPACE, SPACES
  * HIGH-VALUE, HIGH-VALUES
  * LOW-VALUE, LOW-VALUES
  * QUOTE, QUOTES
  * NULL, NULLS

### Data relationships
* Defined in the `DATA DIVISION` - level indicators and level-numbers
* **Level indicators** - include a descriptive entry; identifies each file in a program
* **Level-numbers** - also include a descriptive entry; inidcates the properties of specific data; can be used to describe the data hierarchy

### Level numbers

* The structured level number hierarchic relationship is available to all `DATA DIVISION` sections.
* Programmer chosen numbers

### Levels of data

* Records can be subdivided to provide more detailed data references
* Level number: a one or two digit number between 01 and 49 or one of : 66, 77, 88
* Relationship between level numbers in a group item defines the hierarchy of data within that group.
* Group items include all group and elementary items that follow it, until a level number less than or equal to the level number of the group is encountered

## MOVE and COMPUTE

* Reserved words that alter the value of variable names.
e.g.
```COBOL
 IDENTIFICATION DIVISION
 PROGRAM-ID PAYROL00
 DATA DIVISION
 WORKING STORAGE SECTION
****** Variables for the report
 77  WHO         PIC X(15)
 77  RATE        PIC 9(3)
 77  HOURS       PIC 9(3)
 77  GROSS-PAY   PIC 9(5)

 PROCEDURE DIVISION
****** COBOL MOVE statements - Literal Text to Variables
     MOVE "Captain COBOL" TO WHO
     MOVE 19 TO HOURS
     MOVE 23 TO RATE
****** Calculation using COMPUTE
     COMPUTE GROSS-PAY = HOURS * RATE
****** DISPLAY statements
     DISPLAY "Name: " WHO

****** etc. etc.
```

## Lab

* Dealt with a new program (PAYROL00) and dealt with compile errors

*Pick up with chapter 10 - File Handling*
