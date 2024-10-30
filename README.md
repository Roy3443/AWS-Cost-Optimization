### Problem Explanation
Imagine you created an EC2 instance with an attached root EBS volume, to store the data related to your application hosted on that instance. You decided to take a backup of that EBS volume by taking a snapshot, to restore it as a new volume in a different AZ when a disaster strikes. But, you need the snapshots only as long as the application exists. If you decide to shut down your application on the EC2 instance, there will be no need for the snapshot. In that scenario, the snapshots associated with the instance needs to be deleted to be financially efficient.

If you just have one or two EC2 intances to manage, this won't be a big deal, and you can easily manage creation and deletion snapshots manually. But, companies usually have a lot of resources and EC2 instances to manage in various AWS regions. So the above task is almost impossible to be done manually.

This is when Lambda functions in AWS emerge.

### Why Lambda?
Lambda functions are serverless, it doesn't mean there aren't any servers. It just means that you don't have to manage the underlying servers. All you have to do is write code to perform your desired actions. For this function, you have to add a trigger i.e., for the function to be triggered when an EC2 instance is deleted. This action leads to the running of the function, which will check if any stale snapshots created from the deleted instance exist and delete.

A Lambda function is developed utilizing AWS Boto3, which is an AWS SDK, to automate the identification and deletion of stale snapshots, thus optimizing cloud expenses. Through proactive management of snapshots, the Lambda function contributes to cost optimization strategies within AWS environments.
