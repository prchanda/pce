# Policy Compliance Evaluator
It's a small utility to trigger Azure Policy evaluation cycle on demand. During initial days, we need to rely on policy evaluation cycle to get the updated compliance results in Azure portal. But now we have an option to fire policy evaluation cycle whenever we want through a REST API. There are two REST APIs basically, one to start the policy evaluation cycle and other one is to check whether the scan has been completed or not. Policy scan can be run at subscription scope or at resource group level.

------------

Now, let's see how this tool (*Policy Compliance Evaluator*) will make our life easier. It's a commandline based tool which mainly takes 2 arguments, one is Azure Subscription Id and the other one is Resource Group name which is optional. So let's say if you want to run the evaluation scan at:

- Subscription scope

  #### `pce.exe -s "91897ffb-xxxx-xxxx-xxxx-4bb03c62ca8b"`

- Resource Group scope

  #### `pce.exe -s "91897ffb-xxxx-xxxx-xxxx-4bb03c62ca8b" -rg "AzureApps"`

------------

Why should I use PCE ?
----------------------

- PCE handles the authentication / authorization part of the REST APIs implicitly. You don't need to create an Azure Active Directory application to generate bearer token and invoke the REST APIs.
- PCE automatically reports back once the policy scan is completed, you don't need to manually query the status by invoking the respective REST API which differentiates the tool from other REST clients like Postman or Fiddler, etc.
- PCE helps you to run compliance scan at various scopes at the same time by running multiple instances of it.
- PCE lets you to change the AAD authentication context on the fly using a commandline parameter [-t].
