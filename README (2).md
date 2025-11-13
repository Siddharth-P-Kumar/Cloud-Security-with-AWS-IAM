<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** siddharthpk nextwork  
**Email:** siddharthpknextwork@gmail.com

---

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

In this project, I will demonstrate how to set up and manage EC2 instances, IAM policies, users, groups, and configure an AWS account alias.I'm doing this to deepen my hands-on understanding of AWS services and improve my cloud infrastructure skills.

### Tools and concepts

Services I used were EC2, IAM, and Account Alias. Key concepts I learnt include launching and tagging EC2 instances, creating IAM policies, managing user groups, and controlling access using JSON policies.


### Project reflection

This project took me approximately 2 hours to complete. The most challenging part was writing and testing the IAM policy correctly. It was most rewarding to see the access control work as expected and understand how IAM enhances AWS security.

---

## Tags

✍️  Tags are key-value pairs that you can assign to AWS resources. They are useful for organizing, identifying, and managing resources more easily. Tags help with cost tracking, automation, access control, and quickly locating specific resources.

The tag I’ve used on my EC2 instances is called Env. The values I’ve assigned for my instances are production and development, to help distinguish their purpose and manage them more effectively.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

IAM Policies are creates  a rule for who can do what with your AWS resources. It's all about giving permissions to IAM users, groups, or roles, saying what they can or can't do on certain resources, and when those rules kick in.

### The policy I set up

For this project, I’ve set up a policy using JSON.

I’ve created a policy that allows some actions (like starting, stopping, and describing EC2 instances) for instances tagged with "Env = development" while denying the ability to create or delete tags for all instances.

### When creating a JSON policy, you have to define its Effect, Action and Resource.

Effect defines if the action is allowed or denied. Action lists what actions are permitted or blocked (e.g., `"ec2:*"` allows all EC2 actions). Resource specifies which resources the policy applies to, like a specific instance or `"*"` for all.

---

## My JSON Policy

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_1c864649)

---

## Account Alias

An account alias is is a friendly name for your AWS account that you can use instead of your account ID (which is usually a bunch of digits) to sign in to the AWS Management Console.

Creating an account alias took me just a few moments. Now, my new AWS console sign-in URL is:
https://nextwork-alias-sidak.aws.amazon.com/console

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### Users

IAM users are individual identities created in AWS to represent a person or application. Each IAM user has unique credentials and permissions, allowing secure and controlled access to AWS resources.


### User Groups

IAM user groups are collections of IAM users that share the same permissions. Instead of assigning permissions to users individually, you can assign them to a group, making it easier to manage access for multiple users with similar roles.


I attached the policy I created to this user group, which means all users in the group now have the permissions defined in the policy—such as access to the development EC2 instance—making it easier to manage and enforce consistent access controls.


---

## Logging in as an IAM User

The first is to **email the user's sign-in credentials**, including their username, password, and the AWS sign-in URL.

The second is to **download the credentials as a .csv file** and share it securely with the user.


Once I logged in as my IAM user, I noticed the AWS console treats you as starting from scratch. This was because IAM users have separate settings and don’t inherit the console preferences of the root or other users.


![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

I tested my JSON IAM policy by trying to access both EC2 instances. I was able to connect to the development instance but was denied access to the production one, confirming that the policy works as intended.

### Stopping the production instance

When I tried to stop the production instance  a banner tells us we've failed to stop this instance.  This was because we're not authorized! We don't have permission to stop any instance with the production tag.

![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_0e7a9d6a)

---

## Testing IAM Policies

### Stopping the development instance

Next, when I tried to stop the development instance, the action was successful. This was because the IAM policy I created allows full EC2 access specifically for the development instance.


![Image](http://learn.nextwork.org/mischievous_red_fierce_pony/uploads/aws-security-iam_1811801c)

---

## The IAM Policy Simulator

### How I used the simulator

---

---
