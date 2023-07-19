**<h2>Tutorial: Build a CRUD API with HTTP API, IAM Role, Lambda and DynamoDB</h2>**
First, you create a DynamoDB table using the DynamoDB console. Then you create a Lambda function using the AWS Lambda console. Next, you create an HTTP API using the API Gateway console. Lastly, you test your API.

When you invoke your HTTP API, API Gateway routes the request to your Lambda function. The Lambda function interacts with DynamoDB and returns a response to API Gateway. API Gateway then returns a response.

 ![image](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/c466e323-c080-48c4-987c-4e16dc96395d)


**<h3> Steps</h3>**
Step 1: Create a DynamoDB table <br>
Step 2: Create an IAM Role and Create a Lambda function<br>
Step 3: Create a Lambda function<br>
Step 4: Create an HTTP API<br>
Step 5: Create routes<br>
Step 6: Attach your integration to routes<br>
Step 7: Test your API<br>

**<h3> Step 1: Create a DynamoDB table</h3>**
1. Open the DynamoDB console.
2. Choose Create table.
3. For Table name, enter http-crud-table.
4. For Partition key, enter id.
5. Choose Create table.

![1](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/7fb25d77-91ea-4126-a0ee-53b47cdce289)

![2](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/d1c4e996-bc7e-494f-ae9d-4c73b6fb6acb)

**<h3> Step 2: Create an IAM Role</h3>**
1. Go to IAM.
2. Create Role. 
3. Add Permissions.
4. Create.

![4](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/65af71ff-edff-45c0-b49a-b41a1834cd97)

![5](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/668caf24-790a-4cba-b63a-2c7d6d268b83)

![6](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/f8abecb1-a1c4-4a7a-b568-265aae82139e)

![7](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/66d12490-33bf-4650-b7ae-c68c894402c1)

**<h3> Step 3: Create a Lambda Function</h3>**
1. Sign in to the Lambda console at https://console.aws.amazon.com/lambda.
2. Choose Create function.
3. For Function name, enter http-crud-lambda-function.
4. Under permission choose the IAM role that we just created i.e., http-crud-role

![3](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/2d565164-f25d-4a8f-9ee7-12875761db19)

![8](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/aee437fb-3cf6-4703-ad45-86e2cb0c4de4)

![9](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/c8cbaeae-8bed-4c4a-9bd3-6ecb1f7002b0)

![10](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/66dd3a55-a316-47da-86e3-4d9207b6c3a3)

5. Open index.mjs in the console's code editor, and replace its contents with the following code. Choose Deploy to update your function. Download **HERE** [crud.txt](https://github.com/ravinder-panwar/CRUD-Serverless-API/files/12094506/crud.txt)

**<h3> Step 4: Create an HTTP API</h3>**
1. Go to the API Gateway console at https://console.aws.amazon.com/apigateway.
2. Choose Create API, and then for HTTP API, choose Build.
3. For API name, enter http-crud-api.
4. Choose Next.

![11](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/8bbba3b1-f9c7-49e3-8d26-8050c6945544)

![12](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/f6999d70-f9ce-444b-b017-d62b67ce8587)

**<h3> Step 5: Create routes</h3>**
Routes are a way to send incoming API requests to backend resources. Routes consist of two parts: an HTTP method and a resource path, for example, **GET /items**. For this example API, we create four routes:

GET /items/{id} <br>
GET /items<br>
PUT /items<br>
DELETE /items/{id} <br>

**To create routes**

1. Choose your API.
2. Choose Routes.
3. Choose Create.
4. For Method, choose GET.
5. For the path, enter /items/{id}. The {id} at the end of the path is a path parameter that API Gateway retrieves from the request path when a client makes a request.
6. Choose Create.
7. Repeat steps 4-7 for GET /items, DELETE /items/{id}, and PUT /items.

![13](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/9ed4f983-71d4-4a3f-8dcf-b18cbbb17a68)

**Step 6: Attach your integration to routes**

1. Choose your API.
2. Choose Integrations.
3. Choose a route.
4. Under Choose an existing integration, choose http-crud-function.
5. Choose Attach integration.
All routes show that an AWS Lambda integration is attached.

![14](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/479423ff-6f64-4685-a10d-d8c8128d0425)

**Step 7: Test your API**

1. Choose your API.
2. Copy your API's invoke URL. It appears under Invoke URL on the Details page.

![15](https://github.com/ravinder-panwar/CRUD-Serverless-API/assets/133412857/fdf8415b-7f8c-4e24-8751-4dc236d866a2)

**<h2> DONE!! CONGRATS. Now you can verify the working by either using CLI or Postman.</h2>**



