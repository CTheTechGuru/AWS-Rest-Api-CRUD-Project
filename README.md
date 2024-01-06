AWS Rest API CRUD Project

<h1 align="center">AWS Rest API CRUD Project</h3>

![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/image21.jpg)





<!-- PROJECT Details-->
# About The Project


#### Overview:

 In this tutorial we will go over thr following.  
 
-Creating a REST API in API gateway with several different endpoint and all the CRUD methods.

-Write python code in Lambda to process all methods and resources part of the API Gateway.

-Creating a dynamoDB table to store data from our API.

-Create the IAM roles to use cloudwatch and dynamoDB.


 # Prerequisites


* Access to AWS (Free Tier or Paid)
* _Best Practice_ Create AWS user account with administrator access.(enable MFA on lab account)
* An IDE, I will use studio visual code. 

##  

### 1. Builld DynamoDB Table

* Once in the the dynamoDB console choose tables and create table.
* Name the table employee_info.
* Name the partition id employeeid.
* Seleect create table.



### 2. Create Lambda Function

* Open the lambda service and choose create function.
* Under basic information choose
* Lets name the function api_processing
* For runtime we will use python3.11
* For the default execution role we will choose "create new role from AWS policy templates"
* Under role name enter serverless_dapi_demo (gives access to cloudwatch and dynamoDB)
  


  

  

### 3. Create Role for

* After the Lambda function is created go to the bottom panel and choose Configuration, and select Permissions.
* 
* Select the role name.
  
* Now we want to add permissions that will allow cloudwatch and dynamodb access, choose add permissions and attach policies.
  
* Search within the permissions and choose AmazonDynamoDBFullAccess and CloudwatchLogsFullAccess.





## 4. Create REST API in API Gateway 

* Go to REST API and select build.
* Choose NEW API and name it serverless-demo.
* Select Create API.



 
## 5. Create API Gateway Resources and Methods

* Select create resource and name it status and check CORS. 
* Next we will create a get method. 
* Choose GET for the Method type.
* Select Lambda proxy integration.
* Under the lambda function tab next to the AZ choose the function name api_processing created earlier.

* Next Create 2 more resources. employee and employees.

* For employees and empployees we will create get methods.
* 
*
*




## 6.  

*
*
*
*
*
*
*


## 7. 
 
*
*
*
*


## 8. 

*
*
*
*
*


  
 
## 9. 

*
*
*
*
*




 
## 10.

*
*
*
*
*
*


<h1 align="center">Summary</h3>







<!-- CONTACT -->
## Contact

Cordelra Lowman - Cordelra_Lowman@yahoo.com

<h3 align="left">Follow me on Linkedin:</h3>
<p align="left">
<a href="https://linkedin.com/in/cordelra lowman" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="cordelra lowman" height="30" width="40" /></a>
</p>






