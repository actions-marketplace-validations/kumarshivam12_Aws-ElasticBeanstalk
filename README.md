# Aws-ElasticBeanstalk
This GitHub action enables the user to zip the source code to create a pipeline by pushing the ZIP file into AWS S3 Bucket and then enable Elastic Beanstalk to fetch the ZIP file from the S3 Bucket. It will also enable the versioning of the deployment on every commit.
The action has two workflows combined.

**Pre-requisite**
* An AWS user with privileged access to S3 and Elastic Beanstalk
*  **Generate and Save Your AWS access-key id as "AWS_ACCESS_KEY" and Secret-Key as "AWS_SECRET_KEY" in your Github Repo Secrets. Do not change the name !!**
* S3 Bucket need not be public


User Guide, Please Check out [demo](https://github.com/kumarshivam12/flaskapp)

```YAML
name: Elastic Beanstalk Deployment
on:
  push:
    branches:
    - master
    
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    
    - name: Checkout source code
      uses: actions/checkout@v1
      
    - name: Elastic Beanstalk Deployment
      uses: kumarshivam12/Aws-ElasticBeanstalk@v1.3
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_KEY }}
        EB-BUCKET-NAME: 
          description : Enter The Name of the S3 Bucket
        APPLICATION-NAME: 
          description : Enter the name of the Elastic BeanStalk Application
        EB-ENV-NAME: 
          description : Name of the Elastic beanstalk Environment
        AWS-REGION: 
          description : Enter the Region

```
