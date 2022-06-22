=== Enable dockerization in app & run container ===
1. Enable/add docker support and verify Dockerfile
2. Build the image using below command
> docker build -t demo-webapi .

# note: if build fails move Dockerfile to solution directory / app's root directory
# list images to verify
> docker images 

3. Run the container using this image
> docker run -d -p 8099:80 demo-webapi

# check container run status + portmapping
> docker ps

# browse url - http://localhost:8099/WeatherForecast to verify


=== Push image to a repository ===
# create tag based on docker repo name
> docker tag demo-webapi xxxx/demo-webapi

# push image
> docker push xxxx/demo-webapi

# note: Unable to push image to docker hub due to resitriction in my local network. So pushing image to ACR
# ACR repo url: xxxx.azurecr.io
# Before pushing the changes login to azure and azure acr - with registry name
> docker tag demo-webapi xxxx.azurecr.io/demo-webapi:latest
> docker push xxxx.azurecr.io/demo-webapi

# Once the image is pushed successfully, below logs will be printed
C:\Users\dhivya.d>docker push xxxx.azurecr.io/demo-webapi
Using default tag: latest
The push refers to repository [xxxx.azurecr.io/demo-webapi]
a2935d1e38a2: Pushed
5f70bf18a086: Pushed
1c07f429279b: Pushed
67a72db6b023: Pushed
1c2dcb7df4f3: Pushed
e715acc09394: Pushed
eafcccfc09dc: Pushed
ad6562704f37: Pushed
latest: digest: sha256:9d235fe1d8323506234ef52e3ad945bbfb6cc967a54ee083f79ca35d245abf76 size: 1995