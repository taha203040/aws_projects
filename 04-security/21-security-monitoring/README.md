![](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_reghtjy)

## Introducing Today's Project!

In this project, I will demonstrate how to monitor access to sensitive information stored in AWS Secrets Manager and configure an alerting system using AWS CloudTrail, Amazon CloudWatch, and Amazon SNS. I am doing this project to learn how to track AWS account activity, detect when a secret is accessed, analyze logs, and receive email notifications when specific events occur. This will help me understand how to improve the security and monitoring of cloud applications.

### ✍️ What are we doing in this step?

In this step, I will create a secret in AWS Secrets Manager to store sensitive credentials securely. This will allow me to manage and access the credentials securely when needed, without exposing them in the application’s codebase.

### Tools and concepts

\*\*Services I used were\*\* AWS Secrets Manager, AWS CloudTrail, Amazon CloudWatch Logs, CloudWatch Metric Filters and Alarms, and Amazon SNS.

\*\*Key concepts I learnt include\*\* auditing secret access through CloudTrail, filtering log events to create custom metrics, configuring CloudWatch alarms using appropriate statistics and thresholds, and automating email notifications through SNS. I also learnt how to troubleshoot monitoring pipelines by isolating each component and validating the end-to-end notification flow.

### Project reflection

This project took me approximately two hours, including troubleshooting and debugging. The most challenging part was identifying the root cause of the notification issue. The most rewarding part was learning how to implement AWS security alarms and configure automated email notifications to monitor access to sensitive secrets.

### ❤️ Thanks for doing this project!

I did this project today to gain practical experience with AWS security monitoring and learn how to detect access to sensitive secrets. The project met my goals because I successfully configured CloudTrail, CloudWatch alarms, and SNS email notifications. I also improved my troubleshooting skills by identifying and fixing the alarm configuration issue, giving me a better understanding of how AWS security monitoring works in practice.

## Create a Secret

AWS Secrets Manager is a service that securely stores, manages, and retrieves sensitive information, such as credentials, API keys, and database passwords. We can use Secrets Manager to protect sensitive data, control access through IAM permissions, and retrieve secrets programmatically without hardcoding them in our application's codebase.

To set up my project, I created a secret in AWS Secrets Manager. The secret contains the text, “I need 3 coffees a day to function.” This allowed me to practice creating and storing a secret that I could later access and monitor using AWS CloudTrail and Amazon CloudWatch.

### ✍️ What are we doing in this step?

In this step, I will create a new trail in AWS CloudTrail to record activity within my AWS account. I will also configure the trail to store log files in an Amazon S3 bucket. This is important because it allows me to maintain an audit history, investigate account activity, and monitor events such as access to secrets stored in AWS Secrets Manager.

![Create a Secret](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_o5p6q7r8)

## Set Up CloudTrail

AWS CloudTrail is a service that records and monitors activity in my AWS account by logging actions performed by users and services. I set up a trail to define which activities CloudTrail records and where the log files are stored. In my project, I configured the trail to deliver logs to an Amazon S3 bucket so I can review account activity and investigate events, such as access to secrets stored in AWS Secrets Manager.

CloudTrail events include management events, data events, and Insights events. Management events record administrative actions, such as creating an S3 bucket or updating IAM permissions. Data events record resource-level operations, such as accessing an object in S3 or retrieving a secret from AWS Secrets Manager when the relevant event logging is enabled. Insights events help identify unusual activity patterns in an AWS account.

### Read vs Write Activity

\*\*Read API activity\*\* involves retrieving information without modifying resources, such as retrieving a secret's value using \`GetSecretValue\`.

\*\*Write API activity\*\* involves modifying resources, such as creating, updating, or deleting a secret.\
For this project, we need to monitor \*\*Read API activity\*\*, specifically the \`GetSecretValue\` event, to track when a secret is accessed in AWS Secrets Manager. CloudTrail records this as a management event, which we can use to configure monitoring and alerts through Amazon CloudWatch.

### ✍️ What are we doing in this step?

In this step, I will retrieve and view the secret I created in AWS Secrets Manager to generate a \`GetSecretValue\` API event. Then, I will check AWS CloudTrail to verify that the event was recorded. This confirms that CloudTrail can track secret access and provides an audit trail for monitoring sensitive operations.

## Verifying CloudTrail

I retrieved the secret in two ways. First, through the AWS Secrets Manager console by opening the secret and viewing its value. Second, using the AWS CLI with the following command:

\`\`\`\
aws secretsmanager get-secret-value --secret-id "TopSecretInfo" --region eu-north-1\
\`\`\`

Both methods allowed me to retrieve the secret and generate API activity that I could later verify in AWS CloudTrail.

To analyze my CloudTrail events, I visited the \*\*Event history\*\* section in the AWS CloudTrail console. I found an event with the event source \`secretsmanager.amazonaws.com\` and the event name \`GetSecretValue\`. This tells me that CloudTrail successfully recorded the API call used to retrieve my secret from AWS Secrets Manager, confirming that secret access can be audited.

### ✍️ What are we doing in this step?

In this step, I will enable Amazon CloudWatch Logs for my CloudTrail trail so that I can analyze AWS activity in real time. Then, I will create a CloudWatch metric filter to detect \`GetSecretValue\` events from AWS Secrets Manager. This will allow me to track secret access and use the metric to configure alarms and notifications when a secret is retrieved.

![Verifying CloudTrail](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_s8t9u0v1)

## CloudWatch Metrics

Amazon CloudWatch Logs is a service that collects, stores, and analyzes log data from AWS services and applications. It's important for monitoring because it allows me to search and analyze CloudTrail events, detect specific API activity such as \`GetSecretValue\`, and create metric filters that track secret access. These metrics can then be used to configure alarms and receive notifications when monitored activity occurs.

CloudTrail's Event History is useful for reviewing and investigating recent AWS account activity, including API calls such as \`GetSecretValue\`. CloudWatch Logs are better for centralized log analysis, creating metric filters to track specific events, and setting up alarms and notifications when secret access occurs.

A \*\*CloudWatch metric\*\* is a numerical measurement used to track and monitor activity over time. When setting up a metric, the \*\*metric value\*\* represents the number recorded each time the filter detects a matching log event. In this project, I set it to \`1\` so that each matching \`GetSecretValue\` event increments the metric by one.

The \*\*default value\*\* is used when no log events match the filter during a given time period. I set it to \`0\` to represent periods without detected secret access, making it easier to monitor activity over time.

### ✍️ What are we doing in this step?

In this step, I will create an Amazon CloudWatch alarm based on the \`SecretIsAccessed\` metric to detect when a secret is accessed. I will then create an Amazon SNS topic and subscribe my email address to it. This will allow CloudWatch to send me email notifications when the alarm is triggered, helping me monitor secret access and respond to unexpected activity.

![CloudWatch Metrics](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_a9b0c1d2)

## CloudWatch Alarm

A \*\*CloudWatch alarm\*\* monitors a metric and changes its state when the metric meets a specified condition. I set my CloudWatch alarm threshold to \*\*greater than or equal to 1\*\*, so the alarm will trigger when the \`SecretIsAccessed\` metric reaches or exceeds 1, indicating that at least one secret access event has been detected.

An \*\*Amazon SNS topic\*\* is a communication channel that allows messages to be sent to subscribed endpoints. My SNS topic is set up to send \*\*email notifications\*\* when the CloudWatch alarm is triggered, alerting me whenever secret access is detected.

AWS requires email confirmation for SNS subscriptions to verify that the email address belongs to someone who agrees to receive notifications. This helps prevent unauthorized subscriptions, unwanted emails, and accidental use of someone else's email address. Once I confirmed the subscription, AWS could send CloudWatch alarm notifications to my email address.

### ✍️ What are we doing in this step?

In this step, I will retrieve my secret value again to generate a new \`GetSecretValue\` event and test whether my CloudWatch alarm is triggered. Then, I will check whether I receive an email notification through Amazon SNS. If the notification does not arrive, I will troubleshoot the monitoring pipeline by checking the CloudTrail logs, metric filter, alarm configuration, and SNS subscription. This will help me verify that the entire monitoring and alerting system works as expected.

![CloudWatch Alarm](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_fsdghstt)

## Troubleshooting Notification Errors

To test my monitoring system, I retrieved the secret value again using AWS Secrets Manager, generating another \`GetSecretValue\` event. However, I did not receive an email notification after waiting a few minutes. This suggests that something in the monitoring pipeline may not be configured correctly, so I need to troubleshoot the CloudTrail logs, metric filter, CloudWatch alarm, and SNS notification settings to identify the issue.

While troubleshooting the notification issue, I identified that the CloudWatch alarm was using the \`Average\` statistic instead of \`Sum\`. I changed the statistic to \`Sum\` so that CloudWatch could correctly count secret-access events over the five-minute evaluation period. After this change, the alarm triggered as expected, and the email notification was successfully delivered through Amazon SNS.

I initially didn't receive an email because the CloudWatch alarm was configured to use the \`Average\` statistic, which did not trigger the alarm when the metric failed to reach the threshold of \`1\`.

The key solution was to change the statistic from \`Average\` to \`Sum\`, allowing CloudWatch to count secret-access events over the five-minute evaluation period. Once the metric reached the threshold, the alarm transitioned to \`ALARM\` and successfully sent an email notification through Amazon SNS.

## Success!

To validate the notification system, I accessed the secret in AWS Secrets Manager and checked the CloudWatch alarm history to confirm that the alarm transitioned to the \`ALARM\` state. I then verified that I received the email notification through Amazon SNS.

![Success!](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/a6948fcf-cdce-53e8-9037-892917ce7585_ageraergearge)
