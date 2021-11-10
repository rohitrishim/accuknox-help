## Prerequisites:  

<b>Install below packages</b>
 
    1. node version v12+  
    2. npm  version  6+
    3. Yarn version 1.17+

<b>For your reference:</b>
     
[https://nodejs.org/en/](https://nodejs.org/en/)
[https://yarnpkg.com/getting-started/install](https://yarnpkg.com/getting-started/install)
[https://docs.npmjs.com/cli/v7/commands/npm-install](https://docs.npmjs.com/cli/v7/commands/npm-install)


## Git Clone the Onprem UI
```sh
git clone https://USERNAME:PASSWORD@github.com/accuknox/accuknox-onprem.git
git checkout accuknox-onprem-ui
```


## Steps to install Accuknox UI 

Step 1 : $yarn install

Step 2 : Need to add the new API- base URL path (path to gateway) in two places in the below project files..
      
        a) LINE 1: ui-app/app/src/constants/urls.ts

        b) LINE 7: ui-app/platform-ui/src/api/custom.js

             Eg: const baseAPIPath = 'https://api-dev.accuknox.com'; 
                  change the above api as per your Environment <https://api.example.com>

Step 3 : $npm run build

     3.1 :  optional (Command to remove existing code) 

            Eg: $gsutil -m rm -r gs://accuknox-ui/build/*

Step 4: Pushing build files from apps/build to <b>GCP bucket(aws or azure bucket)</b> 

            Eg: $gsutil -m cp -r app/build/* gs://accuknox-ui/build/


<b> Note : Step 4 will vary for different cloud providers </b> 


Step 5 : Install nginx application on VM

Step 6 : Configure the certmanager(https) 
        
           Eg: letsencrypt Tool

Step 7 : tar -xvf build.tar.gz

Step 8 : sudo cp -rvf build/* /usr/share/nginx/html/

Step 9 : Start the service
