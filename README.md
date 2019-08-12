# Node Red Docker Azure Web App

This repositoty contains a docker image of node red that can run on an Linux Azure Web App with docker deployment. Originally forked from https://github.com/sjkp/node-red-docker-azurewebapp.

# DockerHub image

This script automaticalluy generates a new updated docker image (https://cloud.docker.com/repository/docker/michelpf/nodered-azure-webapp-docker) ready to use.

## Deploy directly to Azure WebApp Docker Linux

Create a new WebApp application with docker deployment. Use public image with this address _nodered-azure-webapp-docker_.

After the deployment, make sure to enable local storate. Usually dockers under WebApp are stateless.
In order to enable local storage, go to _Configurations_ then set the variable ```WEBSITES_ENABLE_APP_SERVICE_STORAGE```to ```True```.

## Managing local storage

To access the local storage, by the local volume mounted, you need to use Kudu utility to access and to upload the files.
It's common to add security on installations like that, so you need to edit the ```settings.js``` file in ```site/data```
folder.

Upload files using Kudu requires API access. Before, make sure you setup the creditials in _Deployment Credentials_. 
Using any _rest_ utility like Postman, make a ```PUT``` request using the credentiais (_Basic Auth_), the route is the path of file (e.g. ```https://<endpoint>.scm.azurewebsites.net/vfs/data/settings.js```).

