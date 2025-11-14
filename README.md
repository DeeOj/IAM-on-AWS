# PROJECT: Identity and Access Management on AWS

## Introduction

In any cloud environment, controlling access to resources is a critical security measure. Misconfigured permissions or unrestricted access can lead to accidental deletion, unauthorized modification, or even data breaches.
This project demonstrates how the AWS Identity and Access Management (IAM) service can be used to enforce the principle of least privilege by defining who can access or modify specific AWS resources, particularly EC2 instances.


## Objective
Configure AWS IAM to securely manage user access, define permissions through policies, and verify that only authorized users can modify or delete key AWS resources


## Overview of Task

The project involved setting up a small, controlled AWS environment to simulate real-world access control scenarios. Two EC2 instances were launched,one representing a development environment and another a production environment.

A custom IAM policy was created to restrict specific users from performing sensitive operations, such as terminating production instances. An IAM user group was configured and the policy was attached to the this group.

New IAM users were created and added to the group, two new junior dev hires. Each user’s login was tested to confirm that they could access the AWS Management Console using their assigned credentials. On first login, users were required to reset their passwords, reinforcing account security best practices.

To ensure the IAM policies worked as intended, the AWS Policy Simulator tool was used to test and validate what actions were permitted or denied for these users in the group. This confirmed that restrictions applied correctly and that only authorized users retained full administrative privileges.

## Task Diagram

## Procedure

- Deployed two EC2 instances, one for the development environment and the other for production environment.

<p align="center">
<img src="https://imgur.com/NXZkT2Q.jpg" height="90%", width="90%">
</p>

-- Production tag (a label I assigned to this AWS instance with name "Environment" and value "production" which will aid in my policy creatiom)
  
<p align="center">
<img src="https://imgur.com/xVdGOw5.jpg" height="90%", width="90%">
</p>

- Development tag (Same concept, with value "development")
 
<p align="center">
<img src="https://imgur.com/q0jcP7X.jpg" height="90%", width="90%">
</p>

- Creating policy

This allows any actions that can be possibly taken on an EC2 instance, where the resource is conditioned by a tag "development". So they (new IAM users) can perform any actions in the development environment, they can edit, and even stop EC2 instances.

Furthermore, they are denied certain actions such as "DeleteTags" and "CreateTags" in any resource.

<p align="center">
<img src="https://imgur.com/UEAxrRm.jpg" height="90%", width="90%">
</p>

- Review of policy.
  
<p align="center">
<img src="https://imgur.com/MO3YFpr.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/UyO9Q8k.jpg" height="90%", width="90%">
</p>

- Created the User group and attached the policy created to it.

<p align="center">
<img src="https://imgur.com/vFV94UP.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/WT6ecmh.jpg" height="90%", width="90%">
</p>

- User group created, with no users yet.
<p align="center">
<img src="https://imgur.com/o4NyO59.jpg" height="90%", width="90%">
</p>

-  Created IAM users, and ensured they changed their passwords on their first login. Also, added them to the IAM user group earlier created.
  
<p align="center">
<img src="https://imgur.com/XxKNqaL.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/VLeFkNP.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/taaDa9c.jpg" height="90%", width="90%">
</p>


- Testing User credentials
  
<p align="center">
<img src="https://imgur.com/OAfUNvi.jpg" height="90%", width="90%">
</p>

- The user is prompted to change their passwords, enhancing security.
  
<p align="center">
<img src="https://imgur.com/5ysgpHw.jpg" height="90%", width="90%">
</p>

<p align="center">
<img src="https://imgur.com/iSaR8kG.jpg" height="90%", width="90%">
</p>

- Utilized Policy simulator tool to check the policy functions as it should.
  
<p align="center">
<img src="https://imgur.com/GI3Ok2Q.jpg" height="90%", width="90%">
</p>

- Selected the Actions that make up the rules in the IAM policy.
  
<p align="center">
<img src="https://imgur.com/WAeEAeV.jpg" height="90%", width="90%">
</p>

- In the policy, it is defined that these users are permitted any action but "DeleteTags" and "CreateTags" in the Development environment, and that reflects in this simulation result. 
  
<p align="center">
<img src="https://imgur.com/8i6RZgV.jpg" height="90%", width="90%">
</p>

- In the Production, they are even more restricted, as they are denied the ability of stopping EC2 instances.
  
<p align="center">
<img src="https://imgur.com/o50SYZ1.jpg" height="90%", width="90%">
</p>

