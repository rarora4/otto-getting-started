## Team

* Kumar Utsav
* Raman Preet Singh
* Rohit Arora
* Xavier Primus 

## Synopsys

**_Otto_** is a developer's dream, it automatically builds a development environment tailored specifically for developer's application, with zero or minimal configuration. It knows how to develop and deploy any application on any cloud platform, all controlled with a single consistent workflow.

It detects the type of application you're developing and configures that development environment for you. For example, if you're developing a PHP application, Otto will automatically install PHP and other related tools for you. It automatically downloads, installs, configures, and starts dependencies in your development environments for you.

## What We think

We think Otto is a DevOps management tool from HashiCorp because if you go through the project documentation you would relaize that it is actually making use of it existing offerings and binding them. What we mean is it uses Vagrant to create a VM instance, uses Terraform to launch servers, consul to confirgure services. So earlier user was responsible for carrying out all these tasks (using pre-existing tools), not Otto is a level of abstraction above all these tools that binds them and helps developers in getting their services up and running instantaneously.

## Key Features
* **Automatic development environments** by automatically detecting application type and services, and then building a development environment tailored specifically for that application and also configuring and starting required services in your development environment for you.

* **Built for Microservices** by understanding dependencies & versioning, then automatically deploying and configuring those dependincies for any enviornment.

* **Deployment:** It knows how to deploy applications and can deploy them in any enviornment.

* **Docker:** Otto can use Docker to download and start dependencies for development to simplify microservices. Applications can be containerized automatically to make deployments easier without changing the developer workflow.

* **Production-hardened tooling:** Otto automatically installs and manages production-hardened tooling to build development environments (Vagrant), launch servers (Terraform), configure services (Consul), and more.

## Installing Otto
Otto is pretty straight forward and easy to install. Don't believe me? Just find an appropiate binary package installer for your maching [here](https://ottoproject.io/downloads.html) and download it. After downloading Otto, unzip the package. Otto runs as a single binary named otto.

And, the final step is to make sure that otto is available on the PATH using:

On Linux/Mac
```
export PATH=$PATH:/path/to/dir
```

On Windows
```
1. Goto control panel -> System -> Advanced System settings* -> Environment Variables 
2. Scroll down in system variables until you find PATH click edit and path to Otto directory. 
3. BE SURE to include a semicolon at the end of the previous as that is the delimiter ie c:\path;c:\path2
```
That's it!

Now, verify you installation. Open a new terminal session and execute ```otto``` command, you should get something similar to below image:

![verify image](/images/image1.png)

## Develop

Lets develop a sample ruby project in this repository ([original source](https://github.com/hashicorp/otto-getting-started)). Run following commands in your terminal:

```
$ git clone https://github.com/rarora4/otto-getting-started.git
$ cd otto-getting-started
$ otto compile
$ otto dev
```

In this step Otto inspects the repository detects ruby application and automatically builds an enviornment tailored to Ruby development. Otto outputs instructions for working with the development environment in green. These are also tailored specifically to your application type. These instructions change for PHP, Node, etc.

To start this ruby application run: 

```
$ otto dev ssh
> bundle && rackup --host 0.0.0.0 
```

The second commands executed in vagrant VM. Then, in another terminal run the below command to get the ip address at which application is running and open the ip address with port ```9292```  (the default listening port for this application).

```
$ otto dev address
172.16.1.137
```

## Infrastructure

To deploy an application, Otto has three steps: start an infrastructure, build the application, and launch the application. In this step we would deploy the application to AWS (make sure you have AWS account setup or [create new one](http://aws.amazon.com/free/)). Then start by executing following command:

```
otto infra
```

This step would first install Terraform, and then ask for AWS credentials post which Otto will go forward and build you an infrastructure. This will take a few minutes. 

## See Where You Are

Lets stop for a minute and check status of your infrastructure by running:

```
otto status
```

### Build

The build step turns your application into a deployable unit, by deploying your application in the infrastructure we built in last step. So execute following command:

```
otto build
```

Again you can check the status using ```otto status```. See how simple it is!

## Finally Let's Deploy

After launching infrastructure, and building application, its time to deploy it. Execute the command (wanna guess...):

```
otto deploy
```

Otto will now take the AMI built in the previous step and launch a server in the infrastructure built previously. Otto will configure firewalls properly to secure the server if necessary.

## See It Running
After deployment, go to the IP of the instance and you will see the application running.

![running instance](/images/image2.png)

## Last Important Thing - Appfile

Hashicorp created a new configuration format for Otto that is expressive enough to solve all the mentioned shortcomings of Vagrant: the Appfile. It is a higher-level description focusing on the application. A complete example is shown below:

```
application {
  name = "otto-getting-started"
  type = "ruby"
}

project {
  name = "otto-getting-started"
  infrastructure = "otto-getting-started"
}

infrastructure "otto-getting-started" {
  type = "aws"
  flavor = "simple"
}
```
The Appfile is meant to describe everything required to develop and deploy an application. Otto with zero configuration only does the bare minimum possible for every application type, and is heavily opinionated. Writing an Appfile allows you to be explicit in how you want Otto to behave.

## Demo 

[Otto Screencast](https://youtu.be/X4Er8EZoUN0)

## References

 * [Otto](https://ottoproject.io/docs/index.html) For getting to know Otto


