## Add accuknox repository to install UI on VM

```sh
helm repo add accuknox-onprem-ui  https:/USERNAME:PASSWORD@agents.accuknox.com/repository/accuknox-ui
helm repo update
helm search repo accuknox-onprem-ui
helm pull accuknox-ui/ui-build --untar
```

Step 1 : Install nginx application on VM

Step 2: Configure the certmanager(https)(eg: letsencrypt) 

Step 3: tar -xvf build.tar.gz

Step 4: sudo cp -rvf build/* /usr/share/nginx/html/ 

Step 5: Start the service

