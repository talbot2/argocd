# Argo CD Demo with vCluster

## Steps to reproduce:
  1. Run aks-create.yml Github Actions job to create the **argocd-main-aks** cluster inside of the **argocd-demo-rg** resource group.
     The aks-create job will install the latest versions of kubectl, helm, vcluster and argocd, as well as, deploying the Argo CD application and providing the login credentials

     ![image](https://github.com/talbot2/argocd/assets/99027661/4e3548b5-c52a-4cd1-9663-d90627d03515)

  3. Run the argocd-password.yml job to update the password from the intial password provided by Argo CD to a more secure permanent password. This job requires running the *argocd login* command.
     For this command to run successfully the user is required to input the Argo CD host IP address and the temporary password provided by Argo CD. These values have been provided as part of the aks-create job.

  4. Once the new password has been created you can run the vcluster-create.yml job to create a new virtual cluster inside of the main aks cluster. You are required to provide the host IP address of Argo Cd and
     and a name for the new environment. If no name is provided it will default to **vcluster-dev-aks**. You should see this cluster update on the Argo CD brower under the Cluster tab.

  5. Once the main and virtual clusters are no longer required you can run the aks-delete.yml job to delete the entire cluster.
