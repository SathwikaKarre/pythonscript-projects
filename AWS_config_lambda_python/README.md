## Ensuring EC2 Compliance with AWS Config
## Objective
This guide outlines how to use AWS Config to automatically check whether EC2 instances have monitoring enabled. Instances that have monitoring enabled will be marked as compliant, while those without monitoring will be flagged as non-compliant.


## Step 1: Configure AWS Config
Access AWS Config:

Sign in to the AWS Management Console.
Navigate to the AWS Config service.
Set Up AWS Config:

If this is your first time, click "Get Started".
Configure delivery settings by specifying an Amazon S3 bucket where AWS Config can store historical configuration data.
Select Resources to Monitor:

Choose the resource types to track.
Select Amazon EC2 Instances to monitor their compliance.


## Step 2: Create a Custom AWS Config Rule
Navigate to AWS Config Rules:

Open the AWS Config dashboard.
Click "Rules" on the left panel.
Choose "Add rule".
Define a Custom Rule:

Select "Create custom rule".
Provide a rule name (e.g., "EC2 Monitoring Compliance") and a brief description.
Set the scope to monitor EC2 instances.
Set a Rule Trigger:

Select "Configuration changes" as the trigger type.
Choose AWS Lambda as the rule’s evaluation mechanism.


## Step 3: Implement a Lambda Function for Compliance Evaluation
Create a Lambda Function:

If not already created, set up a Lambda function to check whether monitoring is enabled for an EC2 instance.
The function should return compliance status based on monitoring settings.
Attach the Lambda Function to the Rule:

In AWS Config, select the Lambda function from the dropdown menu.
Save the rule to activate compliance checks.


## Step 4: Continuous Compliance Monitoring
AWS Config will now automatically assess all EC2 instances.

If an instance has monitoring enabled, it will be marked compliant.

If monitoring is disabled, the instance will be flagged as non-compliant.

You can review compliance reports and set up alerts for non-compliant instances.


## Next Steps
✅ Enable notifications using AWS SNS for real-time alerts.

✅ Automate remediation by integrating AWS Systems Manager to enable monitoring on non-compliant instances.

✅ Schedule periodic evaluations for better visibility into compliance trends.

By following this approach, you ensure that all EC2 instances meet best practices for monitoring, improving security and operational efficiency
