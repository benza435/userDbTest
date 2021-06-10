## What we did:

`$ npm install -g expo-cli`  
`$ expo init meaningfulName`  
`$ cd <projectfolder>`
`$ npm install aws-amplify-react-native`
`npm install @aws-amplify/ui-react`  
`amplify init` - used default project name but it was not what we expected  
-use defaults
-choose access keys

- eu-west-2
- wait a few mins  

now we are going to add amplify api

ben@ben-Predator-PH317-53:~/nc_/project/userDbTest$ amplify add api
? Please select from one of the below mentioned services: GraphQL
? Provide API name: userdbtest
? Choose the default authorization type for the API API key
? Enter a description for the API key: public
? After how many days from now the API key should expire (1-365): 365
? Do you want to configure advanced settings for the GraphQL API No, I am done.
? Do you have an annotated GraphQL schema? No
? Choose a schema template: Single object with fields (e.g., “Todo” with ID, name, description)

`amplify add function`
? Select which capability you want to add: Lambda function (serverless function)
? Provide an AWS Lambda function name: putUserIntoDbTable
? Choose the runtime that you want to use: NodeJS
? Choose the function template that you want to use: Hello World

advanced configuration -Y
? Do you want to configure advanced settings? Yes
? Do you want to access other resources in this project from your Lambda function? Yes
? Select the categories you want this function to have access to. api
? Select the operations you want to permit on userdbtest Query, Mutation

You can access the following resource attributes as environment variables from your Lambda function
        API_USERDBTEST_GRAPHQLAPIENDPOINTOUTPUT
        API_USERDBTEST_GRAPHQLAPIIDOUTPUT
	API_USERDBTEST_GRAPHQLAPIKEYOUTPUT
	ENV
	REGION
? Do you want to invoke this function on a recurring schedule? No
? Do you want to configure Lambda layers for this function? Yes
? Enter up to 5 existing Lambda layer ARNs (comma-separated): 
aborted here because it was full of shit

we are about to run `amplify add auth`
















  `amplify add auth`  
  -choose manual config

Do you want to use the default authentication and security configuration? Manual configuration
Select the authentication/authorization services that you want to use: User Sign-Up, Sign-In, connected with AWS IAM controls (Enables per-user Storage feature
s for images or other content, Analytics, and more)
Please provide a friendly name for your resource that will be used to label this category in the project: friendlyResource
Please enter a name for your identity pool. friendlyResourceIdentityPool
Allow unauthenticated logins? (Provides scoped down permissions that you can control via AWS IAM) No
Do you want to enable 3rd party authentication providers in your identity pool? No
Please provide a name for your user pool: friendlyResourceUserPool
Warning: you will not be able to edit these selections.
How do you want users to be able to sign in? Username
Do you want to add User Pool Groups? Yes
? Provide a name for your user pool group: Admin
? Do you want to add another User Pool Group No
✔ Sort the user pool groups in order of preference · Admin
Do you want to add an admin queries API? No
Multifactor authentication (MFA) user login options: OFF
Email based user registration/forgot password: Enabled (Requires per-user email entry at registration)
Please specify an email verification subject: Your verification code
Please specify an email verification message: Your verification code is {####}
Do you want to override the default password policy for this User Pool? No
Warning: you will not be able to edit these selections.
What attributes are required for signing up? Email
Specify the app's refresh token expiration period (in days): 30
Do you want to specify the user attributes this app can read and write? No
Do you want to enable any of the following capabilities?
Do you want to use an OAuth flow? No
? Do you want to configure Lambda Triggers for Cognito? Yes
? Which triggers do you want to enable for Cognito Post Confirmation
? What functionality do you want to use for Post Confirmation Create your own module
Successfully added resource friendlyResourcePostConfirmation locally.

ext steps:
Check out sample function code generated in <project-dir>/amplify/backend/function/friendlyResourcePostConfirmation/src
"amplify function build" builds all of your functions currently in the project
"amplify mock function <functionName>" runs your function locally
"amplify push" builds all of your local backend resources and provisions them in the cloud
"amplify publish" builds all of your local backend and front-end resources (if you added hosting category) and provisions them in the cloud
Successfully added the Lambda function locally
? Do you want to edit your custom function now? Yes
? Choose your default editor: Visual Studio Code
Edit the file in your editor: /home/ben/nc\_/project/ramblrWithDynamodb/amplify/backend/function/friendlyResourcePostConfirmation/src/custom.js
? Press enter to continue

-renamed custom.js to index.js, then:
-copy code from [link](https://docs.amplify.aws/guides/functions/cognito-trigger-lambda-dynamodb/q/platform/js#create-the-lambda-function)
-saved index.js
