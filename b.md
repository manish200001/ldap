

**Table of Contents**

[Overview](#overview)

[Ldap](#ldap)

[Podman](#podman)

[Apache Directory Studio](#apache-directory-studio)

[Setup Server on Podman](#setup-server-on-podman)

[Install podman](#install-podman)

[Install ldap-utils](#install-ldap-utils)

[Step 1](#step-1)

[Step 2](#step-2)

[Step 3](#step-3)


# Overview

Lightweight directory access protocol (LDAP) is a protocol that helps users find data about organisations, persons, and more. LDAP has two main goals: to store data in the LDAP directory and authenticate users to access the directory. It also provides the communication language that applications require to send and receive information from directory services. A directory service provides access to _where_ information on organisations, individuals, and other data is located within a network.

The most common LDAP use case is providing a central location for accessing and managing directory services. LDAP enables organisations to store, manage, and secure information about the organisation, its users, and assets–like usernames and passwords.


# Ldap

LDAP stands for Lightweight Directory Access Protocol. It is a standardised protocol used for accessing and managing directory information services over a network. 

**Key Points**

**Lightweight**

- The term "Lightweight" here is used to indicate that LDAP (Lightweight Directory Access Protocol) is a simple and easy-to-use protocol. Its primary purpose is to implement complex directory services, yet it uses so few resources that it is termed "lightweight." The idea is that this protocol consumes less network bandwidth and computational resources, making it efficient and speedy.


**Directory**

- "Directory" represents a centralized database or information storehouse where details of items such as users, devices, and resources are stored. LDAP is used for directory services, organising information in a tree structure. Directory services facilitate easy retrieval and updating of specific information.


**Access**

- "Access" here refers to the means of reaching and interacting with data or information. LDAP is used for accessing and making changes to directory information. Through LDAP, clients (such as applications or users) can connect to the directory server, retrieve information, and, if authorized, make changes to the information.


**Protocol**

- "Protocol" is a set of rules that regulate communication between devices or systems. LDAP is a network protocol designed for accessing directory information. Through this protocol, clients and servers communicate with each other, sending queries and updating information.




**Openldap**

OpenLDAP is an open-source implementation of the Lightweight Directory Access Protocol (LDAP). LDAP is a standard protocol used for accessing and managing directory information services, and OpenLDAP provides a free, open-source implementation of this protocol. OpenLDAP is widely used for creating and managing directory services, particularly for user authentication and authorization in network environments.


# Podman

Podman is an open-source container management tool that allows users to manage containers without the need for a container daemon. It is designed to be a lightweight, daemonless alternative to Docker. Podman provides a command-line interface (CLI) for managing containers, pods, and container images.

**key points**

**Daemonless Architecture** Unlike Docker, Podman operates in a daemonless mode, which means it does not require a central daemon process to manage containers. Each Podman command runs in its own container, providing a more secure and resource-efficient approach.

**Compatibility with Docker** Podman is compatible with Docker, which means it can run containers and images created for Docker. This compatibility makes it easy for users familiar with Docker to transition to Podman.

**Rootless Containers** Podman supports running containers without the need for root privileges. This enhances security by reducing the attack surface and minimizing the potential impact of container vulnerabilities.

**Pod Support** Podman introduces the concept of pods, which are groups of containers that share the same network and storage namespaces. Pods provide a way to manage multiple containers as a single unit, similar to Kubernetes pods.


# Apache Directory Studio

Apache Directory Studio is an open-source, cross-platform LDAP (Lightweight Directory Access Protocol) client and development toolset that is part of the Apache Directory project. It provides a set of tools and plugins to work with LDAP directories, making it easier for developers and administrators to interact with and manage LDAP servers.


# Setup Server on Podman

Prerequisites for setup

- Podman
- Ldap-utils
- Apache directory studio


# Install podman

**To install podman**
```
sudo apt install podman
```
![](https://lh7-us.googleusercontent.com/A7ccl40CeeP95B0bTnrfpDlW5Kz60y-og2AysiFN4lTSYuH33jXW43HF8kflQt8KC_mWLXq9aQ6kyf27gYZwLa8YiytxOH1hWMeQleh8do-7eVSzh6YP42_IxlUnW1e0g-NrBg1M_adTY4sybHbcgk0)

**To check podman**
```
which podman
```
![](https://lh7-us.googleusercontent.com/R_Bs8dn01b7wB2trNM2eP2AvZhqhkK8wbagD2fq4jSIaoXvxyEJxAlisWC8ooptcz7aEBJ-mLWJVNvIfRzgoL3oNb9JR_C6kMsMZPcZ-Z4vnZNnLjeAywwym-VH5I1fczkRJfOEWqPaKECjrRnVizcc)


# Install ldap-utils:-

**To install ldap-utils**
```
sudo apt install ldap-utils
```

![](https://lh7-us.googleusercontent.com/dwbeBtlWirTV6XqGzIfqgu4xhCWa6atAS9UZEK7B3SahX3boF5-_ckE7EmrAPx1TSpq-deRPtlC8Qbtq-Q0oxt6xYS6VHDEOr4C6aMrXIB2pyPZaGCdG9nU0u8j7uMvYeOF0CGkfjhXME29C0UFCP-Y)


# Step 1

**Create openldap server in podman**

**To check current directory**
``````
pwd
``````

![](https://lh7-us.googleusercontent.com/ayq-BaNyVutRllh6qpeSWqm2LWYmOimNGIv8PTZ729aUZ_vlkJg4oFbpZzHaD_wICb1wiL5r1dW17aGZK20oUbMS5Aa1dnonDEOSibez98GWUL0Inu2UjPvJe24hedxlF5oMTlJsWeeis_DM8bq31FI)

**To create container for server**
``````
podman run -dt --name openldap-container -p 3389:3389 -v /home/manish/ldap/qqq/git:/data -e DS\_SUFFIX=dc=finoptaplus,dc=com -e DS\_DM\_PASSWORD=1 quay.io/389ds/dirsrv
``````

![](https://lh7-us.googleusercontent.com/tXgKG6P8J5PAJu6hNpSO9huhsyOfHeFVIsodKwl-Chbhxge89IsWyxmBoDEYy09GQcGZ7P7cVAWLKYW6gOmJbiioS8GkPCRbYJwl0xC8EtOVreuqmN8E3VuqvS0P34hAI6yiujf_AC9Kt7Xyj8ke-iM)

**To enter container**

```
podman exec -it openldap-container /bin/bash
```
![](https://lh7-us.googleusercontent.com/J9BQxpiHmQV2zqZv9euhWSlI5Xg-Vhy7hU4eQPw0RvWGFRfuGEQRGqIMIsbYW6zpetUG-eGiXGKBWPlwsaRYXzoa_qTlf-cHHADI7tcDHTvs85YJUOVmn13Bc7dB9YXHiXOt5O8ZHcvOvXF7Qize72A)

**Your password is 1**

**To check environment in the container**
``````
dsconf -D "cn=Directory Manager" ldap\://localhost:3389 backend suffix list
``````
![](https://lh7-us.googleusercontent.com/3g5t5HxG4I7q6judEPg0siT_GqvHBwKWZogHQtZDtAHZ08Q6r31AbW0KejbXnCi9qHD6c8p13GXcYoMzR2T_vX57LDZ09QF94dVFYIB03XXFqC9Nh3LqgZs9KNKbd4a2yG7wrgPgMkjQta1r74clAeY)

**If no backend found**

**To set environment in the container**
``````
dsconf -D "cn=Directory Manager" ldap\://localhost:3389 backend create --suffix "dc=finoptaplus,dc=com" --be-name "finoptaplus"
``````

![](https://lh7-us.googleusercontent.com/74gKjV8vGP8HbkLB0IH1jEZ_U6dgI2qk1gss-hM7WyyxMAV0ltCu5h_Z1WezwawVKlo2iB-A99H_32hKfT2Q0noN1CBMhy6Eqg-SJ3OBu3AD3R7Z4o9Lt_h4Ta4gZqafSRfP7pMP7YnG_l_FVk8cHE8)

**To exit from container**
``````
exit
``````
![](https://lh7-us.googleusercontent.com/lDn6k6ofKte7pkD2ygQL78T77P7bQjPmfLldcFiSq44n5CjFou3GEsi-YzQTZmWymzTgvLGwLMGCv2Y1Xh8bF7HBooKAaRXUrIjPDvEAtComhx676mhExkMCLe4gz9h8b4zdc4PO6-ymP488nZ4VKoQ)


# Step 2

**Note**

When you add a file, If you saw any error like object not found its not an error because all the files depend on each other.

**Add ldif files** 

**To create 1\_Add\_Directory.ldif**
``````
vim 1\_Add\_Directory.ldif
``````
![](https://lh7-us.googleusercontent.com/4ArPiRvLfsjWrb-mXNpBndbaTQmh3QE3wwG_t3XAURo7SAfyFYW0XuCr7aK4DSeouzzjCmHHnBLPXk71JCiOao_Ubxk3lZe3M_CHXFTo1n8zbvnfHgnfxwlsvioWaPmiIBuXHvvU7XCV8rsuq5hlbeQ)

``````
version: 1
dn: cn=schema
changetype: modify
add: objectclasses
objectclasses: ( admin-oid NAME 'admin' SUP top STRUCTURAL MUST (email $ userName $ primaryMobile  $ firstName $ lastName $ address $ userPassword $ userStatus  ) MAY ( ) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: dc=admin,cn=schema
objectClass: organizationalUnit
objectClass: top
objectClass: domain
ou: admin
description: admin

dn: email=admin1\@fino.com,dc=admin,cn=schema

changetype: add

objectClass: top

objectClass: admin

email: admin1\@fino.com

userName: admin1

primaryMobile: 1212121212

firstName: admin1

lastName: fino

address: fino

userPassword: Redhat\@1

userStatus: Active

dn: email=admin2\@fino.com,dc=admin,cn=schema

changetype: add

objectClass: top

objectClass: admin

email: admin2\@fino.com

userName: admin2

primaryMobile: 2121212121

firstName: admin2

lastName: fino

address: fino

userPassword: Redhat\@2

userStatus: Active

dn: dc=FinoPtaPlus,dc=com

objectClass: domain

objectClass: top

dc: FinoPtaPlus

description: FinoPtaPlus database

aci: (targetattr != "aci")(version 3.0; aci "rootdse anon read access"; allo

 w(read,search,compare) userdn="ldap\:///email=admin2\@fino.com,dc=admin,cn=sc

 hema";)

aci: (targetattr = "\*")(version 3.0; aci "rootdse anon read access"; allo

 w(read,search,compare,write,all) userdn="ldap\:///email=admin1\@fino.com,dc=a

 dmin,cn=schema";)

dn: ou=states,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: states

description: states list

dn: ou=accounts,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: accounts

description: accounts details

dn: ou=finoPtaPlusGl,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: finoPtaPlusGl

description: general ledger details

dn: ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: businessTypes

description: type of business master

aci: (targetattr = "\*")(version 3.0; aci "read"; allow(read,search,compare)

 groupdn="ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com  || ldap\://

 /cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

dn: ou=banks,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: banks

description: bank details

dn: ou=transactionGroups,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: transactionGroups

description: transactionGroup details

dn: ou=transactionTypes,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: transactionTypes

description: transactionType details

dn: ou=errorCodeMasters,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: errorCodeMasters

description: errorCodeMasters

dn: ou=holdCodeMasters,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: holdCodeMasters

description: holdCodeMasters

dn: ou=restrictionCodeMasters,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: restrictionCodeMasters

description: restrictionCodeMasters

dn: ou=actHoldsDtls,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: actHoldsDtls

description: actHoldsDtls

dn: ou=accountRestrictions,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: accountRestrictions

description: accountRestrictions

dn: ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: ptapluserrorcode

description: ptapluserrorcode

aci: (targetattr != "aci")(version 3.0; aci "rootdse anon read access"; allo

 w(read,search,compare) userdn="ldap\:///uid=admin,ou=serviceAccounts,dc=fino

 ptaplus,dc=com";)

dn: ou=merchants,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: merchants

aci: (targetattr = "\*")(version 3.0; aci "search all merchants"; allow(read,

 search,compare) groupdn="ldap\:///cn=admin,ou=roles,dc=finoptaplus,dc=com";)

aci: (targetattr = "\*")(version 3.0; aci "write"; allow(write,add) groupdn="

 ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com";)

aci: (targetattr = "aci")(version 3.0; aci "write"; allow(write) groupdn="ld

 ap\:///cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

dn: ou=active,ou=merchants,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: active

dn: ou=inactive,ou=merchants,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: inactive

dn: ou=statuses,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: statuses

description: statuses

aci: (targetattr = "\*")(version 3.0; aci "read"; allow(read,search,compare)

 groupdn="ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com  || ldap\://

 /cn=admin,ou=roles,dc=finoptaplus,dc=com  || ldap\:///cn=backoffice,ou=roles

 ,dc=finoptaplus,dc=com";)

dn: ou=groups,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: groups

dn: cn=finousers,ou=groups,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: posixGroup

objectClass: top

cn: finousers

gidNumber: 99999

uniqueMember: uid=admin,ou=serviceAccounts,dc=finoptaplus,dc=com

uniqueMember: uId=admin1,ou=activeusers,ou=users,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "admin can add members t

 o finousers"; allow(write) groupdn="ldap\:///cn=admin,ou=roles,dc=finoptaplu

 s,dc=com";)

dn: cn=finopartners,ou=groups,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: posixGroup

objectClass: top

cn: finopartners

gidNumber: 99999

aci: (targetattr = "\*")(version 3.0; aci "admin can add add partner groups";

  allow(write,add) groupdn="ldap\:///cn=backoffice,ou=roles,dc=finoptaplus,dc

 =com";)

dn: ou=roles,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: roles

dn: cn=admin,ou=roles,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: top

cn: admin

uniqueMember: statusCode=Active,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Inctive,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: uid=admin,ou=serviceAccounts,dc=finoptaplus,dc=com

uniqueMember: uId=admin1,ou=activeusers,ou=users,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "write"; allow(write) gr

 oupdn="ldap\:///cn=admin,ou=roles,dc=finoptaplus,dc=com";)

dn: cn=backoffice,ou=roles,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: top

cn: backoffice

uniqueMember: statusCode=Active,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Inactive,ou=statuses,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "write"; allow(write) gr

 oupdn="ldap\:///cn=admin,ou=roles,dc=finoptaplus,dc=com";)

dn: cn=partneradmin,ou=roles,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: top

cn: partneradmin

uniqueMember: statusCode=Active,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Blocked,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Dormant,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Inactive,ou=statuses,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "write"; allow(write) gr

 oupdn="ldap\:///cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

dn: cn=partnerops,ou=roles,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: top

cn: partnerops

uniqueMember: statusCode=Active,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Blocked,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Inactive,ou=statuses,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "write"; allow(write) gr

 oupdn="ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com || ldap\:///cn

 =backOffice,ou=roles,dc=finoptaplus,dc=com";)

dn: cn=merchant,ou=roles,dc=FinoPtaPlus,dc=com

objectClass: groupOfNames

objectClass: groupOfUniqueNames

objectClass: nsMemberOf

objectClass: top

cn: merchant

uniqueMember: statusCode=Active,ou=statuses,dc=finoptaplus,dc=com

uniqueMember: statusCode=Inactive,ou=statuses,dc=finoptaplus,dc=com

aci: (targetattr = "uniquemember")(version 3.0; aci "write"; allow(write) gr

 oupdn="ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com";)

dn: ou=users,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: users

aci: (targetattr = "\*")(targetfilter="memberof=cn=partneradmin,ou=roles,dc=f

 inoptaplus,dc=com")(version 3.0; aci "search all users"; allow(read,search,

 compare) groupdn="ldap\:///cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

aci: (targetattr = "\*")(version 3.0; aci "search all users"; allow(read,sear

 ch,compare) groupdn="ldap\:///cn=admin,ou=roles,dc=finoptaplus,dc=com";)

aci: (targetattr = "\*")(version 3.0; aci "write"; allow(write,add) groupdn="

 ldap\:///cn=admin,ou=roles,dc=finoptaplus,dc=com || ldap\:///cn=backoffice,ou

 =roles,dc=finoptaplus,dc=com || ldap\:///cn=partneradmin,ou=roles,dc=finopta

 plus,dc=com";)

aci: (targetattr = "lastModifiedOn || lastModifiedBy || primaryMobile || ema

 il || profileImage")(targetfilter="(memberof=cn=partnerops,ou=roles,dc=fino

 ptaplus,dc=com)")(version 3.0; aci "write"; allow(write) groupdn="ldap\:///c

 n=partnerops,ou=roles,dc=finoptaplus,dc=com";)

aci: (targetattr = "userPassword || firstLogin")(version 3.0; aci "write"; a

 llow(write) userdn="ldap\:///self";)

dn: ou=activeusers,ou=users,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: activeusers

dn: ou=inactiveusers,ou=users,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: inactiveusers

dn: uId=admin1,ou=activeusers,ou=users,dc=FinoPtaPlus,dc=com

objectClass: finoUsers

objectClass: top

createdDate: 20230803000000.000Z

email: finouser1\@gmail.com

firstLogin: FALSE

firstName: finouser1

id: 5

lastModifiedBy: modifiedBy=Admin1

lastModifiedOn: 20230803004400.367Z

lastName: kumar

memberOf: cn=admin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=finousers,ou=groups,dc=FinoPtaPlus,dc=com

uid: admin1

userPassword: Redhat\@1

createdBy: cn=Directory Manager

primaryMobile: 1000000006

profileImage: abc.png

dn: ou=serviceAccounts,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: serviceAccounts

description: serviceAccounts

aci: (targetattr = "\*")(version 3.0; aci "write"; allow(write,add) groupdn="

 ldap\:///cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

dn: uid=admin,ou=serviceAccounts,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: serviceAccount

objectClass: top

memberOf: cn=admin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=finousers,ou=groups,dc=FinoPtaPlus,dc=com

uid: admin

userPassword: redhat

dn: uid=backoffice,ou=serviceAccounts,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: serviceAccount

objectClass: top

memberOf: cn=backoffice,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=finousers,ou=groups,dc=FinoPtaPlus,dc=com

uid: backoffice

userPassword: redhat

dn: statusCode=Active,ou=statuses,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: statusMaster

objectClass: top

id: 1

memberOf: cn=admin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=backoffice,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=merchant,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=partneradmin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=partnerops,ou=roles,dc=FinoPtaPlus,dc=com

statusCode: Active

dn: statusCode=Inactive,ou=statuses,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: statusMaster

objectClass: top

id: 2

memberOf: cn=backoffice,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=merchant,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=partneradmin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=partnerops,ou=roles,dc=FinoPtaPlus,dc=com

statusCode: Inactive

dn: statusCode=Blocked,ou=statuses,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: statusMaster

objectClass: top

id: 3

memberOf: cn=partneradmin,ou=roles,dc=FinoPtaPlus,dc=com

memberOf: cn=partnerops,ou=roles,dc=FinoPtaPlus,dc=com

statusCode: Blocked

dn: statusCode=Dormant,ou=statuses,dc=FinoPtaPlus,dc=com

objectClass: nsMemberOf

objectClass: statusMaster

objectClass: top

id: 4

memberOf: cn=partneradmin,ou=roles,dc=FinoPtaPlus,dc=com

statusCode: Dormant

**To add 1\_Add\_Directory.ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 1\_Add\_Directory.ldif

![](https://lh7-us.googleusercontent.com/gYRoWnO6s8qvTZ6wqo7Z7vXlOm_JO6vv05Of5_N5VIlXkHdRJrL8AXjSCnrbdGC0IX3yXaO3CBPgpcmIQLIdqgdJSkGU8vNjVF8MMEaCMIEmmnnL-bUInMjYXyW527G_d44QkO2oIozmeXpjZbeOV5E)

**Note**:-

When you adding file, If you saw any error like syntax error or object not found its not a error because all the files depend on each other.

**To create 2\_Add\_common\_attribues.ldif**

-  vim 2\_Add\_common\_attribues.ldif

![](https://lh7-us.googleusercontent.com/3pwPYTAxQKLmAvZrfSU3QetEyQUz01ms1ZuC3MzlkcAVJw_DKQoZTj8lrNvDnqSu_tarzX8WUuMhrVO9vkQsQcfprM0KO0XK9A6aq5zCWtbFN7rbLFCJptNe5DV1J30IylkbwJ_aAUuy560_QS8SWKg)

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastModifiedOn-oid NAME 'lastModifiedOn' DESC 'lastModifiedOn, time' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( firstName-oid NAME 'firstName' DESC 'firstName,stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastName-oid NAME 'lastName' DESC 'lastName,stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant bank

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( id-oid NAME 'id' DESC 'id, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant state errormaster holdmaster restrictionmaster account

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (createdDate-oid NAME 'createdDate' DESC 'created Date, GeneralizedTime' EQUALITY generalizedTimeMatch  SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ))

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( alternateMobile-oid NAME 'alternateMobile' DESC 'alternate,telephone number' EQUALITY teleMatch SUBSTR telephoneNumberSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( email-oid NAME 'email' DESC 'email,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( virtualAddress-oid NAME 'virtualAddress' DESC 'virtualAddress,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( mccCode-oid NAME 'mccCode' DESC 'mccCode of merchant' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant bank gls

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( ifsc-oid NAME 'ifsc' DESC 'ifsc, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\# partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( address-oid NAME 'address' DESC 'address, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#merchant bank

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( bankName-oid NAME 'bankName' DESC 'bankName,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\# account

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountNo-oid NAME 'accountNo' DESC 'accountNo,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\# errormaster holdmaster ristrictionmaster account hold accountrestriction

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( creator-oid NAME 'creator' DESC 'Creator of Entity, DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#partner merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( typeOfBusiness-oid NAME 'typeOfBusiness' DESC 'typeOfBusiness, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#accounts gls transationType transactionGroup

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isActive-oid NAME 'isActive' DESC 'isActive, Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#+accounthold hold

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( description-oid NAME 'description' DESC 'Description, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isDormant-oid NAME 'isDormant' DESC 'Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( cifId-oid NAME 'cifId' DESC 'DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isClosed-oid NAME 'isClosed' DESC 'Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#new\_attributes

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isGLType-oid NAME 'isGLType' DESC 'isGlType,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (emailId-oid NAME 'emailId' DESC 'emailId,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( VPAPrefixid-oid NAME 'VPAPrefixid' DESC 'VPAPrefixid,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( firstLogin-oid NAME 'firstLogin' DESC 'firstLogin,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (merchantBusinessName-oid NAME 'merchantBusinessName' DESC 'merchantBusinessName,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( activeVirtualAddress-oid NAME 'activeVirtualAddress' DESC 'activeVirtualAddress,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( inactiveVirtualAddress-oid NAME 'inactiveVirtualAddress' DESC 'inactiveVirtualAddress,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( createdBy-oid NAME 'createdBy' DESC 'createdBy,string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

**To add 2\_Add\_common\_attribues.ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 2\_Add\_common\_attribues.ldif

![](https://lh7-us.googleusercontent.com/Kf1_RV4r0wzbNi6IZWq5T3Wq0rRyiPh5WaZyCjEfpiQ2PaurBFKG_TVnEYER_7-m50KQQr6xIsYRbiooGyDseOCn-qOfCfRKlTXxk6cstXZ64SB9DigLdu9sPGcTCmsnIflQVX1iIixJj08hXbyRi1s)

**To create 3\_Add\_object\_class.ldif on ldap server**

-  vim 3\_Add\_object\_class.ldif

![](https://lh7-us.googleusercontent.com/ijJ4c0xCeN4Ub50bDlvADkxMsfNoU5aqpZYXA9DNalvWkntmpAPmdf-_iUiwhWcb2jopGKUokOokfMv24JD80FZewws6hwUIim1xns40Q5uQkfGTtgCsoW_9HCi5jZVsjIavU1HubZFBbbrSE4dAYG0)

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( finoUsers-oid NAME 'finoUsers' SUP top STRUCTURAL MUST (id $ userId $ firstName $ lastName $ userPassword $ primaryMobile $ lastModifiedBy $ lastModifiedOn $ createdDate $ createdBy $ firstLogin $ email ) MAY ( profileImage $ memberOf $ uniquemember) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( partners-oid NAME 'partners' SUP top STRUCTURAL MUST (id $ userId $ primaryMobile $ firstName $ lastName $ typeOfBusiness $ address $ userPassword $ mccCode $ ifsc $ isGLType $ primaryAccount $ accountHolderName $ gst $ gstImage $ createdDate $ createdBy $ lastModifiedBy $ lastModifiedOn $ VPAPrefixid $ settlementAccount $ accountPVD $ firstLogin ) MAY ( businessName $ email $ virtualAddress $ pan $ panImage $ profileImage $ memberOf $ uniquemember) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( partnerOps-oid NAME 'partnerOps' SUP top STRUCTURAL MUST (id $ userId $ firstName $ lastName $ email $  userPassword $ primaryMobile $ lastModifiedBy $ lastModifiedOn $ createdDate $ createdBy $ firstLogin ) MAY ( profileImage $ memberOf $ uniquemember) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( merchants-oid NAME 'merchants' SUP top STRUCTURAL MUST ( id $ institutionId $ mobileNo $ accountType $  name $ userId $ emailId $ address $ merchantBusinessName $ merchantCategory $ linkedBankAccount $ ifsc $ accountNo $ accountPVD $ status $ statusDateTime $ dealerCode $ sid $ tid $ mid $ registrationDateTime $ merchantId  $ merchantStatus $  merchantAggregator $ onBoardingType $ merchantGenerate $ merchantOwnType $ settlementAccount $ franchise $ brand $ merchantType $ createdDate $ createdBy $ lastModifiedBy $ lastModifiedOn ) MAY ( activeVirtualAddress $ inactiveVirtualAddress $ firstName $ lastName $ alternateMobile $ isNotification $ memberOf $ uniquemember) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( serviceAccount-oid NAME 'serviceAccount' SUP top STRUCTURAL MUST (userId $ userPassword ) MAY () X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=partnerOpsId,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: userId

dnatype: id

dnafilter: (objectclass=partnerOps)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

dn: cn=userId,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: userId

dnatype: id

dnafilter: (objectclass=finoUsers)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 3\_Add\_object\_class..ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 3\_Add\_object\_class.ldif

![](https://lh7-us.googleusercontent.com/U5oDGP9PlZZt3d4tWXJjOIRpTv8ZOsuOoylA5frXeUrzD4HBR7MpnbbVE1q6yttxXU7EIhq3OKfxWadJs0XeGlmFoCsw2Z1MleHr2FBTTt_P2VlNvLohex0-QyBhldbkdO0PJO9IDAGMLq5U6OZ2H8w)

**To create 4\_error\_Code.ldif**

-  vim 4\_error\_Code.ldif

![](https://lh7-us.googleusercontent.com/dJhO1k5JhBMxq63ksYf5hyeF47ktG-QSJtJB7TXCMeguZF00cE4IiAM_USmvw360bEcG98IJZHI8EjWdy1ZwlNWm3IHj6RzUqph3kh1OH3iUBQhPdrsMwZzlDLMwX18jv4aCoYn9UeycY1WFf0D56p0)

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( PTAErrorcode-oid NAME 'PTAErrorcode' DESC 'PTAErrorcode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( ErrorSource-oid NAME 'ErrorSource' DESC 'ErrorSource, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( NativeErrorCode-oid NAME 'NativeErrorCode' DESC 'NativeErrorCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( NativeErrorMessage-oid NAME 'NativeErrorMessage' DESC 'NativeErrorMessage, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( NativeErrorDescription-oid NAME 'NativeErrorDescription' DESC 'NativeErrorDescription, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( HTTPCode-oid NAME 'HTTPCode' DESC 'HTTPCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( StatusCode-oid NAME 'StatusCode' DESC 'StatusCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( HTTPCodeDescription-oid NAME 'HTTPCodeDescription' DESC 'HTTPCodeDescription, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( ErrorMessage-oid NAME 'ErrorMessage' DESC 'ErrorMessage, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( TroubleshootMessage-oid NAME 'TroubleshootMessage' DESC 'TroubleshootMessage, stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( errorcodeptaplus-oid NAME 'errorcodeptaplus' SUP top STRUCTURAL MUST (ErrorSource $ PTAErrorcode $ NativeErrorCode $ HTTPCode $ StatusCode $ ErrorMessage ) MAY (TroubleshootMessage $ HTTPCodeDescription $ NativeErrorMessage $ NativeErrorDescription) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

**To add 4\_error\_Code.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 4\_error\_Code.ldif

![](https://lh7-us.googleusercontent.com/4OMSZRaxUW_u7m5V7UQmig2kI3doFh7vjBPCL1iEtX1t47OdfodWeQ8fCswBi7Vdzoq6LDP7kzESYM9EBkZUPm6gCFBBGAwISLPwhb6Om7supp4_sGoe2AuPq06IzqnqBlzOjE4fxmX2iF2_4EDiEAQ)

**To create 5\_add\_account.ldif**

-  vim 5\_add\_account.ldif

![](https://lh7-us.googleusercontent.com/sFjVxw0fQwi10VA14gdjl2WAFQOEJgSl6yiKr1ZbcSeh9uEF6ILQf9j5DKu7egqeZrVCZFWQjoeIUSNPIJf5yz4JJe4XtzbCtDVn4SHn-u2qqj3XbxEDxd9PMCrbiRikd94I4cySeiJzrUwy2laEvbU)

\#accounts

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accstatusCode-oid NAME 'accstatusCode' DESC 'IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accStatus-oid NAME 'accStatus' DESC 'IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accType-oid NAME 'accType' DESC 'IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isAccountHold-oid NAME 'isAccountHold' DESC 'Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isAccountRestricted-oid NAME 'isAccountRestricted' DESC 'isAccountRestricted, Boolean' EQUALITY  booleanMatch  SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\#

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountLastRestrictionApplyDate-oid NAME 'accountLastRestrictionApplyDate' DESC 'GeneralizedTime' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountLastRestrictionApplyUser-oid NAME 'accountLastRestrictionApplyUser' DESC 'DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountLastRestrictionRemovalDate-oid NAME 'accountLastRestrictionRemovalDate' DESC 'GeneralizedTime' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountLastRestrictionRemovalUser-oid NAME 'accountLastRestrictionRemovalUser' DESC 'DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountMinBalanceFixed-oid NAME 'accountMinBalanceFixed' DESC 'DirectoryString' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountMinBalancePercent-oid NAME 'accountMinBalancePercent' DESC 'DirectoryString' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( cifId-oid NAME 'cifId' DESC 'DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isClosed-oid NAME 'isClosed' DESC 'Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isDormant-oid NAME 'isDormant' DESC 'Boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\# new added

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountsUid-oid NAME 'accountsUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( creationDate-oid NAME 'creationDate' DESC 'GeneralizedTime' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountNum-oid NAME 'accountNum' DESC 'IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( cbsCustomerId-oid NAME 'cbsCustomerId' DESC 'IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( activationAuditTrail-oid NAME 'activationAuditTrail' DESC 'activationAuditTrail' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountRestrictionApplyAuditTrail-oid NAME 'accountRestrictionApplyAuditTrail' DESC 'accountRestrictionApplyAuditTrail' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( deactivationAuditTrail-oid NAME 'deactivationAuditTrail' DESC 'deactivationAuditTrail' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastDeActivationDate-oid NAME 'lastDeActivationDate' DESC 'Entity Last DeActivation Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( finoPTAaccount-oid NAME 'finoPTAaccount' SUP top STRUCTURAL MUST ( accountNum $ cbsCustomerId $ isActive $ creationDate $ creator $ lastActivationDate $ lastActivationUser $ isAccountRestricted ) MAY ( cifId $ accountMinBalanceFixed $ accountMinBalancePercent $ isDormant $ isClosed $ activationAuditTrail $ lastDeActivationDate $ lastDeActivationUser $ deactivationAuditTrail $ accountLastRestrictionApplyDate $ accountLastRestrictionApplyUser $ accountRestrictionApplyAuditTrail $ accountLastRestrictionRemovalDate $ accountLastRestrictionRemovalUser ) X-ORIGIN ( 'Fino PTA' 'user defined' ) )

dn: cn=accountsUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: accountsUid

dnatype: accountsUid

dnafilter: (objectclass=accounts)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 5\_add\_account.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 5\_add\_account.ldif

![](https://lh7-us.googleusercontent.com/YQS7E0XL0ce0Lr2SVPqL0KWe2cv0CqprstlxknOIh7olLnFw5WsmLxCsff807RGGeshRnYCxlrjCRE3yiNavNHHt17ql1d6O0SaemOvQhTqZuihESruZqopRdKrZ_dBmby7iXAzI0Gfp0Kr6AsPfsLM)

**To create 6\_add\_bussiness\_type\_code.ldif**

-  vim 6\_add\_bussiness\_type\_code.ldif

![](https://lh7-us.googleusercontent.com/uSYgT0gdCj4rok1ItujlAN60ZjbYWjR-l8sfuYCx1JdqathCRovm6RcFCnjcs7z_YTR5AlgQZBZAVuPr3LGqVQyl9QdgGHraLLnO3P14ApzpC8HeOsPt_pG5V619I_ig9hIL2IpVi7xLKbzYocYhyyw)

version: 1

dn: ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: organizationalUnit

objectClass: top

ou: businessTypes

description:: YnVzaW5lc3MgdHlwZSBkZXRhaWxzICA=

aci: (targetattr = "\*")(version 3.0; aci "read"; allow(read,search,compare)

 groupdn="ldap\:///cn=partneradmin,ou=roles,dc=finoptaplus,dc=com  || ldap\://

 /cn=backoffice,ou=roles,dc=finoptaplus,dc=com";)

dn: mcode=763,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 276

mCode: 763

mCategory: Agricultural co-operatives

dn: mcode=780,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 277

mCode: 780

mCategory: Landscaping and horticultural services

dn: mcode=5995,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 278

mCode: 5995

mCategory: Pet shops, pet food and supplies

dn: mcode=5611,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 279

mCode: 5611

mCategory: Men's and boys' clothing and accessory shops

dn: mcode=5621,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 280

mCode: 5621

mCategory: Women's ready-to-wear shops

dn: mcode=5631,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 281

mCode: 5631

mCategory: Women's accessory and speciality shops

dn: mcode=5641,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 282

mCode: 5641

mCategory: Children's and infants' wear shops

dn: mcode=5651,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 283

mCode: 5651

mCategory: Family clothing shops

dn: mcode=5661,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 284

mCode: 5661

mCategory: Shoe shops

dn: mcode=5681,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 285

mCode: 5681

mCategory: Furriers and fur shops

dn: mcode=5691,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 286

mCode: 5691

mCategory: Men's and women's clothing shops

dn: mcode=5697,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 287

mCode: 5697

mCategory: Tailors, seamstresses, mending and alterations

dn: mcode=5698,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 288

mCode: 5698

mCategory: Wig and toupee shops

dn: mcode=5699,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 289

mCode: 5699

mCategory: Miscellaneous apparel and accessory shops

dn: mcode=7210,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 290

mCode: 7210

mCategory: Laundry, cleaning and garment services

dn: mcode=7211,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 291

mCode: 7211

mCategory: Laundry services - family and commercial

dn: mcode=7216,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 292

mCode: 7216

mCategory: Dry cleaners

dn: mcode=7217,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 293

mCode: 7217

mCategory: Carpet and upholstery cleaning

dn: mcode=7296,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 294

mCode: 7296

mCategory: Clothing rentals - costumes, uniforms and formal wear

dn: mcode=1520,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 295

mCode: 1520

mCategory: General contractors - residential and commercial

dn: mcode=1711,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 296

mCode: 1711

mCategory: Heating, plumbing and air-conditioning contractors

dn: mcode=1731,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 297

mCode: 1731

mCategory: Electrical contractors

dn: mcode=1740,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 298

mCode: 1740

mCategory: Masonry, stonework, tile setting, plastering and insulation contr

 actors

dn: mcode=1750,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 299

mCode: 1750

mCategory: Carpentry contractors

dn: mcode=1761,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 300

mCode: 1761

mCategory: Roofing, siding and sheet metal work contractors

dn: mcode=1771,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 301

mCode: 1771

mCategory: Concrete work contractors

dn: mcode=1799,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 302

mCode: 1799

mCategory: Special trade contractors - not elsewhere classified

dn: mcode=2741,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 303

mCode: 2741

mCategory: Miscellaneous publishing and printing services

dn: mcode=2791,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 304

mCode: 2791

mCategory: Typesetting, platemaking and related services

dn: mcode=2842,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 305

mCode: 2842

mCategory: Speciality cleaning, polishing and sanitation preparations

dn: mcode=5942,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 306

mCode: 5942

mCategory: Bookshops

dn: mcode=5943,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 307

mCode: 5943

mCategory: Stationery, office and school supply shops

dn: mcode=8211,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 308

mCode: 8211

mCategory: Elementary and secondary schools

dn: mcode=8220,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 309

mCode: 8220

mCategory: Colleges, universities, professional schools and junior colleges

dn: mcode=8241,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 310

mCode: 8241

mCategory: Correspondence schools

dn: mcode=8244,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 311

mCode: 8244

mCategory: Business and secretarial schools

dn: mcode=8249,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 312

mCode: 8249

mCategory: Trade and vocational schools

dn: mcode=8299,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 313

mCode: 8299

mCategory: Schools and educational services - not elsewhere classified

dn: mcode=5722,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 314

mCode: 5722

mCategory: Household appliance shops

dn: mcode=5732,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 315

mCode: 5732

mCategory: Electronics shops

dn: mcode=5733,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 316

mCode: 5733

mCategory: Music shops - musical instruments, pianos and sheet music

dn: mcode=5734,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 317

mCode: 5734

mCategory: Computer software outlets

dn: mcode=5735,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 318

mCode: 5735

mCategory: Record shops

dn: mcode=5815,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 319

mCode: 5815

mCategory: Digital Goods: Media, Books, Movies, Music

dn: mcode=5816,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 320

mCode: 5816

mCategory: Digital Goods: Games

dn: mcode=5817,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 321

mCode: 5817

mCategory: Digital Goods: Applications (Excludes Games)

dn: mcode=5818,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 322

mCode: 5818

mCategory: Digital Goods: Large Digital Goods Merchant

dn: mcode=5946,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 323

mCode: 5946

mCategory: Camera and photographic supply shops

dn: mcode=7221,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 324

mCode: 7221

mCategory: Photographic studios

dn: mcode=7372,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 325

mCode: 7372

mCategory: Computer programming, data processing and integrated systems desi

 gn services

dn: mcode=7379,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 326

mCode: 7379

mCategory: Computer maintenance and repair services - not elsewhere classifi

 ed

dn: mcode=7622,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 327

mCode: 7622

mCategory: Electronics repair shops

dn: mcode=7623,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 328

mCode: 7623

mCategory: Air conditioning and refrigeration repair shops

dn: mcode=7629,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 329

mCode: 7629

mCategory: Electrical and small appliance repair shops

dn: mcode=7631,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 330

mCode: 7631

mCategory: Watch, clock and jewellery repair shops

dn: mcode=7829,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 331

mCode: 7829

mCategory: Motion picture and video tape production and distribution

dn: mcode=7832,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 332

mCode: 7832

mCategory: Motion picture theatres

dn: mcode=7911,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 333

mCode: 7911

mCategory: Dance halls, studios and schools

dn: mcode=7922,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 334

mCode: 7922

mCategory: Theatrical producers (except motion pictures) and ticket agencies

dn: mcode=7929,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 335

mCode: 7929

mCategory: Bands, orchestras and miscellaneous entertainers - not elsewhere

 classified

dn: mcode=7932,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 336

mCode: 7932

mCategory: Billiard and pool establishments

dn: mcode=7933,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 337

mCode: 7933

mCategory: Bowling alleys

dn: mcode=7991,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 338

mCode: 7991

mCategory: Tourist attractions and exhibits

dn: mcode=7993,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 339

mCode: 7993

mCategory: Video amusement game supplies

dn: mcode=7994,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 340

mCode: 7994

mCategory: Video game arcades and establishments

dn: mcode=7995,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 341

mCode: 7995

mCategory: Betting, including lottery tickets, casino gaming chips, off-trac

 k betting and wagers at race tracks

dn: mcode=7996,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 342

mCode: 7996

mCategory: Amusement parks, circuses, carnivals and fortune tellers

dn: mcode=7998,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 343

mCode: 7998

mCategory: Aquariums, seaquariums and dolphinariums

dn: mcode=7999,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 344

mCode: 7999

mCategory: Recreation services - not elsewhere classified

dn: mcode=6010,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 345

mCode: 6010

mCategory: Financial institutions manual cash disbursements/Cash Withdrawal

dn: mcode=6011,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 346

mCode: 6011

mCategory: Financial institutions - automated cash disbursements

dn: mcode=6051,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 347

mCode: 6051

mCategory: Non-financial institutions - foreign currency, money orders (not

 wire transfer), scrip and travellers' checks

dn: mcode=6540,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 348

mCode: 6540

mCategory: Debit card to wallet credit (Wallet top up)

dn: mcode=7321,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 349

mCode: 7321

mCategory: Consumer credit reporting agencies

dn: mcode=5811,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 350

mCode: 5811

mCategory: Caterers

dn: mcode=5812,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 351

mCode: 5812

mCategory: Eating places and restaurants

dn: mcode=5814,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 352

mCode: 5814

mCategory: Fast food restaurants

dn: mcode=9223,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 353

mCode: 9223

mCategory: Bail and bond payments

dn: mcode=9402,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 354

mCode: 9402

mCategory: Postal services - government only

dn: mcode=8111,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 355

mCode: 8111

mCategory: Legal services and attorneys

dn: mcode=8398,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 356

mCode: 8398

mCategory: Charitable and social service organizations - PM Relief Fund

dn: mcode=8641,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 357

mCode: 8641

mCategory: Civic, social and fraternal associations

dn: mcode=8651,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 358

mCode: 8651

mCategory: Political organizations

dn: mcode=7230,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 359

mCode: 7230

mCategory: Beauty and barber shops

dn: mcode=7273,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 360

mCode: 7273

mCategory: Dating and escort services

dn: mcode=7297,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 361

mCode: 7297

mCategory: Massage parlours

dn: mcode=7298,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 362

mCode: 7298

mCategory: Health and beauty spas

dn: mcode=7299,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 363

mCode: 7299

mCategory: Miscellaneous personal services - not elsewhere classified

dn: mcode=5962,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 364

mCode: 5962

mCategory: Telemarketing - travel-related arrangement services

dn: mcode=5963,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 365

mCode: 5963

mCategory: Door-to-door sales

dn: mcode=5964,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 366

mCode: 5964

mCategory: Direct marketing - catalogue merchants

dn: mcode=5965,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 367

mCode: 5965

mCategory: Direct marketing - combination catalogue and retail merchants

dn: mcode=5966,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 368

mCode: 5966

mCategory: Direct marketing - outbound telemarketing merchants

dn: mcode=5967,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 369

mCode: 5967

mCategory: Direct marketing - inbound telemarketing merchants

dn: mcode=5968,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 370

mCode: 5968

mCategory: Direct marketing - continuity/subscription merchants

dn: mcode=7311,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 371

mCode: 7311

mCategory: Advertising services

dn: mcode=7333,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 372

mCode: 7333

mCategory: Commercial photography, art and graphics

dn: mcode=5912,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 373

mCode: 5912

mCategory: Drug stores and pharmacies

dn: mcode=5975,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 374

mCode: 5975

mCategory: Hearing aids - sales, service and supplies

dn: mcode=5976,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 375

mCode: 5976

mCategory: Orthopaedic goods and prosthetic devices

dn: mcode=7339,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 376

mCode: 7339

mCategory: Stenographic and secretarial support services

dn: mcode=8011,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 377

mCode: 8011

mCategory: Doctors and physicians - not elsewhere classified

dn: mcode=8021,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 378

mCode: 8021

mCategory: Dentists and orthodontists

dn: mcode=8031,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 379

mCode: 8031

mCategory: Osteopaths

dn: mcode=8041,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 380

mCode: 8041

mCategory: Chiropractors

dn: mcode=8042,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 381

mCode: 8042

mCategory: Optometrists and ophthalmologists

dn: mcode=8043,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 382

mCode: 8043

mCategory: Opticians, optical goods and eyeglasses

dn: mcode=8049,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 383

mCode: 8049

mCategory: Podiatrists and chiropodists

dn: mcode=8050,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 384

mCode: 8050

mCategory: Nursing and personal care facilities

dn: mcode=8062,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 385

mCode: 8062

mCategory: Hospitals

dn: mcode=8071,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 386

mCode: 8071

mCategory: Medical and dental laboratories

dn: mcode=8099,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 387

mCode: 8099

mCategory: Medical services and health practitioners not elsewhere classifie

 d

dn: mcode=5935,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 388

mCode: 5935

mCategory: Wrecking and salvage yards

dn: mcode=5994,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 389

mCode: 5994

mCategory: Newsagents and news-stands

dn: mcode=7261,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 390

mCode: 7261

mCategory: Funeral services and crematoriums

dn: mcode=7277,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 391

mCode: 7277

mCategory: Counselling services - debt, marriage and personal

dn: mcode=7342,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 392

mCode: 7342

mCategory: Exterminating and disinfecting services

dn: mcode=7349,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 393

mCode: 7349

mCategory: Cleaning, maintenance and janitorial services

dn: mcode=7361,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 394

mCode: 7361

mCategory: Employment agencies and temporary help services

dn: mcode=7375,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 395

mCode: 7375

mCategory: Information retrieval services

dn: mcode=7392,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 396

mCode: 7392

mCategory: Management, consulting and public relations services

dn: mcode=7393,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 397

mCode: 7393

mCategory: Detective agencies, protective agencies and security services, in

 cluding armoured cars and guard dogs

dn: mcode=7395,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 398

mCode: 7395

mCategory: Photofinishing laboratories and photo developing

dn: mcode=7399,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 399

mCode: 7399

mCategory: Business services - not elsewhere classified

dn: mcode=8351,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 400

mCode: 8351

mCategory: Child care services

dn: mcode=8661,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 401

mCode: 8661

mCategory: Religious organizations

dn: mcode=8699,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 402

mCode: 8699

mCategory: Membership organization - not elsewhere classified

dn: mcode=8734,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 403

mCode: 8734

mCategory: Testing laboratories (non-medical)

dn: mcode=8911,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 404

mCode: 8911

mCategory: Architectural, engineering and surveying services

dn: mcode=8999,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 405

mCode: 8999

mCategory: Professional services - not elsewhere classified

dn: mcode=6513,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 406

mCode: 6513

mCategory: Real Estate Agents and Managers - Rentals

dn: mcode=7011,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 407

mCode: 7011

mCategory: Lodging - hotels, motels and resorts

dn: mcode=5013,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 408

mCode: 5013

mCategory: Motor vehicle supplies and new parts

dn: mcode=5021,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 409

mCode: 5021

mCategory: Office and commercial furniture

dn: mcode=5039,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 410

mCode: 5039

mCategory: Construction materials - not elsewhere classified

dn: mcode=5044,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 411

mCode: 5044

mCategory: Office, photographic, photocopy and microfilm equipment

dn: mcode=5045,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 412

mCode: 5045

mCategory: Computers, computer peripheral equipment - not elsewhere classifi

 ed

dn: mcode=5046,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 413

mCode: 5046

mCategory: Commercial equipment - not elsewhere classified

dn: mcode=5047,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 414

mCode: 5047

mCategory: Dental/laboratory/medical/ophthalmic hospital equipment and suppl

 ies

dn: mcode=5051,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 415

mCode: 5051

mCategory: Metal service centres and offices

dn: mcode=5065,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 416

mCode: 5065

mCategory: Electrical parts and equipment

dn: mcode=5072,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 417

mCode: 5072

mCategory: Hardware equipment and supplies

dn: mcode=5074,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 418

mCode: 5074

mCategory: Plumbing and heating equipment and supplies

dn: mcode=5085,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 419

mCode: 5085

mCategory: Industrial supplies - not elsewhere classified

dn: mcode=5094,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 420

mCode: 5094

mCategory: Precious stones and metals, watches and jewellery

dn: mcode=5099,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 421

mCode: 5099

mCategory: Durable goods - not elsewhere classified

dn: mcode=5111,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 422

mCode: 5111

mCategory: Stationery, office supplies and printing and writing paper

dn: mcode=5122,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 423

mCode: 5122

mCategory: Drugs, drug proprietors

dn: mcode=5131,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 424

mCode: 5131

mCategory: Piece goods, notions and other dry goods

dn: mcode=5137,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 425

mCode: 5137

mCategory: Men's, women's and children's uniforms and commercial clothing

dn: mcode=5139,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 426

mCode: 5139

mCategory: Commercial footwear

dn: mcode=5169,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 427

mCode: 5169

mCategory: Chemicals and allied products - not elsewhere classified

dn: mcode=5192,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 428

mCode: 5192

mCategory: Books, periodicals and newspapers

dn: mcode=5193,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 429

mCode: 5193

mCategory: Florists' supplies, nursery stock and flowers

dn: mcode=5198,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 430

mCode: 5198

mCategory: Paints, varnishes and supplies

dn: mcode=5199,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 431

mCode: 5199

mCategory: Non-durable goods - not elsewhere classified

dn: mcode=5200,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 432

mCode: 5200

mCategory: Home supply warehouse outlets

dn: mcode=5211,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 433

mCode: 5211

mCategory: Lumber and building materials outlets

dn: mcode=5231,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 434

mCode: 5231

mCategory: Glass, paint and wallpaper shops

dn: mcode=5251,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 435

mCode: 5251

mCategory: Hardware shops

dn: mcode=5261,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 436

mCode: 5261

mCategory: Lawn and garden supply outlets, including nurseries

dn: mcode=5271,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 437

mCode: 5271

mCategory: Mobile home dealers

dn: mcode=5300,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 438

mCode: 5300

mCategory: Wholesale clubs

dn: mcode=5309,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 439

mCode: 5309

mCategory: Duty-free shops

dn: mcode=5310,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 440

mCode: 5310

mCategory: Discount shops

dn: mcode=5311,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 441

mCode: 5311

mCategory: Department stores

dn: mcode=5331,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 442

mCode: 5331

mCategory: Variety stores

dn: mcode=5399,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 443

mCode: 5399

mCategory: Miscellaneous general merchandise

dn: mcode=5411,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 444

mCode: 5411

mCategory: Groceries and supermarkets

dn: mcode=5422,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 445

mCode: 5422

mCategory: Freezer and locker meat provisioners

dn: mcode=5441,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 446

mCode: 5441

mCategory: Candy, nut and confectionery shops

dn: mcode=5451,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 447

mCode: 5451

mCategory: Dairies

dn: mcode=5462,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 448

mCode: 5462

mCategory: Bakeries

dn: mcode=5499,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 449

mCode: 5499

mCategory: Miscellaneous food shops - convenience and speciality retail outl

 ets

dn: mcode=5511,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 450

mCode: 5511

mCategory: Car and truck dealers (new and used) sales, services, repairs, pa

 rts and leasing

dn: mcode=5521,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 451

mCode: 5521

mCategory: Car and truck dealers (used only) sales, service, repairs, parts

 and leasing

dn: mcode=5531,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 452

mCode: 5531

mCategory: Auto and home supply outlets

dn: mcode=5532,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 453

mCode: 5532

mCategory: Automotive tyre outlets

dn: mcode=5533,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 454

mCode: 5533

mCategory: Automotive parts and accessories outlets

dn: mcode=5541,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 455

mCode: 5541

mCategory: Service stations (with or without ancillary services)

dn: mcode=5551,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 456

mCode: 5551

mCategory: Boat dealers

dn: mcode=5561,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 457

mCode: 5561

mCategory: Camper, recreational and utility trailer dealers

dn: mcode=5571,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 458

mCode: 5571

mCategory: Motorcycle shops and dealers

dn: mcode=5592,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 459

mCode: 5592

mCategory: Motor home dealers

dn: mcode=5598,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 460

mCode: 5598

mCategory: Snowmobile dealers

dn: mcode=5599,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 461

mCode: 5599

mCategory: Miscellaneous automotive, aircraft and farm equipment dealers - n

 ot elsewhere classified

dn: mcode=5712,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 462

mCode: 5712

mCategory: Furniture, home furnishings and equipment shops and manufacturers

 , except appliances

dn: mcode=5713,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 463

mCode: 5713

mCategory: Floor covering services

dn: mcode=5714,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 464

mCode: 5714

mCategory: Drapery, window covering and upholstery shops

dn: mcode=5718,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 465

mCode: 5718

mCategory: Fireplaces, fireplace screens and accessories shops

dn: mcode=5719,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 466

mCode: 5719

mCategory: Miscellaneous home furnishing speciality shops

dn: mcode=5931,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 467

mCode: 5931

mCategory: Used merchandise and second-hand shops

dn: mcode=5932,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 468

mCode: 5932

mCategory: Antique shops - sales, repairs and restoration services

dn: mcode=5933,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 469

mCode: 5933

mCategory: Pawn shops

dn: mcode=5937,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 470

mCode: 5937

mCategory: Antique reproduction shops

dn: mcode=5944,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 471

mCode: 5944

mCategory: Jewellery, watch, clock and silverware shops

dn: mcode=5945,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 472

mCode: 5945

mCategory: Hobby, toy and game shops

dn: mcode=5947,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 473

mCode: 5947

mCategory: Gift, card, novelty and souvenir shops

dn: mcode=5948,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 474

mCode: 5948

mCategory: Luggage and leather goods shops

dn: mcode=5949,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 475

mCode: 5949

mCategory: Sewing, needlework, fabric and piece goods shops

dn: mcode=5950,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 476

mCode: 5950

mCategory: Glassware and crystal shops

dn: mcode=5970,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 477

mCode: 5970

mCategory: Artist supply and craft shops

dn: mcode=5971,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 478

mCode: 5971

mCategory: Art dealers and galleries

dn: mcode=5972,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 479

mCode: 5972

mCategory: Stamp and coin shops

dn: mcode=5973,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 480

mCode: 5973

mCategory: Religious goods and shops

dn: mcode=5977,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 481

mCode: 5977

mCategory: Cosmetic Stores

dn: mcode=5978,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 482

mCode: 5978

mCategory: Typewriter outlets - sales, service and rentals

dn: mcode=5992,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 483

mCode: 5992

mCategory: Florists

dn: mcode=5993,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 484

mCode: 5993

mCategory: Cigar shops and stands

dn: mcode=5997,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 485

mCode: 5997

mCategory: Electric razor outlets - sales and service

dn: mcode=5998,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 486

mCode: 5998

mCategory: Tent and awning shops

dn: mcode=5999,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 487

mCode: 5999

mCategory: Miscellaneous and speciality retail outlets

dn: mcode=7251,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 488

mCode: 7251

mCategory: Shoe repair shops, shoe shine parlours and hat cleaning shops

dn: mcode=7278,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 489

mCode: 7278

mCategory: Buying and shopping services and clubs

dn: mcode=7332,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 490

mCode: 7332

mCategory: Blueprinting and Photocopying Services

dn: mcode=7338,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 491

mCode: 7338

mCategory: Quick copy, reproduction and blueprinting services

dn: mcode=7394,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 492

mCode: 7394

mCategory: Equipment, tool, furniture and appliance rentals and leasing

dn: mcode=7641,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 493

mCode: 7641

mCategory: Furniture reupholstery, repair and refinishing

dn: mcode=7692,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 494

mCode: 7692

mCategory: Welding services

dn: mcode=7699,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 495

mCode: 7699

mCategory: Miscellaneous repair shops and related services

dn: mcode=7841,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 496

mCode: 7841

mCategory: Video tape rentals

dn: mcode=5715,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 497

mCode: 5715

mCategory: Alcoholic beverage wholesalers

dn: mcode=5813,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 498

mCode: 5813

mCategory: Drinking places (alcoholic beverages) - bars, taverns, night-club

 s, cocktail lounges and discotheques

dn: mcode=5921,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 499

mCode: 5921

mCategory: Package shops - beer, wine and liquor

dn: mcode=5655,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 500

mCode: 5655

mCategory: Sports and riding apparel shops

dn: mcode=5940,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 501

mCode: 5940

mCategory: Bicycle shops - sales and service

dn: mcode=5941,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 502

mCode: 5941

mCategory: Sporting goods shops

dn: mcode=5996,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 503

mCode: 5996

mCategory: Swimming pools - sales, supplies and services

dn: mcode=7012,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 504

mCode: 7012

mCategory: Timeshares

dn: mcode=7032,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 505

mCode: 7032

mCategory: Sporting and recreational camps

dn: mcode=7033,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 506

mCode: 7033

mCategory: Trailer parks and camp-sites

dn: mcode=7941,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 507

mCode: 7941

mCategory: Commercial sports, professional sports clubs, athletic fields and

  sports promoters

dn: mcode=7992,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 508

mCode: 7992

mCategory: Public golf courses

dn: mcode=7997,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 509

mCode: 7997

mCategory: Membership clubs (sports, recreation, athletic), country clubs an

 d private golf courses

dn: mcode=7276,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 510

mCode: 7276

mCategory: Tax preparation services

dn: mcode=8931,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 511

mCode: 8931

mCategory: Accounting, auditing and bookkeeping services

dn: mcode=3020,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 512

mCode: 3020

mCategory: AIR-INDIA

dn: mcode=4011,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 513

mCode: 4011

mCategory: Railroads

dn: mcode=4119,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 514

mCode: 4119

mCategory: Ambulance services

dn: mcode=4121,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 515

mCode: 4121

mCategory: Taxi-cabs and limousines

dn: mcode=4131,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 516

mCode: 4131

mCategory: Bus lines

dn: mcode=4214,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 517

mCode: 4214

mCategory: Motor freight carriers and trucking - local and long distance, mo

 ving and storage companies and local delivery

dn: mcode=4215,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 518

mCode: 4215

mCategory: Courier services - air and ground and freight forwarders

dn: mcode=4225,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 519

mCode: 4225

mCategory: Public warehousing and storage - farm products, refrigerated good

 s and household goods

dn: mcode=4411,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 520

mCode: 4411

mCategory: Steamships and cruise lines

dn: mcode=4457,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 521

mCode: 4457

mCategory: Boat rentals and leasing

dn: mcode=4468,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 522

mCode: 4468

mCategory: Marinas, marine service and supplies

dn: mcode=4511,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 523

mCode: 4511

mCategory: Airlines and air carriers

dn: mcode=4582,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 524

mCode: 4582

mCategory: Airports, flying fields and airport terminals

dn: mcode=4722,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 525

mCode: 4722

mCategory: Travel agencies and tour operators

dn: mcode=4784,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 526

mCode: 4784

mCategory: Tolls and bridge fees

dn: mcode=4789,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 527

mCode: 4789

mCategory: Transportation services - not elsewhere classified

dn: mcode=7511,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 528

mCode: 7511

mCategory: Truck Stop

dn: mcode=7512,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 529

mCode: 7512

mCategory: Automobile rentals

dn: mcode=7513,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 530

mCode: 7513

mCategory: Truck and utility trailer rentals

dn: mcode=7519,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 531

mCode: 7519

mCategory: Motor home and recreational vehicle rentals

dn: mcode=7523,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 532

mCode: 7523

mCategory: Parking lots and garages

dn: mcode=7531,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 533

mCode: 7531

mCategory: Automotive body repair shops

dn: mcode=7534,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 534

mCode: 7534

mCategory: Tyre retreading and repair shops

dn: mcode=7535,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 535

mCode: 7535

mCategory: Automotive paint shops

dn: mcode=7538,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 536

mCode: 7538

mCategory: Automotive service shops (non-dealer)

dn: mcode=7542,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 537

mCode: 7542

mCategory: Car washes

dn: mcode=7549,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 538

mCode: 7549

mCategory: Towing services

dn: mcode=8675,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 539

mCode: 8675

mCategory: Automobile associations

dn: mcode=4812,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 540

mCode: 4812

mCategory: Telecommunication equipment and telephone sales

dn: mcode=4814,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 541

mCode: 4814

mCategory: Telecommunication services, including local and long distance cal

 ls, credit card calls, calls through use of magnetic stripe reading telepho

 nes and faxes

dn: mcode=4815,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 542

mCode: 4815

mCategory: Monthly summary telephone charges

dn: mcode=4816,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 543

mCode: 4816

mCategory: Computer network/information services

dn: mcode=4821,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 544

mCode: 4821

mCategory: Telegraph services

dn: mcode=4829,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 545

mCode: 4829

mCategory: Wire transfers and money orders

dn: mcode=4899,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 546

mCode: 4899

mCategory: Cable and other pay television services

dn: mcode=4900,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 547

mCode: 4900

mCategory: Utilities - electric, gas, water and sanitary

dn: mcode=742,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 548

mCode: 742

mCategory: Veterinary services

dn: mcode=743,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 549

mCode: 743

mCategory: Wine producers

dn: mcode=744,ou=businessTypes,dc=FinoPtaPlus,dc=com

objectClass: businessTypes

objectClass: top

businessTypeUid: 550

mCode: 744

mCategory: Champagne producers

**To add 6\_add\_bussiness\_type\_code.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 6\_add\_bussiness\_type\_code.ldif

![](https://lh7-us.googleusercontent.com/M54eSnlV1QUAZzfT_lUgTID-__tjGpKKX2vET96g4xH19aprCl7VmyqIYMSI1mlm52WLqzAPwMHNCyWid2tl8MYHp25K6tJ0EmL2zryI-EzETHBnXwKn2zdYYROzU0dl14hF2_jzdvKA-x7yTRfvjAE)

**To create 7\_add\_master\_for\_error\_hold\_restrictions.ldif**

-  vim 7\_add\_master\_for\_error\_hold\_restrictions.ldif

![](https://lh7-us.googleusercontent.com/ITG9N-gguKsVXr5-_6056kQsLHkC3Q6MCEq_A_Il3268DtXaRvslV5JyfDfYb1wwIOIwUmviU8yFy3N_VOQo7Vpzy6ymYZCKiaHaJlyAIWqssNRVBvDSsgw0CmCfMPKL6TaexIv1eM24MHMwBXNSt5o)

\# Error master

   

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( errorCode-oid NAME 'errorCode' DESC 'errorCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( errorMessage-oid NAME 'errorMessage' DESC 'errorMessage, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

   

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( errorCodeMasters-oid NAME 'errorCodeMasters' SUP top STRUCTURAL MUST (errorCode $ errorMessage ) MAY ( creator $ createdDate) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\# Hold master

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( holdCode-oid NAME 'holdCode' DESC 'holdCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( holdDescription-oid NAME 'holdDescription' DESC 'holdDescription, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( holdCodeMasters-oid NAME 'holdCodeMasters' SUP top STRUCTURAL MUST (holdCode $ holdDescription $ createdDate ) MAY ( creator ) X-ORIGIN ( 'Fino PtaPlus INFO' 'user defined' ) )

\# Restriction master

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( restrictionCode-oid NAME 'restrictionCode' DESC 'restrictionCode, Integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( restrictionDescription-oid NAME 'restrictionDescription' DESC 'restrictionDescription, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( restrictionCodeMasters-oid NAME 'restrictionCodeMasters' SUP top STRUCTURAL MUST (restrictionCode $ restrictionDescription $ createdDate ) MAY ( creator ) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

\##Account master

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( expiryDate-oid NAME 'expiryDate' DESC 'expiryDate of hold, GeneralizedTime' EQUALITY generalizedTimeMatch  SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( requestType-oid NAME 'requestType' DESC 'requestType, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( amount-oid NAME 'amount' DESC 'amount hold, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( actHoldsDtlsUid-oid NAME 'actHoldsDtlsUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( actHoldsDtls-oid NAME 'actHoldsDtls' SUP top STRUCTURAL MUST (actHoldsDtlsUid $ userId $ holdCode $ amount $ requestType $ accountNo $ createdDate $ expiryDate ) MAY (description $ creator $ member ) X-ORIGIN ( 'Fino PtaPlus INFO' 'user defined' ) )

dn: cn=actHoldsDtlsUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: actHoldsDtlsUid

dnatype: actHoldsDtlsUid

dnafilter: (objectclass=actHoldsDtls)

dnascope: dc=finoPtaPlus,dc=com

dnanextvalue: 1

**To add 7\_add\_master\_for\_error\_hold\_restrictions.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 7\_add\_master\_for\_error\_hold\_restrictions.ldif

![](https://lh7-us.googleusercontent.com/G423Sw3VnRBMf95DMl9FqDJA-hB8cptkotRsNx89GTjiZSXHoE0LuoIK59_TB0dW7X90tgffQ4wa3_q2iqv23NuCcIHPPZPMbwpRxRwTqK2dzFXE5aCBIxKhgUkIzthB4NP_XtsFikv5CBB1dKOcSxo)

**To create 8\_add\_partners.ldif**

-  vim 8\_add\_partners.ldif

![](https://lh7-us.googleusercontent.com/9L9eZTahivBvnLoeJOwwdQgzh9dnTwVrWlT9RGtD-aL299I2Mm_cYiZivhF3tQjNmlAcaXuFosjMQ1dketpSrZlvWuK4bx57dp9KHDnBXs0QfJ5rtxXN39d7-1ZfzM04cuMR2boDHolYxG9iKaQ_sek)

\#partners

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( userName-oid NAME 'userName' DESC 'userName, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( primaryMobile-oid NAME 'primaryMobile' DESC 'primaryMobile,telephone number' EQUALITY telephoneNumberMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( businessName-oid NAME 'businessName' DESC 'businessName, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( primaryAccount-oid NAME 'primaryAccount' DESC 'primaryAccount, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountHolderName-oid NAME 'accountHolderName' DESC 'accountHolderName, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( phoneNumber-oid NAME 'phoneNumber' DESC 'phoneNumber,telephone number 'EQUALITY telephoneNumberMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( gst-oid NAME 'gst' DESC 'gst, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isVerified-oid NAME 'isVerified' DESC 'isVerified, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isShowGLSettlement-oid NAME 'isShowGLSettlement' DESC 'isShowGLSettlement, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isGLAccount-oid NAME 'isGLAccount' DESC 'isGLAccount, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isExternal-oid NAME 'isExternal' DESC 'isExternal, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isRegistered-oid NAME 'isRegistered' DESC 'isRegistered, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isFisSwitch-oid NAME 'isFisSwitch' DESC 'isFisSwitch, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( pan-oid NAME 'pan' DESC 'pan, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( securityStamp-oid NAME 'securityStamp' DESC 'securityStamp, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( twoFactorEnabled-oid NAME 'twoFactorEnabled' DESC 'twoFactorEnabled, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lockoutEnd-oid NAME 'lockoutEnd' DESC 'lockoutEnd, time' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lockoutEnabled-oid NAME 'lockoutEnabled' DESC 'lockoutEnabled, boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accessFailedCount-oid NAME 'accessFailedCount' DESC 'accessFailedCount, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( userStatus-oid NAME 'userStatus' DESC 'userStatus, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( fisUserId-oid NAME 'fisUserId' DESC 'fisUserId, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'fisUserId' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( fisPassword-oid NAME 'fisPassword' DESC 'fisPassword, octetString' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.40 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( fisClientId-oid NAME 'fisClientId' DESC 'fisClientId , IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( fisCustomerNumber-oid NAME 'fisCustomerNumber' DESC 'fisCustomerNumber, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (panImage-oid NAME 'panImage' DESC 'panImage,IA5string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (profileImage-oid NAME 'profileImage' DESC 'profileImage,IA5string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (gstImage-oid NAME 'gstImage' DESC 'gstImage,IA5string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (prefix-oid NAME 'prefix' DESC ' prefix,IA5string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (phoneNumberConfirmed-oid NAME 'phoneNumberConfirmed' DESC ' phoneNumberConfirmed,boolean' SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 EQUALITY booleanMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: (emailConfirmed-oid NAME 'emailConfirmed' DESC ' emailConfirmed,boolean' SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 EQUALITY booleanMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( id-oid NAME 'id' DESC 'id,number' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( createdBy-oid NAME 'createdBy' DESC 'createdBy,string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=id,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: id

dnatype: id

dnafilter: (objectclass=partners)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 8\_add\_partners.ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 8\_add\_partners.ldif

![](https://lh7-us.googleusercontent.com/yurjQwWjXe8fgCuzeWMQr1I8s4sErCFf4UzOn-Fv1qdS1mvR7_UALFgzAcfhAQ6XASlrQ8mgQFqFBsLgadxF72syvlzIuswhVvcLxfiZLnCKgDSde026cJPp1Lwtyw0-sQ6Kxvf3JpVVmcBhAHaU4ts)

**To create 9\_status.ldif**

-  vim 9\_status.ldif

![](https://lh7-us.googleusercontent.com/mrms-DuVlMdFwMFeO7iq8vHXYtrFxxiswvqxtSt_E6BfPnm0NU1CwcX7a1fRmO-y_G1ubfJsBgE4lhYXD-QOr-F9i518i_m6pTN0SZllIZtdHkO7MzdCVBrBGN41sy5XCQIdgbCJfWVolag8J8tGJ_I)

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( statusCode-oid NAME 'statusCode' DESC 'statusCode,string' SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( id-oid NAME 'id' DESC 'id,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( statusMaster-oid NAME 'statusMaster' SUP top STRUCTURAL MUST (id $ statusCode ) MAY ( ) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

**To add 9\_status.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 9\_status.ldif

![](https://lh7-us.googleusercontent.com/16gOBtYRK9c_GwDzDW4Iw5EF2MfFZWw8E8QS2WQVeVW2M3lmCG9xxKZLf1Hm6VqD0LzYBstkImnipNLQNDw-eruJIYizlrNuniBgZD749xItPURuv84PTgB8lEApJDVB8GS9qXbodZLzamM4JOm6xeg)

**To create 10\_Add\_Business\_types.ldif**

-  vim 10\_Add\_Business\_types.ldif

![](https://lh7-us.googleusercontent.com/8SU_Sg99EhZxep6-ewXFndpluncrkzra_e4lYdbgB4kL49fXZiT20kKk9CSuJ7MNO60daZOxmFVtobvixvi_picDITpRB7XxmqbNgLI9ZB75LdduT9qYEtyw6kqL04VDMSe-ziEQZtwDmV7YC7kmL0M)

\#business type

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( mCategory-oid NAME 'mCategory' DESC 'mCategory,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( mCode-oid NAME 'mCode' DESC 'mCode,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( businessTypeUid-oid NAME 'businessTypeUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( businessTypes-oid NAME 'businessTypes' SUP top STRUCTURAL MUST (businessTypeUid $ mCode) MAY (mCategory $ member ) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=businessTypeUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: businessTypeUid

dnatype: businessTypeUid

dnafilter: (objectclass=businessTypes)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 10\_Add\_Business\_types.ldif on ldap server**

-  lldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 10\_Add\_Business\_types.ldif

![](https://lh7-us.googleusercontent.com/a9ZqnW2lP83QvmPSRtXnPMJomnn5L6Wh1d-2Lf5M2MSUiV9wKgcsEahdvrqIAUFhx385LFMraF42SE0yOiGgs-PkZZeRS4m2TY07APouH3SnV0pLlXPc57IWS55hQb6bAuSQQRpEvbQwD75pT0GCqwk)

**To create 11\_Add\_Merchants.ldif**

-  vim 11\_Add\_Merchants.ldif

![](https://lh7-us.googleusercontent.com/jL0AwDutJrGbJ4PLoQqvDMyrtCjTXr1CSxQKx2yn1L4PgWfa02Yyq1n5u-ediAucl3fUrMYS9pb_NoaLqZeGGPVABvM-dx32V-35ihQQI4Zus7T4q7Zg7sZZ4QKlsuHTUZ6tP6SLUOOJ5__lh6zV7-0)

\#merchant

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( mobileNo-oid NAME 'mobileNo' DESC 'mobileNo,telephone number' EQUALITY telephoneNumberMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.50 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( partnerId-oid NAME 'partnerId' DESC 'partnerId,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantStatus-oid NAME 'merchantStatus' DESC 'merchantStatus,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( registrationDateTime-oid NAME 'registrationDateTime' DESC 'registrationDateTime, generalizedTime' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( settlementAccount-oid NAME 'settlementAccount' DESC 'settlementAccount,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( businessName-oid NAME 'businessName' DESC 'businessName of merchant' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isNotification-oid NAME 'isNotification' DESC 'isNotification' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( pinCode-oid NAME 'pinCode' DESC 'pinCode of merchant' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( state-oid NAME 'state' DESC 'state,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( status-oid NAME 'status' DESC 'status,IA5String' EQUALITY  caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountType-oid NAME 'accountType' DESC 'accounttype,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( birthDate-oid NAME 'birthDate' DESC 'birthDate' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( gender-oid NAME 'gender' DESC 'gender' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( franchise-oid NAME 'franchise' DESC 'franchise,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( brand-oid NAME 'brand' DESC 'brand,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( institutionId-oid NAME 'institutionId' DESC 'institutionId of merchant' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( type-oid NAME 'type' DESC 'type,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountPVD-oid NAME 'accountPVD' DESC 'accountPVD,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantCategory-oid NAME 'merchantCategory' DESC 'merchantCategory,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( linkedBankAccount-oid NAME 'linkedBankAccount' DESC 'linkedBankAccount,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( entityType-oid NAME 'entityType' DESC 'entityType,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( statusDateTime-oid NAME 'statusDateTime' DESC 'statusDateTime,IA5String' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( dealerCode-oid NAME 'dealerCode' DESC 'dealerCode,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( tid-oid NAME 'tid' DESC 'terminal identification number,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( mid-oid NAME 'mid' DESC 'merchant identification number,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantId-oid NAME 'merchantId' DESC 'merchantId,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantAggregator-oid NAME 'merchantAggregator' DESC 'merchantAggregator,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantOwnType-oid NAME 'merchantOwnType' DESC 'merchantOwnType,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( sid-oid NAME 'sid' DESC 'Structured Investment Deposit,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( vpaStatus-oid NAME 'vpaStatus' DESC 'vpaStatus,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( id-oid NAME 'id' DESC 'id,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantRefNo-oid NAME 'merchantRefNo' DESC 'merchantRefNo,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( legal-oid NAME 'legal' DESC 'legal,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantType-oid NAME 'merchantType' DESC 'merchantType,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( onBoardingType-oid NAME 'onBoardingType' DESC 'onBoardingType,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantVirtualAddress-oid NAME 'merchantVirtualAddress' DESC 'merchantVirtualAddress,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( merchantGenerate-oid NAME 'merchantGenerate' DESC 'merchantGenerate,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( accountNo-oid NAME 'accountNo' DESC 'accountNo,IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=merchantsUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: merchant uidNumber

dnatype: id

dnafilter: (objectclass=merchants)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 11\_Add\_Merchants.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 11\_Add\_Merchants.ldif

![](https://lh7-us.googleusercontent.com/HVWaQKGRygk3WaZA0pPbWdr-HQOK1JM_0Tj2cBq_sbb5ayVuyeAxhimkWeV5roIQdz_nohHjpAuAgNeVZBCF640VlIjm9EEw9qd8ETgNImf6Dvul07GQw5-_GhmPWmA5KOfeoge68VkTM3yiDDL2V3E)

**To create 12\_Add\_prapluserror\_code.ldif**

-  vim 12\_Add\_prapluserror\_code.ldif

![](https://lh7-us.googleusercontent.com/meqAvEur7IcAXXnPrJLSjuI-ISPEYIDnSItqjecFe5qMeU4N2VfhDU2_Mm8np4eVYf1jxl6KOTXtunpRSSWmkvt2JA1m6atB_FbKUr3jRfOYqzOty0OJ8ndlmoPT6N3bG3u9GjGQ1Hmn9IPtxBe6gY8)

version: 1

dn: PTAErrorcode=100,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: null

ErrorSource: LDAP

HTTPCode: 200

NativeErrorCode: 0

PTAErrorcode: 100

StatusCode: 200

HTTPCodeDescription: Request has succeeded

NativeErrorDescription: The request was successful(Example-Item has been suc

 cessfully added to LDAP )

NativeErrorMessage: LDAP\_SUCCESS

TroubleshootMessage: null

dn: PTAErrorcode=101,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: CONSTRAINT\_VIOLATION

ErrorSource: LDAP

HTTPCode: 406

NativeErrorCode: 19

PTAErrorcode: 101

StatusCode: 200

HTTPCodeDescription: NOT ACCEPTABLE

NativeErrorDescription: Some constraint has been violated(Example- Attribute

  which is marked as MUST, should not be null.)

NativeErrorMessage: LDAP\_CONSTRAINT\_VIOLATION

TroubleshootMessage: null

dn: PTAErrorcode=102,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: ENTRY\_ALREADY\_EXISTS

ErrorSource: LDAP

HTTPCode: 208

NativeErrorCode: 68

PTAErrorcode: 102

StatusCode: 200

HTTPCodeDescription: ALREADY EXISTS

NativeErrorDescription: Entry already present.(Example- DN should be unique)

NativeErrorMessage: LDAP\_ALREADY\_EXISTS

TroubleshootMessage: null

dn: PTAErrorcode=103,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INVALID\_SYNTAX

ErrorSource: LDAP

HTTPCode: 400

NativeErrorCode: 21

PTAErrorcode: 103

StatusCode: 200

HTTPCodeDescription: BAD REQUEST

NativeErrorDescription: An attribute value that is not valid was specified.(

 Input type mismatch, Example-If attribute is of Integer type then input typ

 e should also be of Integer type.)

NativeErrorMessage: LDAP\_INVALID\_SYNTAX

TroubleshootMessage: null

dn: PTAErrorcode=104,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: NO\_SUCH\_OBJECT

ErrorSource: LDAP

HTTPCode: 404

NativeErrorCode: 20

PTAErrorcode: 104

StatusCode: 200

HTTPCodeDescription: NOT FOUND

NativeErrorDescription: The specified object does not exist in the directory

 (No matching record found,Example-Entry which needs to update is absent. )

NativeErrorMessage: NO\_SUCH\_OBJECT

TroubleshootMessage: null

dn: PTAErrorcode=105,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: TIMEOUT

ErrorSource: LDAP

HTTPCode: 504

NativeErrorCode: 55

PTAErrorcode: 105

StatusCode: 200

HTTPCodeDescription: Timed out

NativeErrorDescription: A time limit was exceeded while waiting for a result

 .(No response recieved,LDAP request is made by a client to a server and the

  server does not respond for some reason)

NativeErrorMessage: LDAP\_TIMEOUT

TroubleshootMessage: null

dn: PTAErrorcode=106,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: CONNECT ERROR

ErrorSource: LDAP

HTTPCode: 503

NativeErrorCode: 91

PTAErrorcode: 106

StatusCode: 200

HTTPCodeDescription: CONNECTION ERROR

NativeErrorDescription: The server is temporarily unable to service your req

 uest due to maintenance downtime or capacity problems.(Service temporarily

 unavailable)

NativeErrorMessage: LDAP\_CONNECT\_ERROR

TroubleshootMessage: null

dn: PTAErrorcode=107,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: CHANGE\_NOT\_ALLOWED

ErrorSource: EXCEPTION

HTTPCode: 406

NativeErrorCode: 101

PTAErrorcode: 107

StatusCode: 200

HTTPCodeDescription: Not Acceptable

NativeErrorDescription: Non accessible field.Example- Fields like lastModifi

 edDate,CreatedDate are non accessible field we cannot change it.

NativeErrorMessage: CHANGE\_NOT\_ALLOWED

TroubleshootMessage: null

dn: PTAErrorcode=108,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: NULL\_POINTER\_EXCEPTION

ErrorSource: EXCEPTION

HTTPCode: 500

NativeErrorCode: 102

PTAErrorcode: 108

StatusCode: 200

HTTPCodeDescription: Internal Server Error

NativeErrorDescription:: V2hlbiB3ZSB0cnkgdG8gbW9kaWZ5IHRoZSBmaWVsZCBmb3IgYSB

 udWxsIG9iamVjdCA=

NativeErrorMessage: NULL\_POINTER\_EXCEPTION

TroubleshootMessage: null

dn: PTAErrorcode=109,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: DUPLICATE\_VALUE

ErrorSource: EXCEPTION

HTTPCode: 409

NativeErrorCode: 103

PTAErrorcode: 109

StatusCode: 200

HTTPCodeDescription: Conflict in values

NativeErrorDescription:: V2hlbiB3ZSB0cnkgdG8gZW50ZXIgc2FtZSB2YWx1ZSB3aGljaCB

 pcyBhbHJlYWR5IGluIERCLiA=

NativeErrorMessage: DUPLICATE\_VALUE

TroubleshootMessage: null

dn: PTAErrorcode=110,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: NOT\_IN\_MASTERS

ErrorSource: EXCEPTION

HTTPCode: 404

NativeErrorCode: 104

PTAErrorcode: 110

StatusCode: 200

HTTPCodeDescription: NOT FOUND

NativeErrorDescription: When we try to entry value which is not avaliable in

  masters.Example - Suppose there is a master for typesOfBusiness and if we

 will enter value which is not in master then we get this exception.

NativeErrorMessage: NOT\_IN\_MASTERS

TroubleshootMessage: null

dn: PTAErrorcode=111,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INVALID\_CONTROLS

ErrorSource: EXCEPTION

HTTPCode: 400

NativeErrorCode: 105

PTAErrorcode: 111

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: When we pass wrong controls example- while sending s

 ort key we pass firstName with spelling mistake in that case this happens.

NativeErrorMessage: INVALID\_CONTROLS

TroubleshootMessage: null

dn: PTAErrorcode=112,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INVALID\_ATTRIBUTE\_SYNTAX

ErrorSource: EXCEPTION

HTTPCode: 400

NativeErrorCode: 106

PTAErrorcode: 112

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: Input type mismatch, Example-If attribute is of Inte

 ger type then input type should also be of Integer type.

NativeErrorMessage: INVALID\_ATTRIBUTE\_SYNTAX

TroubleshootMessage: null

dn: PTAErrorcode=113,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: VALIDATION\_FAILURE

ErrorSource: EXCEPTION

HTTPCode: 403

NativeErrorCode: 107

PTAErrorcode: 113

StatusCode: 200

HTTPCodeDescription: Forbidden

NativeErrorDescription: If we have put validation in phone number that it sh

 ould be of 10 digits and user is providing 9 digits value in that case ther

 e will be a validation failure.

NativeErrorMessage: VALIDATION\_FAILURE

TroubleshootMessage: null

dn: PTAErrorcode=114,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage:: SlNPTl9QQVJTSU5HX0VYQ0VQVElPTiA=

ErrorSource: EXCEPTION

HTTPCode: 400

NativeErrorCode: 108

PTAErrorcode: 114

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: Invalid JSON format is given

NativeErrorMessage: JSON\_PARSING\_EXCEPTION

TroubleshootMessage: null

dn: PTAErrorcode=115,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: UNKNOWN\_RESPONSE

ErrorSource: EXCEPTION

HTTPCode: 400

NativeErrorCode: 109

PTAErrorcode: 115

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: Error which is not known

NativeErrorMessage: UNKNOWN\_RESPONSE

TroubleshootMessage: null

dn: PTAErrorcode=116,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: ERR\_CONNECTION\_REFUSED

ErrorSource: EXCEPTION

HTTPCode: 400

NativeErrorCode: 110

PTAErrorcode: 116

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: Using wrong IP address in connection string

NativeErrorMessage: ERR\_CONNECTION\_REFUSED

TroubleshootMessage: null

dn: PTAErrorcode=117,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: AUTH\_KEY\_EXPIRED

ErrorSource: SERVICECALL

HTTPCode: 402

NativeErrorCode: 101

PTAErrorcode: 117

StatusCode: 200

HTTPCodeDescription: time limit exceeded

NativeErrorDescription: Auth key expired

NativeErrorMessage: AUTH\_KEY\_EXPIRED

TroubleshootMessage: null

dn: PTAErrorcode=118,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: SERVICE\_UNAVAILABLE

ErrorSource: SERVICECALL

HTTPCode: 404

NativeErrorCode: 102

PTAErrorcode: 118

StatusCode: 200

HTTPCodeDescription: service not found

NativeErrorDescription: service may not be in running state or wrong endpoin

 t

NativeErrorMessage: SERVICE\_UNAVAILABLE

TroubleshootMessage: null

dn: PTAErrorcode=119,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INTERNAL\_ERROR

ErrorSource: SERVICECALL

HTTPCode: 500

NativeErrorCode: 103

PTAErrorcode: 119

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: Using wrong IP address in connection string

NativeErrorMessage: INTERNAL\_ERROR

TroubleshootMessage: null

dn: PTAErrorcode=120,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: test

ErrorSource: KEYCLOAK

HTTPCode: 402

NativeErrorCode: 101

PTAErrorcode: 120

StatusCode: 200

HTTPCodeDescription: connection refused

NativeErrorDescription: connection refused

NativeErrorMessage:: Y29ubmVjdGlvbiByZWZ1c2VkIA==

TroubleshootMessage: null

dn: PTAErrorcode=121,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: test

ErrorSource: KEYCLOAK

HTTPCode: 402

NativeErrorCode: 401

PTAErrorcode: 121

StatusCode: 200

HTTPCodeDescription: Authentication Failure

NativeErrorDescription: invalid userName or password

NativeErrorMessage: INVALID\_LOGIN\_CREDENTIALS

TroubleshootMessage: null

dn: PTAErrorcode=122,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: test

ErrorSource: KEYCLOAK

HTTPCode: 404

NativeErrorCode: 404

PTAErrorcode: 122

StatusCode: 200

HTTPCodeDescription: Not Found

NativeErrorDescription: invalid endpoint

NativeErrorMessage: NOT\_FOUND

TroubleshootMessage: null

dn: PTAErrorcode=123,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: test

ErrorSource: KEYCLOAK

HTTPCode: 400

NativeErrorCode: 400

PTAErrorcode: 123

StatusCode: 200

HTTPCodeDescription: Bad Request

NativeErrorDescription: invalid request

NativeErrorMessage: BAD\_REQUEST

TroubleshootMessage: null

dn: PTAErrorcode=124,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: test

ErrorSource: KEYCLOAK

HTTPCode: 500

NativeErrorCode: 500

PTAErrorcode: 124

StatusCode: 200

HTTPCodeDescription: internal error

NativeErrorDescription: invalid request

NativeErrorMessage: INTERNAL\_ERROR

TroubleshootMessage: null

dn: PTAErrorcode=125,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INVALID\_CREDENTIALS

ErrorSource: LDAP

HTTPCode: 401

NativeErrorCode: 401

PTAErrorcode: 125

StatusCode: 200

HTTPCodeDescription: UNAUTHORIZED

NativeErrorDescription: request rejected due to incorrect passwords

NativeErrorMessage: INVALID\_CREDENTIALS

TroubleshootMessage: null

dn: PTAErrorcode=126,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: OBJECT\_CLASS\_VIOLATION

ErrorSource: LDAP

HTTPCode: 406

NativeErrorCode: 65

PTAErrorcode: 126

StatusCode: 200

HTTPCodeDescription: NOT ACCEPTABLE

NativeErrorDescription: Some majority attribute missing

NativeErrorMessage: OBJECT\_CLASS\_VIOLATION

TroubleshootMessage: null

dn: PTAErrorcode=127,ou=ptapluserrorcode,dc=FinoPtaPlus,dc=com

objectClass: errorcodeptaplus

objectClass: top

ErrorMessage: INSUFFICIENT\_ACCESS\_RIGHTS

ErrorSource: LDAP

HTTPCode: 403

NativeErrorCode: 403

PTAErrorcode: 127

StatusCode: 200

HTTPCodeDescription: INSUFFICIENT\_ACCESS\_RIGHTS

NativeErrorDescription: request rejected due to insufficient accress rights

NativeErrorMessage: INSUFFICIENT\_ACCESS\_RIGHTS

TroubleshootMessage: null

**To add 12\_Add\_prapluserror\_code.ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 12\_Add\_prapluserror\_code.ldif

![](https://lh7-us.googleusercontent.com/mCSOYI2ToNVoY9LHHPlZ9et3sxIlB4hY_lKeTRMHLl17CrgZlYqfT92sKRmlA8Gc83Pcqdt1yrEXqErQHFjGO1ckXgfStfaK1n8WkRaBXvnciR62TI0Zm3Ff0IppqZyMFrltl6E7n8gv3W1QOy4GHcI)

**To create 13\_Add\_transaction\_Groups\_And\_Transaction\_Types.ldif**

-  vim 13\_Add\_transaction\_Groups\_And\_Transaction\_Types.ldif

![](https://lh7-us.googleusercontent.com/mgDGZqEEXdnveMgj4cQsGTr-_u27Exv_eQdJpehFCS0r01_0uAQ9P_Gj3LUoFpbqB3N4-v-2YpcDfS5_7pwZteknB9TzxZJZFqsc4fVSRN2VJOMSzSBtoCWm2enOSZvRBsIppeSqUEwm--kSJ5JoU9s)

\# 4.transaction Group

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( transactionGroupId-oid NAME 'transactionGroupId' DESC 'transactionGroupId, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( transactionGroupsUid-oid NAME 'transactionGroupsUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( transactionGroups-oid NAME 'transactionGroups' SUP top STRUCTURAL MUST (transactionGroupsUid $ createdDate $ creator $ isActive $ lastActivationUser $ lastActivationDate $ description $ transactionGroupId) MAY ( member) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=transactionGroupsUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: transactionsGroupsUid

dnatype: transactionGroupsUid

dnafilter: (objectclass=transactionGroups)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

\# 5.transaction type

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( transactionType-oid NAME 'transactionType' DESC 'transactionType, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( transactionTypeName-oid NAME 'transactionTypeName' DESC 'transactionTypeName, IA5String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( transactionTypeUid-oid NAME 'transactionTypeUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( transactionTypes-oid NAME 'transactionTypes' SUP top STRUCTURAL MUST (transactionTypeUid $ transactionTypeName  $ createdDate $ creator $ isActive $ lastActivationUser $ lastActivationDate $ description $ transactionType) MAY (member) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=transactionTypesUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: transactionTypeUid

dnatype: transactionTypeUid

dnafilter: (objectclass=transactionTypes)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 13\_Add\_transaction\_Groups\_And\_Transaction\_Types.ldif**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 13\_Add\_transaction\_Groups\_And\_Transaction\_Types.ldif

![](https://lh7-us.googleusercontent.com/vdl1mSFPCtVVBMhqe6FJvXPcDJVpm3lOr0F3gCif9wUY8v6IILvYA6WfNyn9nQUqbmDUmGZUIcW00IahO_c9i5KBtQOlWqo2Hbc_wiZj1lL8TPcneLla_6lkPcrhm5GFhYOvZtSo_IKwVqwNq86ZlqU)

**To create 14\_Add\_banks.ldif**

-  vim 14\_Add\_banks.ldif

![](https://lh7-us.googleusercontent.com/DJFEGpJ-yQl9vE48hlxfiUAVRbaa71sNMCEUCuKlyOWJiL5b0Z_q8BWLm85rFAKBPeI05HQSwHMFlGEDiqeEevAkAgdFy-KmD4SNtrDdgdx4UMiSbK7HnfeTZugovDTbcTW8uteI44U6AEvPAdWNwBg)

\# banks

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isActive-oid NAME 'isActive' DESC 'isActive,boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( verifyStatus-oid NAME 'verifyStatus' DESC 'verifyStatus,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( authTypeId-oid NAME 'authTypeId' DESC 'authTypeId,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isVerifyMandatory-oid NAME 'isVerifyMandatory' DESC 'isVerifyMandatory,boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aadharPay-oid NAME 'aadharPay' DESC 'aadharPay,boolean' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( impsStatus-oid NAME 'impsStatus' DESC 'impsStatus,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( defaultIIFSCCode-oid NAME 'defaultIIFSCCode' DESC 'defaultIIFSCCode,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( defaulIFSCStatus-oid NAME 'defaulIFSCStatus' DESC 'defaulIFSCStatus,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( impsnbin-oid NAME 'impsnbin' DESC 'impsnbin,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepsStatus-oid NAME 'aepsStatus' DESC 'aepsStatus,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( nbin-oid NAME 'nbin' DESC 'National Bank Identification Number,integer' EQUALITY  integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( nbinStatus-oid NAME 'nbinStatus' DESC 'nbinStatus,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepSbankOrder-oid NAME 'aepSbankOrder' DESC ' Aadhaar Enabled Payment System bankOrder,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepsIcon-oid NAME 'aepsIcon' DESC ' Aadhaar Enabled Payment System Icon,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepsBalStatus-oid NAME 'aepsBalStatus' DESC ' Aadhaar Enabled Payment System BalStatus,string ' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( systemDecision-oid NAME 'systemDecision' DESC 'systemDecision,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( routeId-oid NAME 'routeId' DESC 'routeId,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( routeIDBE-oid NAME 'routeIDBE' DESC 'routeIDBE,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepsMinisStatus-oid NAME 'aepsMinisStatus' DESC 'aepsMinisStatus,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( beneAmount-oid NAME 'beneAmount' DESC 'beneAmount,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( beneVerify-oid NAME 'beneVerify' DESC 'beneVerify,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aepsCashDStatus-oid NAME 'aepsCashDStatus' DESC 'aepsCashDStatus,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aadharPayStatus-oid NAME 'aadharPayStatus' DESC 'aadharPayStatus,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( defaultIFSCStatus-oid NAME 'defaultIFSCStatus' DESC 'defaultIFSCStatus,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( banksUid-oid NAME 'banksUid' DESC 'banksUid,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( banks-oid NAME 'banks' SUP top STRUCTURAL MUST (banksUid $ ifsc $ bankName $ isActive $ verifyStatus $ authTypeId $ isVerifyMandatory $ aadharPay ) MAY (id $ impsStatus $ defaultIIFSCCode $ defaultIFSCStatus $ impsnbin $ aepsStatus $ nbin $ nbinStatus $ aepSbankOrder $ aepsIcon $ aepsBalStatus $ systemDecision $ routeId $ routeIDBE $ aepsMinisStatus $ beneAmount $ beneVerify $ aepsCashDStatus $ aadharPayStatus $ member) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=finobanksUid,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: banksUid

dnatype: banksUid

dnafilter: (objectclass=banks)

dnascope: dc=finoPtaPlus,dc=com

dnanextvalue: 1

**To add 14\_Add\_banks.ldif. on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 14\_Add\_banks.ldif

![](https://lh7-us.googleusercontent.com/6GYB-GudxToVD6ore3zzcc55ltAiOyogtnvtHA-GR-pY5v1RtXzUflhZA_yC9PWmcaJ6cKg_W5Rcv88sOYA5nEosYO-YnFoWFjHj43OxzZ79gZPxIgbLbvglkKvmPcnay9AhciX7Jpw5Np_v6YePfaA)

**To create 15\_Add\_glsfinal.ldif**

-  vim 15\_Add\_glsfinal.ldif

![](https://lh7-us.googleusercontent.com/PWZXffPJWlgS22OipxFF2R2Y5_NJ881xQwmXUvLQ1uaofUuVi3V6iNtoKcU4VfZGftD_pQuPbrvtdb-sxc___TqPUsvPxjy3TUOjP_w2qt_eGwFAf2xU_dBph9GQ5dDRf3DX6XrMOoowABinu64rxMo)

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isDormant-oid NAME 'isDormant' DESC 'Is Entity Active' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glNumber-oid NAME 'glNumber' DESC 'GL Number' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( cbsMirrorGLcode-oid NAME 'cbsMirrorGLcode' DESC 'GL Number' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( bscDesc-oid NAME 'bscDesc' DESC 'Branch Description' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( cbsCustomerId-oid NAME 'cbsCustomerId' DESC 'Partner Customer ID in CBS' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glEntry-oid NAME 'glEntry' DESC 'GL Entry' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glDept-oid NAME 'glDept' DESC 'GL Department' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( bscCode-oid NAME 'bscCode' DESC 'Branch Description Code' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( pcCode-oid NAME 'pcCode' DESC 'PC Code' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( pcName-oid NAME 'pcName' DESC 'PC Name' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( spcCode-oid NAME 'spcCode' DESC 'SPC Code' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( spcName-oid NAME 'spcName' DESC 'SPC Name' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( sbucCode-oid NAME 'sbucCode' DESC 'SBUC Code' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( sbucName-oid NAME 'sbucName' DESC 'SBUC Name' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glRunningSequence-oid NAME 'glRunningSequence' DESC 'GL Running Sequence' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isActive-oid NAME 'isActive' DESC 'Is Entity Active' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( creationDate-oid NAME 'creationDate' DESC 'Entity Creation Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( creator-oid NAME 'creator' DESC 'The user that created the Entity,DN' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastActivationDate-oid NAME 'lastActivationDate' DESC 'Entity Last Activation Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastActivationUser-oid NAME 'lastActivationUser' DESC 'The user that last Activated the PtaPartner' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isGLrestricted-oid NAME 'isGLrestricted' DESC 'Is GL Restricted' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isFullySettledatEoD-oid NAME 'isFullySettledatEoD' DESC 'Does the GL have to be settled fully at EoD' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isFullyTransferredatSoD-oid NAME 'isFullyTransferredatSoD' DESC 'Does the GL have to be transferred fully at SoD' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isLienAppliedAtEoD-oid NAME 'isLienAppliedAtEoD' DESC 'Do Lien Calculations apply at EoD' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( isClosed-oid NAME 'isClosed' DESC 'Is GL Closed' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( activationAuditTrail-oid NAME 'activationAuditTrail' DESC 'activationAuditTrail' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( partnerLastDeActivationDate-oid NAME 'partnerLastDeActivationDate' DESC 'Partner Last Deactivation Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lastDeActivationUser-oid NAME 'lastDeActivationUser' DESC 'The user that last Deactivated the Entity' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( deactivationAuditTrail-oid NAME 'deactivationAuditTrail' DESC 'deactivationAuditTrail' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glLastRestrictionApplyDate-oid NAME 'glLastRestrictionApplyDate' DESC 'GL Last Restriction Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glLastRestrictionApplyUser-oid NAME 'glLastRestrictionApplyUser' DESC 'The user that last Restricted the GL' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glRestrictionApplyAuditTrail-oid NAME 'glRestrictionApplyAuditTrail' DESC 'Account Previous Restriction Removal Date/Time, User and RestrictionId' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glLastRestrictionRemovalDate-oid NAME 'glLastRestrictionRemovalDate' DESC 'Account Last Restriction Removal Date' SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glLastRestrictionRemovalUser-oid NAME 'glLastRestrictionRemovalUser' DESC 'The user that last Removed Restriction from the Account' SYNTAX 1.3.6.1.4.1.1466.115.121.1.12 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( glMinBalanceFixed-oid NAME 'glMinBalanceFixed' DESC 'Fixed Minimum Balance Amount' EQUALITY caseIgnoreMatch SUBSTR caseIgnoreSubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.15 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( id-oid NAME 'id' DESC 'id Number' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( finoPtaPlusGl-oid NAME 'finoPtaPlusGl' SUP top STRUCTURAL MUST ( id $ glNumber $ description $ cbsMirrorGLcode $ cbsCustomerId $ glEntry $ glDept $ bscCode $ bscDesc $ pcCode $ pcName $ spcCode $ spcName $ sbucCode $ sbucName $ glRunningSequence $ isActive $ creationDate $ creator $ isGLrestricted ) MAY ( isFullySettledatEoD $ isFullyTransferredatSoD $ isLienAppliedAtEoD $ isClosed $ activationAuditTrail $ lastDeActivationDate $ lastDeActivationUser $ deactivationAuditTrail $ glLastRestrictionApplyDate $ glLastRestrictionApplyUser $ isDormant $ glRestrictionApplyAuditTrail $ glLastRestrictionRemovalDate $ glLastRestrictionRemovalUser $ glMinBalanceFixed $ lastActivationDate $ lastActivationUser ) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=idgls,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: idgls

dnatype: id

dnafilter: (objectclass=finoPtaPlusGl)

dnascope: dc=FinoPtaPlus,dc=com

dnanextvalue: 1

**To add 15\_Add\_glsfinal.ldif on ldap server**

-  ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 15\_Add\_glsfinal.ldif

![](https://lh7-us.googleusercontent.com/3v9V7smLqGW4cwV6Yx4wvmRRI3dk2cLBGxtXePP7fxav9KnRwukQuYMIRnd0cfHR7DE_ECIsoiyYFFM_Yn88vlF_zmNwjUFqiiNFEHcD9Qzq2b4lfcpT0vmfw1DjuNGh-LJchuF4p9AfZJ7ee2gw0qo)

**To create 16\_Add\_status.ldif**

-  vim 16\_Add\_status.ldif

![](https://lh7-us.googleusercontent.com/J8VUpPcY1o1Ljh2bQ4Da_8F8NgJzXgjB7Vra8SpzO83dgRGOSjySgaT86c7rxq0krhUhK34Wyry8c2uJb0VOhwdACSkpqeTsmGWg0OWWkfMV1YC1Hq13laubRZsbb0Xt2Ak2XtqviwJo32A_6MsBZU8)

\#state

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( stateCode-oid NAME 'stateCode' DESC 'stateCode,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'stateCode' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( stateName-oid NAME 'stateName' DESC 'stateName,String' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'stateName' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( stateId-oid NAME 'stateId' DESC 'stateId,integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( countryCode-oid NAME 'countryCode' DESC 'countryCode,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( createdBy-oid NAME 'createdBy' DESC 'createdBy,stringIA5' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( updatedDate-oid NAME 'updatedDate' DESC 'updatedDate' EQUALITY generalizedTimeMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( orderId-oid NAME 'orderId' DESC 'orderId' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( gstStateCode-oid NAME 'gstStateCode' DESC 'gstStateCode,string' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lomState-oid NAME 'lomState' DESC 'lomState' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( lomStateNumericId-oid NAME 'lomStateNumericId' DESC 'lomStateNumericId of bank' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( aadharFlag-oid NAME 'aadharFlag' DESC 'aadharFlag' EQUALITY booleanMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.7 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( weightAge-oid NAME 'weightAge' DESC 'weightAge of bank' EQUALITY caseIgnoreIA5Match SUBSTR caseIgnoreIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: attributetypes

attributetypes: ( stateUid-oid NAME 'stateUid' DESC 'integer' EQUALITY integerMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 SINGLE-VALUE X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=schema

changetype: modify

add: objectclasses

objectclasses: ( states-oid NAME 'states' SUP top STRUCTURAL MUST (stateUid $ stateCode $ stateName $ countryCode ) MAY ( stateId $ description $ createdDate $ createdBy $ updatedDate $ orderId $ gstStateCode $ lomState $ lomStateNumericId $ aadharFlag $ weightAge $ member) X-ORIGIN ( 'Fino PtaPlus' 'user defined' ) )

dn: cn=CUIDnumberPtaPlusstates,cn=Distributed Numeric Assignment Plugin,cn=plugins,cn=config

objectClass: top

objectClass: extensibleObject

cn: CUID numbers

dnatype: stateUid

dnafilter: (objectclass=states)

dnascope: dc=finoPtaPlus,dc=com

dnanextvalue: 1

**To add 16\_Add\_status.ldif on ldap server**

- ldapadd -a -c -x -H ldap\://localhost:3389 -D "cn=Directory Manager" -W -f 16\_Add\_status.ldif


# Step 3

**Create connection apache directory studio with openldap server** 

To install apache directory studio

Click link below and download file

<https://directory.apache.org/studio/download/download-linux.html>

cd Download/

![](https://lh7-us.googleusercontent.com/yjMAZZJpxqC_09PqCn_p9mXGjp4nozmXFHpc2yPr6GiJY9nBYt_7sCE62KAGg2AP-Xb0AqMPwYuW0NN58GqsUZtH3fBIEM2XLpjt4n4df0VNopv5AE6v03SZi1LzWqcitlMYyReBoYN5pEKtbPpVZaY)

tar -zxvf ApacheDirectoryStudio-2.0.0.v20210717-M17-linux.gtk.x86\_64.tar.gz

![](https://lh7-us.googleusercontent.com/V0ZudBJ30D8gunjGGGRlrWHnA5wocF1UxjLGCWlSQhpc-El3T3pgf4GZk9M_rms3rU2rXMjcjBnp57NwFEk1777LGmF0EAJ9s5-EBSUJ3oB3PkylBsR1MXhvMi6r8cGmOg17uZzxzkZ2VoGdPslnXvo)

sudo mv ApacheDirectoryStudio-\* /opt/

sudo ln -s /opt/ApacheDirectoryStudio\*/ApacheDirectoryStudio /usr/local/bin/ApacheDirectoryStudio

sudo apt-get install openjdk-11-jre

![](https://lh7-us.googleusercontent.com/s6VqkN5xYlL35n5xxxIBWQF_Kz5rre_RPIeoo6G-FFTTG6-xdE4eZ3Gi5gEEFeHdobh01bxQDkJJiGiXGRTqHc7Y9FKodUZ6juumDmfuEMh3p-pcrQh2l8LNUHN8o4iSmxzH4AUeYqUwsbPxp6kJYAQ)

cd ApacheDirectoryStudio/

./ApacheDirectoryStudio

![](https://lh7-us.googleusercontent.com/OoTbGSS3Lt9tRNJz08YMmlSsUrXscHaVixs5VAog-NX8KySHZ646kMSyDTTyncOXsicoUpX0aZXphZLdHBnCzu6CT1pfcuRIuFgY57yHjPyMzJ5IuStik-p-6HNbUydTpQinPFWouJkxFUxrvDfYg_0)

Now start your apache directory studio

![](https://lh7-us.googleusercontent.com/hgrfQzBffiSW2Rf3amnmQqCzJ6nH6aPFDiU8IZdTCFsPs2KfEFocZaMN8iM2MCKAaMmWNjPS8hb8P3U0lxpVeOa_5E68JKTOG2m4JcLZVIu0UugHr7NCFry2h390-GdYZ_Q8pttsa1QiaXGTdSC8_ZE)

Click Ldap button after that Click New Connection

![](https://lh7-us.googleusercontent.com/VbCceVyfIl0LeLMQpLQbXhbZbrs9_pGFKNV57n8VmwEzMBUHI0PH82XchcnDIrqVSWhVjwBz_-ep6gmZalWojqtyzpRpWTQ9YO6y1DPmi9TIZBHGlxJ_n6IgqR_GxtvxVOq-xHct4YwcRowkwW9UQ8Y)

Fill the parameters

![](https://lh7-us.googleusercontent.com/uR-GfmwLVmfQuVXzTnDsYhEWsRLJvfPLYZmdXVsJJPg-1vhnT18ISxqJeaEEB247VnxrkvosdrstmlxJ8jH26REw4_KxiiBU34voQlUjTTFUHAAnNEctzDq9GhEVuCKXtmNmqdHZkj-2Aiodr_7rzO8)

![](https://lh7-us.googleusercontent.com/5gOTL5CGYfohLve9o421o4gPT_mTChPaUsP83RFZ1i7FksbNiyG3zszm_hLXrmjVXu5_csjx-QTzyQPvzhFjmalCNy9VyMEBs5rwLgYA16w3FQ5FIElBbpZFoB-oU29KAd9ypOUPczL7br-P72FoV2Y)

![](https://lh7-us.googleusercontent.com/dzuejIYeiE92aq7bDfoElj2Np9JhX4DNTYS8KD4ef0IBPlpaUoTtDU-PSo5yJf21IhUP_TfTl4AmwjCqeaX8pJHVBK09ActSj5wfy1G2IoiJJNta3jXs4Jw02CiFFUcroh2BOBTEKS8sKBzBA7EG67E)

When you see dc=finoptaplus,dc=com. Now your ldif file is configured successfully.

That means your setup is successful.
