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

ben@ben-Predator-PH317-53:~/nc\_/project/userDbTest$ amplify add api
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

### aborted here because we have devjated too far from the docs

`amplify add auth`
-manual configuration
-first option

Please provide a friendly name for your resource that will be used to label this category in the project
: userDbTestResource
Please enter a name for your identity pool. userDbTestIdentityPool
Allow unauthenticated logins? (Provides scoped down permissions that you can control via AWS IAM) No
Do you want to enable 3rd party authentication providers in your identity pool? No
Please provide a name for your user pool: userDbTestUserPool
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
Successfully added resource userDbTestResourcePostConfirmation locally.

Next steps:
Check out sample function code generated in <project-dir>/amplify/backend/function/userDbTestResourcePostConfirmation/src
"amplify function build" builds all of your functions currently in the project
"amplify mock function <functionName>" runs your function locally
"amplify push" builds all of your local backend resources and provisions them in the cloud
"amplify publish" builds all of your local backend and front-end resources (if you added hosting category) and provisions them in the cloud
Successfully added the Lambda function locally
? Do you want to edit your custom function now? (Y/n)

---

? Choose your default editor: Visual Studio Code
Edit the file in your editor: /home/ben/nc\_/project/userDbTest/amplify/backend/function/userDbTestResourcePostConfirmation/src/custom.js
? Press enter to continue
Successfully added auth resource userDbTestResource locally

Some next steps:
"amplify push" will build all your local backend resources and provision it in the cloud
"amplify publish" will build all your local backend and frontend resources (if you have hosting category added) and provision it in the cloud
-0--------------

`amplify update api`
? Please select from one of the below mentioned services: GraphQL
? Select from the options below Walkthrough all configurations
? Choose the default authorization type for the API Amazon Cognito User Pool
Use a Cognito user pool configured as a part of this project.
? Do you want to configure advanced settings for the GraphQL API Yes, I want to make some additional chan
ges.
? Configure additional auth types? No
? Enable conflict detection? No

The following types do not have '@auth' enabled. Consider using @auth with @model - User
Learn more about @auth here: https://docs.amplify.aws/cli/graphql-transformer/auth

GraphQL schema compiled successfully.

Edit your schema at /home/ben/nc*/project/userDbTest/amplify/backend/api/userdbtest/schema.graphql or place .graphql files in a directory at /home/ben/nc*/project/userDbTest/amplify/backend/api/userdbtest/schema
The API_KEY auth type has been removed from the API.
If other resources depend on this API, run "amplify update <category>" and reselect this API to remove the dependency on the API key.
⚠️ This must be done before running "amplify push" to prevent a push failure
Successfully updated resource

# this may have been a mistake

updated amplify/backend/api/userdbtest/schema.graphql

en@ben-Predator-PH317-53:~/nc\_/project/userDbTest$ amplify push --y
✔ Successfully pulled backend environment dev from the cloud.

Current Environment: dev

`amplify push --y`

| Category | Resource name                      | Operation | Provider plugin   |
| -------- | ---------------------------------- | --------- | ----------------- |
| Api      | userdbtest                         | Create    | awscloudformation |
| Function | userDbTestResourcePostConfirmation | Create    | awscloudformation |
| Auth     | userPoolGroups                     | Create    | awscloudformation |
| Auth     | userDbTestResource                 | Create    | awscloudformation |

GraphQL schema compiled successfully.

https://6xqblemyzreutmgj2dvtwti3ui.appsync-api.eu-west-2.amazonaws.com/graphql
returns

{
errors: [
{
errorType: "UnauthorizedException",
message: "Missing authorization header"
}
]
}

`amplify update api`
? Please select from one of the below mentioned services: GraphQL
? Select from the options below Update auth settings
? Choose the default authorization type for the API Amazon Cognito User Pool
Use a Cognito user pool configured as a part of this project.
? Configure additional auth types? Yes
? Choose the additional authorization types you want to configure for the API IAM

GraphQL schema compiled successfully.

Edit your schema at /home/ben/nc*/project/userDbTest/amplify/backend/api/userdbtest/schema.graphql or place .graphql files in a directory at /home/ben/nc*/project/userDbTest/amplify/backend/api/userdbtest/schema
Successfully updated resource

`amplify push`
