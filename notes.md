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

*Pick up on pg 52: PROCEDURE DIVISION explained*
