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
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Create%20Table.png?raw=true)

* Name the table employee_info.
* Name the partition id employeeid.
* Seleect create table.



### 2. Create Lambda Function

* Open the lambda service and choose create function.

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Create%20Function.png?raw=true)

* Under basic information choose.
* Lets name the function api_processing
* For runtime we will use python3.11
* For the default execution role we will choose "create new role from AWS policy templates"
* Under role name enter serverless_api_demo (gives access to cloudwatch and dynamoDB)

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/api%20processing.png?raw=true)

  


  

  

### 3. Create IAM Role for DynamoDB and Cloudwatch

* After the Lambda function is created go to the bottom panel and choose Configuration, and select Permissions.

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Add%20Roles.png?raw=true)

* Now we want to add permissions that will allow cloudwatch and dynamodb access, choose add permissions and attach policies.
  
* Search within the permissions and choose AmazonDynamoDBFullAccess and CloudwatchLogsFullAccess.

   ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Roles%20Added.png?raw=true)




## 4. Create REST API in API Gateway 

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Choose%20API.png?raw=true)
* Go to REST API and select build.
* Choose NEW API and name it serverless-demo.
* Select Create API.



 
## 5. Create API Resources 

* Go into the API Gateway Service.

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/2.png?raw=true)
  
* Select Create resource, we will create 3 resources.
* For the resource path choose /
* For the reource name we will create 3 individual resources named
 ```
  employee
  employees
  status

```
``` Output should look like this ```

![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/API%20Resources.png?raw=true)



## 6.  Create API Methods for our resources

* Once in the API module select the employee resource and to the right select create method.
* For method type choose GET.
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/1.png?raw=true)

 
``` Repeat this process for each reseource (employees and status) ```
* Choose Enable Lambda proxy Integration.
* Select the Lambda function we created api_processing.
* Select Create Method.

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/3.png?raw=true)
 
* _Once back at the API module repeat the same process for the employees resouce and status resources_

* To modify employee we will add DELETE PATCH and POST Methods. Repeat the process but choose each for method type when creating.
* When done your API module should look similar to below. 

![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/API%20METHODS%20COMPLETE.png?raw=true)

## 7. Deploy API
 
* In the API module select Deploy API
* Select the drop down and choose "New Stage" for stage name enter production.
* Select Deploy.
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/prod%20deploy.png?raw=true)
* To test, select the invoke url and enter it into a browser with /status at the end.
* Your webpage should display
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/API%20Test.png?raw=true)

  


## 8. Enter Lambda Code

* Open the Lambda Service and choose the lambda function created api_processing.
  
* Under Code source choose Test.
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/lambda%20code%20edit.png?raw=true)
  
* Here is where we will copy the python code from here:  ![Python Code](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Lambda_Function.py)

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/la%20mbda%20configure%20test%20event.png?raw=true)\

* Now select configure test event and name it test.

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/test%20.png?raw=true)

* Next Deploy changes.

* To check launch the url again with /status at the end and you should get

  ``` "Service is operational" ```
   
## 9. Postman- Add entries to DynamoDB table

* In the Postman My work space next to overview we will select the plus sign. 
* Make select POST is selected and add the invoke url in the blank. 
* Below select Body and make sure its in JSON format
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






