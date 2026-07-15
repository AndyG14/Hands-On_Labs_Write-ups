# Lab Title: AWSRaid Lab

**Platform:** Cyberdefenders
**Category:** Cloud Security / Log Analysis 

---

## Objective

This lab introduces the use of AWS CloudTrail and Splunk for cloud security investigations. The investigation focuses on identifying unauthorized access, analyzing configuration changes, and detecting persistence techniques used by an attacker.

---

## Skills Demonstrated

- AWS CloudTrail Log Analysis
- Splunk Log Investigation
- Cloud Incident Response

---

## Tools Used

- Splunk

---

## Scenario

Your organization utilizes AWS to host critical data and applications. An incident has been reported that involves unauthorized access to data and potential exfiltration. The security team has detected unusual activities and needs to investigate the incident to determine the scope of the attack.

## Methodology

Given the scenario, my first objective was to identify an unauthorized access through a compromised account.

To achieve this, I started by analyzing the **AWS CloudTrail** logs using the Splunk query:

`index="aws_cloudtrail"`

CloudTrail records every API activity performed within the AWS environment, providing a comprehensive source of information for security investigations.

I then applied additional filters in Splunk to identify evidence of a brute-force attack and determine which account had been compromised:

![Brute-Force](images/fail-task1.png)

After identifying the compromised account, I began investigating the attacker's activity. Considering the AWS environment, the next objective was to determine the timestamp of the attacker's first access to an **Amazon S3** object:

![Timestamp](images/timestamp-task2.png)

Next, I investigated which sensitive data had been accessed by the attacker. During the analysis, I identified an S3 bucket containing **.dwg** files that had been accessed:

![DWG file](images/S3-dwg-task3.png)

The following task focused on identifying changes made to the bucket configuration. To accomplish this, I used the following Splunk query:

`index="aws_cloudtrail" "userIdentity.userName"="helpdesk.luke" eventName="PutBucketPublicAccessBlock" | table _time, requestParameters.bucketName, userIdentity.arn`

This allowed me to identify the S3 bucket whose public access configuration had been modified by the attacker:

![Access Configuration](images/S3-vuln-task4.png)

Finally, I investigated the persistence technique used by the attacker. By analyzing the CloudTrail logs, I identified the backdoor IAM user created to maintain long-term access to the AWS environment:

![Backdoor Account](images/CreateUser-task5.png)

As a final step, I determined the IAM group to which the attacker added the newly created account, confirming the persistence mechanism:

![Backdoor Account Group](images/UserToGroup-task6.png)

---

## Key Takeaways

- Gained hands-on experience investigating AWS CloudTrail logs to reconstruct attacker activity in a cloud environment.
- Improved my ability to use Splunk queries to identify unauthorized access, configuration changes, and persistence techniques.
- Better understood how attackers abuse IAM users, S3 buckets, and AWS services to maintain access and compromise cloud environments.

---

## Real-World Relevance

AWS CloudTrail is one of the primary log sources used during cloud security investigations, as it records every API activity performed within an AWS environment. 
Security analysts rely on CloudTrail to identify unauthorized access, investigate configuration changes, and detect persistence techniques used by attackers.

Combined with Splunk, CloudTrail logs can be efficiently searched, correlated, and analyzed to identify suspicious activities, making it an essential skill for cloud security monitoring and threat investigations.
