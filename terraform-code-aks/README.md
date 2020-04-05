Terraform tracks state locally via the terraform.tfstate file. This pattern works well in a single-person environment. In a multi-person environment, Azure storage is used to track state.

1. In the Azure portal, select All services in the left menu.

2. Select Storage accounts.

3. On the Storage accounts tab, select the name of the storage account into which Terraform is to store state. For example, you can use the storage account created when you opened Cloud Shell the first time. The storage account name created by Cloud Shell typically starts with cs followed by a random string of numbers and letters. Take note of the storage account you select. This value is needed later.

4. On the storage account tab, select Access keys.

5. Make note of the key1 key value. (Selecting the icon to the right of the key copies the value to the clipboard.)

6. az storage container create -n tfstate --account-name <YourAzureStorageAccountName> --account-key <YourAzureStorageAccountKey>


To Create the Kubernetes cluster


1. In Cloud Shell, initialize Terraform. Replace the placeholders with appropriate values for your environment.

Command: terraform init -backend-config="storage_account_name=<YourAzureStorageAccountName>" -backend-config="container_name=tfstate" -backend-config="access_key=<YourStorageAccountAccessKey>" -backend-config="key=codelab.microsoft.tfstate" 

The terraform init command displays the success of initializing the backend and provider plug-in:

2. Run the terraform plan command to create the Terraform plan that defines the infrastructure elements.

Command: terraform plan -out out.plan

3. Run the terraform apply command to apply the plan to create the Kubernetes cluster. The process to create a Kubernetes cluster can take several minutes, resulting in the Cloud Shell session timing out. If the Cloud Shell session times out, you can follow the steps in the section "Recover from a Cloud Shell timeout" to enable you to complete the tutorial.

command : terraform apply out.plan

4. In the Azure portal, select All resources in the left menu to see the resources created for your new Kubernetes cluster.


