# CH 01 Introduction

[toc]

## Introduces

The NIST Computer Security Handbook defines the term computer security as:

>“The protection afforded to an automated information system in order to attain the applicable objectives of preserving the integrity, availability and confidentiality of information system resources” (includes hardware, software, firmware, information/ data, and telecommunications)

## Computer Security Objectives

### Confidentiality(기밀성)

- Data confidentiality 

  Assures that private or confidential information is not made available or disclosed to unauthorized individuals

- Privacy

  Assures that individuals control or influence what information related to them may be collected and stored and by whom and to whom that information may be disclosed

### Integrity(무결성)

- Data integrity 

  Assures that information and programs are changed only in a specified and authorized manner

- System integrity

  Assures that a system performs its intended function in an unimpaired manner, free from deliberate or inadvertent unauthorized manipulation of the system

### Availability(가용성)

- Assures that systems work promptly and service is not denied to authorized users

### Essential Network and Computer Security Requirements

- CIA : Confidentiality、Integrity、Availability
- AA ：Accountability、Authenticity

![](Resources\07.jpg)

## Computer Security Challenges

- Security is not simple
- Potential attacks on the security features need to be considered 
- Procedures used to provide particular services are often counter-intuitive
- It is necessary to decide where to use the various security mechanisms
- Requires constant monitoring 
- Is too often an afterthought 
- Security mechanisms typically involve more than a particular algorithm or protocol 
- Security is essentially a battle of wits between a perpetrator and the designer 
- Little benefit from security investment is perceived until a security failure occurs 
- Strong security is often viewed as an impediment to efficient and user-friendly operation

## OSI Security Architecture

- Security attack

  Any action that compromises the security of information owned by an organization

- Security mechanism

  A process (or a device incorporating such a process) that is designed to detect, prevent, or recover from a security attack

- Security service

  A processing or communication service that enhances the security of the data processing systems and the information transfers of an organization

  Intended to counter security attacks, and they make use of one or more security mechanisms to provide the service

### Threats and Attacks (RFC 4949)

![](Resources\08.jpg)

### Security Attacks

- A means of classifying security attacks, used both in X.800 and RFC 4949, is in terms of **passive attacks** and **active attacks**

- A `passive attack` attempts to learn or make use of information from the system but does not affect system resources

- An `active attack` attempts to alter system resources or affect their operation

![](Resources\10.jpg)

#### Passive Attacks

- **A passive attack attempts to learn or make use of information from the system but does not affect system resources**

  ![](Resources\09.jpg)

- Are in the nature of eavesdropping on, or monitoring of, transmissions

- Goal of the opponent is to obtain information that is being transmitted

- Two types of passive attacks are:
  - **The release of message contents**
  - **Traffic analysis**

#### Active Attacks

- **An active attack attempts to alter system resources or affect their operation**

  ![](Resources\10.jpg)

- Involve some modification of the data stream or the creation of a false stream
- Difficult to prevent because of the wide variety of potential physical, software, and network vulnerabilities

- Goal is to detect attacks and to recover from any disruption or delays caused by them

- Four types of active attacks are：
  - **Masquerade**：
    - Takes place when one entity pretends to be a different entity
    - Usually includes one of the other forms of active attack
  - **Replay**:
    - Involves the passive capture of a data unit and its subsequent retransmission to produce an unauthorized effect
  - **Modification of messages**:
    - Some portion of a legitimate message is altered, or messages are delayed or reordered to produce an unauthorized effect
  - **Denial of service**:
    - Prevents or inhibits the normal use or management of communications facilities

## Security Services

### Data Confidentiality

![](Resources\11.jpg)

### Data Integrity

![](Resources\12.jpg)

### Availability

![](Resources\13.jpg)

### Authentication

![](Resources\14.jpg)

### Nonrepudiation

![](Resources\15.jpg)

### Access Control

![](Resources\16.jpg)

## Fundamental Security Design Principles

- Economy of mechanism 

  ![](Resources\17.jpg)

- Fail-safe defaults 

  ![](Resources\18.jpg)

- Complete meditation 

  ![](Resources\19.jpg)

- Open design 

  ![](Resources\20.jpg)

- Separation of privilege 

  ![](Resources\21.jpg)

- Least privilege 

  ![](Resources\22.jpg)

- Least common mechanism 

  ![](Resources\23.jpg)

- Psychological acceptability 

  ![](Resources\24.jpg)

- Isolation 

  ![](Resources\25.jpg)

- Encapsulation 

  ![](Resources\26.jpg)

- Modularity 

  ![](Resources\27.jpg)

- Layering 

  ![](Resources\28.jpg)

- Least astonishment

  ![](Resources\29.jpg)

## Attack Surfaces

An attack surface consists of the reachable and exploitable vulnerabilities in a system

Example:

- Open ports on outward facing Web and other servers, and code listening on those ports 
- Services available on the inside of a firewall 
- Code that processes incoming data, email, XML, office documents, and industry-specific custom data exchange formats 
- Interfaces, SQL, and Web forms 
- An employee with access to sensitive information vulnerable to a social engineering attack

## Attack Surface Categories

- Network attack surface 

  Refers to vulnerabilities over an enterprise network, wide-area network, or the Internet

- Software attack surface 

  Refers to vulnerabilities in application, utility, or operating system code

- Human attack surface 

  Refers to vulnerabilities created by personnel or outsiders

## Attack Tree

- A branching, hierarchical data structure that represents a set of potential techniques for exploiting security vulnerabilities 
- The security incident that is the goal of the attack is represented as the root node of the tree, and the ways that an attacker could reach that goal are represented as branches and sub-nodes of the tree 
- The final nodes on the paths outward from the root, (leaf nodes), represent different ways to initiate an attack 
- The motivation for the use of attack trees is to effectively exploit the information available on attack patterns

![](Resources\30.jpg)

## Model for Network Security

![](Resources\31.jpg)

## Standards

- National Institute of Standards and Technology
  - NIST is a U.S. federal agency that deals with measurement science, standards, and technology related to U.S. government use and to the promotion of U.S. private-sector innovation 
  - Despite its national scope, NIST Federal Information Processing Standards (FIPS) and Special Publications (SP) have a worldwide impact
- Internet Society
  - ISOC is a professional membership society with world-wide organizational and individual membership 
  - Provides leadership in addressing issues that confront the future of the Internet and is the organization home for the groups responsible for Internet infrastructure standards

- ITU-T
  - The International Telecommunication Union (ITU) is an international organization within the United Nations System in which governments and the private sector coordinate global telecom networks and services 
  - The ITU Telecommunication Standardization Sector (ITU-T) is one of the three sectors of the ITU and whose mission is the development of technical standards covering all fields of telecommunications
- ISO
  - The International Organization for Standardization is a world-wide federation of national standards bodies from more than 140 countries
  - ISO is a nongovernmental organization that promotes the development of standardization and related activities with a view to facilitating the international exchange of goods and services and to developing cooperation in the spheres of intellectual, scientific, technological, and economic activity

