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

_just about to start 'Learning COBOL' on page 48_