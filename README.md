# Personal website with automation for an S3 static site.

## Instructions
1. Grab HostedZoneID
```
aws route53 list-hosted-zones
```
2. Update parameters.json with your zone ID and domain name.
3. Provision resources using CloudFormation. Replace with the name you'd like for your Cloudformation stack.
```
aws cloudformation create-stack --stack-name <stack-name> --template-body file://template.yaml  --parameters file://parameters.json
```
4. Monitor progress via the AWS Console or from the CLI with aws cloudformation describe-stacks until the status is CREATION_COMPLETE. Grab a coffee because this step may take 30-45 minutes.
5. Upload site contents to S3. Replace with the chosen stack name from step 2.
aws s3 cp site/* s3://<stack-name>-root 
## Note:
- It is required to deploy this stack in us-east-1, as ACM and CloudFront run out of this region.