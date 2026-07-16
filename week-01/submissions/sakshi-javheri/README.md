# Week 01 Submission

AWS Zero to Hero – Week 1
Overview

In Week 1, I explored the fundamentals of AWS Identity and Access Management (IAM), the AWS Shared Responsibility Model, GitHub OIDC integration, and AWS User Notifications. I also performed hands-on exercises to understand how secure access management works in AWS.

1. AWS User Notification Configuration
Objective

Configured an AWS Notification Configuration to receive alerts whenever specific events or requests occur.

What I Did
Created a notification configuration named Notifyme.

Added the description:

Notify me when request comes

Verified that the notification status is Active.
Outcome

This configuration enables AWS to send notifications for selected events, helping monitor account activity efficiently.

2. IAM User Groups
Objective

Learned how IAM Groups simplify permission management by assigning policies to groups instead of individual users.

What I Did

Created three IAM Groups:

Group Name	Purpose
Billing	Manage billing-related permissions
Devops	Administrative and infrastructure management
Monitoring	Monitoring AWS resources and services
Outcome

Grouping users makes permission management easier and follows AWS security best practices.

3. IAM Users
Objective

Created IAM Users to practice identity management and access control.

What I Did

Created three IAM Users:

Billing
Devops
Monitoring

Each user was assigned to its respective IAM Group.

Outcome

Each user inherits permissions from the assigned IAM Group, reducing manual permission assignments.

4. IAM Policies
Objective

Understood how AWS IAM Policies define permissions.

What I Configured

AdministratorAccess

Attached through the Devops IAM Group.
Grants full administrative access to AWS resources.

IAMUserChangePassword

Attached directly to the IAM User.
Allows users to change their own passwords securely.
Outcome

Learned the difference between:

Group-based permissions
User-specific permissions
5. GitHub OIDC Identity Provider
Objective

Integrated GitHub with AWS using OpenID Connect (OIDC) to enable secure authentication without storing AWS credentials.

What I Did
Added GitHub as an Identity Provider.

Provider URL:

token.actions.githubusercontent.com

Provider Type:

OpenID Connect (OIDC)
Outcome

This setup allows GitHub Actions to securely assume IAM Roles using temporary credentials instead of long-term access keys.

6. IAM Role Trust Policy
Objective

Configured an IAM Role Trust Policy to allow GitHub Actions to assume an AWS IAM Role.

What I Configured

The Trust Policy includes:

OIDC Identity Provider ARN
sts:AssumeRoleWithWebIdentity

Audience (aud)

sts.amazonaws.com

Repository restrictions (sub)

repo:<GitHub-username>/*
Outcome

Only workflows from the specified GitHub repository can assume this IAM Role, improving security by restricting unauthorized access.

Key Concepts Learned
AWS IAM

IAM (Identity and Access Management) enables secure control over access to AWS services by managing users, groups, roles, and permissions.

IAM Groups

Groups help manage permissions collectively by assigning policies once and allowing all group members to inherit them.

IAM Policies

Policies are JSON documents that specify what actions users, groups, or roles are allowed or denied to perform.

OpenID Connect (OIDC)

OIDC is an authentication protocol that enables GitHub Actions to securely access AWS resources without storing permanent AWS credentials.

IAM Roles

IAM Roles provide temporary credentials that applications, services, or users can assume to access AWS resources securely.

AWS Shared Responsibility Model

AWS security responsibilities are divided between AWS and the customer.

AWS is responsible for:
Physical data centers
Networking infrastructure
Hardware
Global cloud infrastructure
Customers are responsible for:
IAM Users and Roles
Security configurations
Data protection
Application security
Operating system updates (where applicable)
