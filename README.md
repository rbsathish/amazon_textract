# amazon_textract
Extracting text(text,form,table) using Textract.
for the given formats .png,.jpg,.pdf in the s3.
use the src ---> lamnda_function.py to extract.
But first you need to config s3,lambda,layer,iam.

Lambda Layer:
	First download the boto3 layer.
	click lambda ---> layer
	And fill the details
		Name of the layer
		upload the boto3-layer zip using zip upload
		select compitable runtime as python 3.7
		And click create.

Create S3:
	Go to the S3 bucket area. Just click on “Services” then “S3”
	Gives the name “textract-analysis-example” and click on	“Create”.


Lambda Function:
	Go to “Services”, then “Lambda”

	Click on “Functions” in the sided menu and then click on 	“Create function”

	Select “Use a blueprint” and search for “s3-get-object-	
	python”

	Select the option listed and click on “configure”
	
	Give a “Function name” and “Execution role”

	Click--> create a new role from AWS policy templates

	Select your S3 bucket that we already created
	
	Add “.pdf” at Suffix area. With this option, Lambda 	functions will run only when a PDF file was uploaded.
	(Later you can add more events in s3. follow this steps
	Go to your s3 bucket--->click permision--->scroll & go for 	Events--->click events --->Add ---> here you can add more 	events like .jpg,.png) If you put this formats of files in 	your s3 bucket means this will trigger the lambda.)

	
	Enable trigger

	Click on “Create function”

	After creating copy the lambda_fuction.py code from my	src.
	And paste and save the lambda fuction.



IAM Role:(Add Textract, SNS, SQS and S3 permissions)
	
	Go to the role on the iam select your role that you already 	create using lambda.

	Click on attach policies

	Add the following policies: 
	“AmazonSQSFullAccess”	          “AmazonS3FullAccess”, 			“AmazonTextractFullAccess”, 	“AmazonSNSFullAccess”

	Mark the checkbox of the listed option

	click on Attach policy


	Copy Role ARN and paste that in your 	lamda_functions.py 	(self.roleArn = " paste here" )in your code


Add boto3 layer:
	
	Go to your lambda function
	
	Click on “Layers”
		
	Then “Add Layer”
	
	Select your layer and give version name.

	Click on “Add” then “Save”


	
	






 