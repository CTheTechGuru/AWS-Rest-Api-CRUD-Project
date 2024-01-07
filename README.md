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
  ![]()

* Name the table employee_info.
* Name the partition id employeeid.
* Seleect create table.



### 2. Create Lambda Function

* Open the lambda service and choose create function.

  ![]()

* Under basic information choose.
* Lets name the function api_processing
* For runtime we will use python3.11
* For the default execution role we will choose "create new role from AWS policy templates"

  ![]()

* Under role name enter serverless_dapi_demo (gives access to cloudwatch and dynamoDB)

  ![]()

  


  

  

### 3. Create IAM Role for DynamoDB and Cloudwatch

* After the Lambda function is created go to the bottom panel and choose Configuration, and select Permissions.

 ![]()

* Select the role name.
  ![]()

* Now we want to add permissions that will allow cloudwatch and dynamodb access, choose add permissions and attach policies.
  
* Search within the permissions and choose AmazonDynamoDBFullAccess and CloudwatchLogsFullAccess.

![]()




## 4. Create REST API in API Gateway 

* Go to REST API and select build.
* Choose NEW API and name it serverless-demo.
* Select Create API.

![]()


 
## 5. Create API Resources 

* Go into the API Gateway Service. 
* Select Create resource, we will create 3 resources.
* For the resource path choose /
* For the reource name we will create 3 individual resources named
 ```
  employee
  employees
  status

```
![]()



## 6.  Create API Methods for our resources

* Once in the API module select the employee resource and to the right select create method.
* For method type choose GET.
  ![]()

 
``` Repeat this process for each method ```
* Choose Enable Lambda proxy Integration.
* Select the Lambda function we created api_processing.
* Select Create Method.

* _Once back at the API module repeat the same process for the employees resouce and status resources_

* To modify employee we will add DELETE PATCH and POST Methods. Repeat the process but choose each for method type when creating.
* When done your API module should look similar to below. 

![]()

## 7. Deploy API
 
* In the API module select Deploy API
* Select the drop down and choose "New Stage" for stage name enter production.
* Select Deploy.
* To test, select the invoke url and enter it into a browser with /status at the end.
* Your webpage should display
  ![]()

* Next we will bo
*
*


## 8. Enter Lambda Code

* Open the Lambda Service and choose the lambda function created api_processing.
* Under Code source choose Test.
* Here is where we will copy the python code from here:  ![Python_Code]()
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






