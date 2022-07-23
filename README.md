# log4jScan

A burp plugin used to help enterprises quickly scan log4j's jndi vulnerabilities.
I found this on twitter and decided to translate it in english. All credits go to [https://github.com/sobinge][sobinge]

# Disclaimer

This tool should only be used on your own systems or systems that you have permission to test

You are responsible for your actions. You are responsible for any direct or indirect consequences and losses caused by the use of this tool and/or the information provided in this repository. The author and me do not assume any responsibility for anything.

The original author holds the right to modify and interpret this tool. Without the permission of the network security department and relevant departments, you may not use this tool to conduct testing or attacks. You may not use it for commercial purposes in any way.

# Introduction

log4jScan is a burpsuite plugin for identifying log4j vulnerabilities

This plugin will detect incoming request packets from BurpSuite

The current functions are as follows
- Remote command execution

# detection rules

Currently only the following types are supported to scan for jndi vulnerabilities in log4j

- GET
- POST
- Cookies
- JSON
- Xml
- Body
- Header

# caution!!!!

<font color=red>After downloading, be sure to open /resources/config.yml to see the configuration file, there are many custom functions in it, you can choose freely!!</font>

It is recommended to use a burp2.x version, because in the new version of burp, passive scanning is automatically multi-threaded, so the scanning speed will be much faster.

Please download the source code by yourself and compile it with the same version of jdk as BurpSuite, thank you

# compile method

<details>
<summary><b>Compile method</b></summary>

This is a java maven project

Import the idea and open the source code that was just downloaded

![](./images/1.png)

Open: /log4jScan/pom.xml to install the corresponding package. It takes a long time to install the dependency packages for the first time, so don’t rush it.

![](./images/2.png)

![](./images/3.png)

Compiled file location: /log4jScan/target/log4jScan/

Jar package location: /log4jScan/target/log4jScan/log4jScan.jar

Project configuration file location: /log4jScan/target/log4jScan/resources/config.yml

Then import the jar file into BurpSuite

</details>

# installation method

![](./images/4.png)

![](./images/5.png)

![](./images/6.png)

# Instructions

Browse the website, and if a request from the site occurs, the plugin will try to detect

After the access is completed, the plug-in will automatically scan

If there is a finding, the plugin will display it in the following places
- Tag
- Extender
- Scanner-Issue activity

# Question View

Here are a few places to check

![](./images/7.png)

![](./images/8.png)

![](./images/9.png)

# tag interface to view vulnerabilities

````
Vulnerabilities can now be viewed through the tag interface

will return respectively
- request parameter no eligible = request parameter is not eligible (controlled in scan type settings)
- the number of website problems has exceeded = exceeded
- the number of website scans exceeded = the number of website scans exceeded
- waiting for test results = waiting for test results
- [+] found log4j command execution = found log4j command execution
- [-] not found log4j command execution = No log4j command execution found
- [x] scan task timed out = scan task timed out
- [x] unknown error = unknown error
````

# Troubleshooting

What if there is a problem with the scan and I want to rescan?

For example, tag has the following problems:
- the number of website problems has exceeded = exceeded
- the number of website scans exceeded = the number of website scans exceeded

solution:
![](./images/11.png)

# How to switch the problem of dnslog

After compiling, enter the log4j folder, enter the resources directory, and open config.yml

as follows:
![](./images/12.png)

If you want to replace it with DnsLogCn/BurpDnsLog, you only need to replace the value of the provider with the corresponding value.

If you want to use Ceye, you need to do the following:

![](./images/14.png)

Get token and Identifier

Then open config.yml and fill it out as follows, how to reinstall the plugin:
![](./images/15.png)
