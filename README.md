# Output-2.5-Vagrant-demo
Output 2.5 Vagrant-demo


## Prerequisites
To work with this project you need to have the following installed on your local machine

1. [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
2. [Vagrant](https://www.vagrantup.com/downloads.html/)

## Install and run locally

```bash
$ git clone https://github.com/wombolo/Output-2.5-Vagrant-demo.git
$ cd Output-2.5-Vagrant-demo
```
To start the box you need to run the command
```bash
$ vagrant up 
```

Then access the guest OS via ssh, like so
```bash
$ vagrant ssh
```

# How to Create a Server
In this submission, I capture various portions of the configuration file to outline their responsibilities.

![](Output%202.5%20Create%20a%20Server/Picture1.png)

Firstly, I have to create a folder to store the Vagrant config file, titled: Output 2.5. Then, I run the command ‘**vagrant init**’,this will create a ‘Vagrantfile’ file which will store all the necessary configurations needed by Vagrant.

![](Output%202.5%20Create%20a%20Server/Picture2.png)



All I had to do was to modify the ‘Vagrantfile’ to achieve my goal of creating a server. Line 8 in the above screenshot specifies the version of vagrant configuration I’ll be using. While line 15 indicates the vagrant box flavour I will use, which is ubuntu/bionic64.

![](Output%202.5%20Create%20a%20Server/Picture3.png)



Line 22 above indicates rules for port forwarding between the host O.S. and the guest O.S. This implies that port 80 on the guest OS can be accessed via port 8080 on the host.
![](Output%202.5%20Create%20a%20Server/Picture4.png)

Line 27 above indicates a private network initialization between the host and the guest and the guest can be located at 192.168.33.10 on the network. This can only be accessed by the host.
Protocols like ssh and ftp can make use of this IP address to work with the guest OS.


![](Output%202.5%20Create%20a%20Server/Picture5.png)


The above screenshot instructs vagrant to make use of the provider: Virtualbox. Other examples of providers include VMWare, Hyper-V, Docker, etc.

Furthermore, provider specific options on lines 41 and 44 instructs vagrant to display the VirtualBox GUI when starting the guest OS and to allocate 1024MB of R.A.M. to the guest OS respectively.


![](Output%202.5%20Create%20a%20Server/Picture6.png)



Lines 50 – 53 instructs vagrant to run the specified set of instructions in the guest OS immediately after setting up the guest OS. In this instance however, the guest will update all software provided in the box to their respective latest versions and then install the apache2 server.
External shells scripts and configuration files for docker, chef, etc. can also be provided and they will be implemented by vagrant.

![](Output%202.5%20Create%20a%20Server/Picture7.png)

After saving the configuration file, I ran the command _vagrant up_in order to execute vagrant with the provided Vagrant configuration file. This will download the ubuntu image file from the vagrant repo of images and then configure the image with the configuration parameters specified in the Vagrant configuration file.

![](Output%202.5%20Create%20a%20Server/Picture8.png)

Upon successful provisioning of the guest OS, I the run ‘vagrant ssh’ command, which is a short form of writing “ssh  [vagrant@192.168.33.10](mailto:vagrant@192.168.33.10)  -I PATH_TO_SSH_KEY”, in order to access the guest OS via a secure shell. 
Afterwards, the username and the hostname changes to vagrant@ubuntu-bionic to indicate successful login to the guest OS.


![](Output%202.5%20Create%20a%20Server/Picture9.png)



-* A screenshot of Apache default page accessed at localhost:8080.

