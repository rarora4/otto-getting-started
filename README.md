## Synopsys

**_Otto_** is a developer's dream, it automatically builds a development environment tailored specifically for developer's application, with zero or minimal configuration. It knows how to develop and deploy any application on any cloud platform, all controlled with a single consistent workflow.

It detects the type of application you're developing and configures that development environment for you. For example, if you're developing a PHP application, Otto will automatically install PHP and other related tools for you. It automatically downloads, installs, configures, and starts dependencies in your development environments for you.

## What we think

We think Otto is management tool for the HashiCorp because if you go through the project documentation you would relaize that it is actually making use of it existing offerings and binding them. What we mean is it uses Vagrant to create a VM instance, uses Terraform to launch servers, consul to confirgure services. So earlier user was responsible for carrying out all these tasks (using pre-existing tools), not Otto is a level of abstraction above all these tools that binds them and helps developers in getting their services up and running instantaneously.

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

## References

 * [Otto](https://ottoproject.io/docs/index.html) For getting to know Otto


