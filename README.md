# Deploy the Application over the AppEngine in GCP.

Here we have to decaler the app.yml file which will execute over the AppEngine under the GCP platform. 

runtime: python27:-   The runtime will confirm what kind of the application is being used under your project.

api_version: 1:-  The API version we would need to declared here.

threadsafe: true : For more info you may use the following URL:- https://cloud.google.com/appengine/docs/standard/python/config/appref


handlers:
- url: /
  static_files: website/index.html

This is basically being used where your exact code is being lying. In my case all of the static files are available under website folder.

# If we need to host the multiple application under APP Engine then we must need to decare the service name under app.yml

It will use the same name of the URL which we will declare under the service name. For example:- service: my-second-app

# Steps to Deploy the application under APP Engine.

gcloud init :-  This will basically Initialized the project & configuration

Again we would need to use the single deploy command for push the chnages.

gcloud app deploy   .. That's it Guys.


# Also, if we need to mentioned the autoscaling for handler the high traffic then we must need to include the following things under app.yml

This is easily done with services. When you deploy to App Engine define your app.yaml file with a line like: service: my-second-app

Complete app.yaml file for another Node.js service:

service: my-second-app
runtime: nodejs
env: flex
automatic_scaling:
   min_num_instances: 1
When you deploy, do it from the directory containing your app.yaml file:

gcloud app deploy
Or if you want to define your configuration in a yaml file just for your seond app:

gcloud app deploy my-second-app.yaml
The new service will be deployed along side your default service and will get it's own URL like:

https://my-second-app-dot-my-project-name.appspot.com


I think it is a good idea to have a picture (worth a thousand words) presenting Google App Engine services hierarchy.


![Image description](https://i.stack.imgur.com/NfZTg.png)

