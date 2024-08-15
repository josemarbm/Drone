# Drone Install


**Create the OAuth authentication in an SCM platform.**

Go to your GitHub account and navigate to the[ developers settings](https://github.com/settings/developers) and select the OAuth apps from the left menu. Click on the “New OAuth App” button and fill up the fields. Here you will need the hostname where Drone is deployed. The call back URL *must* end with “/login”:

![img](https://miro.medium.com/v2/resize:fit:529/0*LjHOsT6hez870y7-)

Click on the “Register Application” button. On the next screen, click on the “Generate a new client secret” button, then put your password when asked to generate a new access secret:

![img](https://miro.medium.com/v2/resize:fit:700/0*hXZJN8-J2WYS1Jxt)

Take note of the Client ID and secret.

**Configure the Drone server and runners.**

Server configuration is done using environment variables. To simplify the setup, we are going to use *docker-compose*. Create a text file named *.env* to store the environment variables that will configure both server and runners, refer to the[ official documentation](https://docs.drone.io/server/reference/) for a more in depth explanation of them.

Add the following variables:

```
# Server configuration
DRONE_SERVER_HOST=drone-127.0.0.1.sslip.io
DRONE_SERVER_PROTO=http
DRONE_GITHUB_CLIENT_ID=git-hub-client-id
DRONE_GITHUB_CLIENT_SECRET=github-client-secret
DRONE_RPC_SECRET=740957c92d39a2320b9ed1a0152ed94b
DRONE_TLS_AUTOCERT=false
DRONE_USER_CREATE=username:josemarbm,admin:true
# Runners configuration
DRONE_RPC_HOST=drone #drone-127.0.0.1.sslip.io
DRONE_RPC_PROTO=http
DRONE_RUNNER_NAME="drone-runner" # It CANNOT contain spaces!
```

docker-compose up

Access web browser http://drone-127.0.0.1.sslip.io
