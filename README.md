Serverless REST API with API Gateway & Lambda | CRUD Project

<h1 align="center">Serverless REST API with API Gateway & Lambda</h3>

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
* Select create table.



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
* For the resource name we will create 3 individual resources named
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

 
``` Repeat this process for each resource (employees and status) ```
* Choose Enable Lambda proxy Integration.
* Select the Lambda function we created api_processing.
* Select Create Method.

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/3.png?raw=true)
 
* _Once back at the API module repeat the same process for the employees resource and status resources_

* To modify employee we will add DELETE PATCH and POST Methods. Repeat the process but choose each for method type when creating.
* When done your API module should look similar to below. 

![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/API%20METHODS%20COMPLETE.png?raw=true)

## 7. Deploy API
 
* In the API module select Deploy API
* Select the drop down and choose "New Stage" for stage name enter production.
* Select Deploy.
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/prod%20deploy.png?raw=true)
  
* To test, select the invoke URL and enter it into a browser with /status at the end.
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
   
## 9. Postman- Add entries to DynamoDB table ![Postman Link](https://webpostman.co)

* Once logged in In the Postman My workspace next to overview we will select the plus sign. 
* Hover over overview and right click, choose NEW Request. 
* Add the Lambda invoke URL in the blank. 
* Below select Body and make sure it’s in JSON format and for the body choose Raw.

* Next we will add entries.
* Select GET Method
* In the editor enter your values
* I will add multiple entries. Duplicate with different values and select send for the entries to update in the table. 
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Get%20Method%20based%20off%20ID.png?raw=true)

* To verify multiple were made entries check the employees resource. 

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/GET%20Employees%20Table.png)
 
## 10. Verify DynamoDB entries in employee_info table

* Open the DynamoDB console and select Tables.
* Select the employee_info table then explore table items.
* You should see the entries you’ve made.

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/DBTABLE.png?raw=true)


 
## 10. Cloudwatch Logs

* Open the cloudwatch console and select the Logs drop down, then choose log insights.
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Log%20Insights.png?raw=true)
  
* Now select the drop down next to browse log groups, here we will select our api. ``` api_processing ```
  
* Choose Run query.
  
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Logs%20from%20our%20api.png?raw=true)
  
* From here you can monitor the logs and errors that occur. 


 
## 10. GET, PATCH, DELETE Methods 

1. GET METHOD _example_ ``` GET https://jel1cmykxa.execute-api.us-east-1.amazonaws.com/production/employee?employeeid=(your choice of employee id) ```
 * First we will use the GET method to query data for our employeeid "98"
  ``` Our return ```
  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Get%20Method%20based%20off%20ID.png?raw=true)
  
* Remember if we want to query all inputs we can run a GET on employees. Which would return
 _example_ ```https://jel1cmykxa.execute-api.us-east-1.amazonaws.com/production/employees ```
   ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/GET%20Employees%20Table.png)

2. PATCH  METHOD _example_ ``` PATCH https://jel1cmykxa.execute-api.us-east-1.amazonaws.com/production/employees ```
* Next we will PATCH an entry.
* To select our first entry will be the employeeid, in our code when patching the key has to be employeeId instead of employeeid.
* We will enter values for update key and update value of what we would like to change.

_Example_ update employee 98 Salary to 555555

![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/PATCH%20Changed%20Salary%20of%20ID%2098.png?raw=true)

```
{
    "employeeId": "98",
    "updateKey": "Salary",
    "updateValue": 5555555


    
}

```

3. DELETE METHOD _example_ DELETE ``` https://jel1cmykxa.execute-api.us-east-1.amazonaws.com/production/employee ```

{
   "employeeId": "98",

}

 ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/GET%20Employees%20Table.png?raw=true)

* Run GET on the employees table to confirm deletion.

  ![](https://github.com/CTheTechGuru/AWS-Rest-Api-CRUD-Project/blob/main/Images/Verify%20Delete.png)


<h1 align="center">Summary</h3>

   In summary we created a dynamoDB table which we used to store our entries. We created a lambda function which and named our api. 
 We created an IAM role for DynamoDB and Cloudwatch to allow our lambda function to have access to store items in our table along with logging and monitoring.
 Used API Gateway to create a Rest API which allowed us to implement our CRUD methods to interact without DB.
 Deployed our lambda code which created our serverless environment. Next we used postman to add entries to our DB table and tested each CRUD method.
 We verified that the tables were added in our DynamoDB table and we also used Cloudwatch for monitoring 
 the logs of our API. 




<!-- CONTACT -->
## Contact

Cordelra Lowman - Cordelra_Lowman@yahoo.com

<h3 align="left">Follow me on Linkedin:</h3>
<p align="left">
<a href="https://linkedin.com/in/cordelra lowman" target="blank"><img align="center" src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="cordelra lowman" height="30" width="40" /></a>
</p>






