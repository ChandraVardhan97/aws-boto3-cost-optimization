# AWS Cloud Cost Optimization - Identifying Stale Resources

## Identifying Stale EBS Snapshots

In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

### Description:

The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.


## Steps to be followed:

1. Create a Lambda function. Copy the Boto3.py code and add it to the function body.
2. Before testing the function, increase the Lambda function timeout to 10 secs from the default 3 secs.
3. Also, provide the necessary permissions like DeleteSnapshot, DescribeSnapshot, DescribeInstances and DescibeVolumes to the default Lambda role.
4. Test the Lambda function. Here ,we are manually triggering the function. We can also setup a event in CloudWatch and trigger this Lambda function based on a CRON expression.
5. Also, the code can be modified to only delete the volumes beyond a certain expiration date. This can be achieved by using the if condition.