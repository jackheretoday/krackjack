# krackjack
krackjack is a security tool webapp.

exp.7 Lambda function "Hello World" using node/python/java

1. Create new function(author from scratch, func name, runtime:python 3.13, x86_64,new role)
2. After create function dismiss pop-up, scroll to code source automatically code is visible, add: print("Hello World") below #TODO implement 
3. Sholud be visible like this:
4. # TODO implement
    print("Hello World")

5.Change body: "hii"
6.Click test, new test event appears, name the event & save it.
7. Click Deploy
8. Open new AWS tab,search cloudwatch 
9. Go to Log group, u will find the function there, go to it.
10. Go to Log Stream, u will find there the stream click it, in Logs Hello World will be visible.

exp.8 Lambda function to log "an object has been added" on adding the object to S3 bucket.

1. search IAM Role, create role(service:Lambda)
2. Add permissions:AmazonS3FullAccess, CloudWatch FullAccess, Lambda basic execution, then name the role and create role.
3. Goto Lambda function, create function(name function,runtime:python 3.13,use existing role:role made in IAM role) 
4.  open new tab and goto aws console, S3 buckets, create bucket.
5.  Go to last tab of lamnda function, in code source replace & edit the code:
6.
import json
import boto3

s3 = boto3.client('s3')

def lambda_handler(event, context):
    bucket_name = 'your-bucket-name'     # change this to your S3 bucket
    file_name = 'data.json'
    data = {
        "name": "Asmit",
        "age": 21,
        "course": "IT Engineering"
    }
    # Upload JSON to S3
    s3.put_object(
        Bucket=bucket_name,
        Key=file_name,
        Body=json.dumps(data)
    )
    print("✅ Object has been uploaded to S3!")
    return {
        'statusCode': 200,
        'body': json.dumps('File uploaded successfully!')
    }
7.Click deploy, test(new test event,name the test,save it)
8.status: success
9.Goto bucket, view the object.
10.Cloudwatch the logs group.
    
