FAQ

<details>
  <summary> What is puppet and puppet architect </summary><br><b>
  Puppet is configuration management and deployment tool. It's most commonly used on Linux and Windows to pull the strings on multiple application servers at once
  
  ![alt_text](https://puppet.com/docs/pe/2019.8/pe_architecture.png)
  
  </b></details>


<details>
  <summary> What is complie master and How to install puppet compile master </summary><br><b>
  Compilers typically run Puppet Server and PuppetDB services, as well as a file sync client. Older, legacy-style compilers must be converted in order to add PuppetDB.

When triggered by a web endpoint, file sync takes changes from the working directory on the master and deploys the code to a live code directory. File sync then deploys that code to all your compilers, ensuring that all masters in a multi-master configuration remain in sync. By default, compilers check for code updates every five seconds.

The certificate authority (CA) service is disabled on compilers. A proxy service running on the compiler Puppet Server directs CA requests to the master, which hosts the CA in default installations.

Compilers also have:

The repository for agent installation, pe_repo
The controller profile used with PE client tools
Puppet Communications Protocol (PCP) brokers to enable orchestrator scale
Logs for compilers are located at /var/log/puppetlabs/puppetserver/.

Logs for PCP brokers on compilers are located at /var/log/puppetlabs/puppetserver/pcp-broker.log

https://puppet.com/docs/pe/2019.8/installing_compilers.html#install_compilers
  
  </b></details>
  
 <detais>
  <summary> what is puppet manifest </summary><br><b>
  </b></details>
  
 <detais>
  <summary> what is puppet module </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet resources </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet facts </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet environment </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet life cycle </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet tuning </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet csr attributes </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet management console </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet hiera </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet code manager </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet site.pp </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet class </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet Puppetfile </summary><br><b>
  </b></details>
  
  
  
 <detais>
  <summary> what is puppet version </summary><br><b>
  </b></details>
  
  
  
 <detais>
  <summary> what is puppet ports </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> How to check puppet master,compiler,DB status </summary><br><b>
  </b></details>
  
  
 <detais>
  <summary> what is puppet manifest </summary><br><b>
  </b></details>
  
  
