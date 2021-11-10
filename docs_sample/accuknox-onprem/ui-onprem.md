## Steps to install Accuknox UI 

```sh
git clone https://USERNAME:PASSWORD@github.com/accuknox/accuknox-onprem.git
git checkout accuknox-onprem-ui
cd build
```

Step 1 : Install nginx application on VM

Step 2: Configure the certmanager(https)(eg: letsencrypt)

Step 3: tar -xvf build.tar.gz

Step 4: sudo cp -rvf build/* /usr/share/nginx/html/

Step 5: Start the service
