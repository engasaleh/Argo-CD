First thing I need you to know, An Application can create from ArgoCD UI or ArgoCD CLI ... so here I'm gonna tackle to show the two ways ☺ 


1- The ArgoCD UI

- After installation ArgoCD and expose it via command "kubectl port-forward -n argocd svc/argocd-server 8080:443" to open it local on your machine, you will be forwarded to a Web UI for ArgoCD, from Dashboard you can select "New APP" and fulfill the labels for create an ew application such as:-
   -> Name of the Application
   -> Project
   -> Sync Policy [Manual or Automatic]

Then for Source Section:
   -> Repo URL/Git Repo
   -> Branch
   -> Path


Also, Destination Section 
    -> Cluster URL 
    -> Namespace

After you did that, you can click on Create button.





## ===========================================================================================================================================================================


The Second way, through ArgoCD CLI

```bash
argocd app create {app-name} \
--project {project} like as mentioned before default or you can customize it based on what you need 
--repo {Git Repo}  \
--path  {App Folder} \
--dest-namespace {NameSpace} \
--dest-server {Server-URL}




# To list apps thatb create it .. you can execute this command to list it/them:

```bash 
argocd app list
```


# Also, If you want to get more information about the application you can use this command:

```bash
argocd app get {App Name}


