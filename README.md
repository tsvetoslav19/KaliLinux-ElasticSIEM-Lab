
# KaliLinux-ElasticSIEM-Lab 

In this project, I set up a home lab for Elastic Stack SIEM using Elastic Cloud and a Kali Linux virtual machine (VM). The goal was to simulate a security monitoring environment where I could collect and analyze security events, create visualizations, and configure alerts for real-time monitoring.

## Setting Up Elastic Stack on Elastic Cloud
Created an Elastic Cloud account and set up a deployment. Created a deployment with Elasticsearch. Selected a region and size that matched my needs and waited for the deployment to complete.
## Installing and Configuring Kali Linux VM
For the lab environment, I used Kali Linux as the endpoint. I downloaded the pre-configured virtual machine from the official Kali website and imported it into VirtualBox. After booting up the VM, I completed the setup, using the default credentials provided.
## Installing the Elastic Agent
To send logs from Kali Linux to Elastic Stack, I installed the Elastic Agent. I logged into Kibana, went to the Integrations section, and found the Elastic Defend integration. I followed the setup instructions and copied the installation command for the Elastic Agent. On the Kali VM, I ran the command and confirmed that the agent was running successfully using sudo systemctl status elastic-agent.service.
## Generating Security Events
To test the setup, I generated logs by running Nmap scans from the Kali VM. Since Nmap is preinstalled on Kali, I used it to perform various scans against a target IP. For example, I ran commands like sudo nmap <ip> and sudo nmap -sS <ip> to simulate reconnaissance activity. This allowed me to create realistic security events for analysis in the SIEM.

![App Screenshot](https://i.imgur.com/rFEgVbG.png)

## Analyzing Logs in Elastic SIEM
Once the logs started flowing into Elastic Stack, I moved to the Logs section in Kibana. I searched for specific events, such as those related to Nmap, by using queries like event.action: "nmap_scan". This gave me a detailed view of the generated events, including timestamps, IP addresses, and other relevant metadata.
## Building a Dashboard
To visualize the collected data, I created a dashboard in Kibana. I added visualizations, such as bar charts, to display event trends over time. For the metrics, I used "Count" as the vertical axis and "Timestamp" as the horizontal axis. This helped me get a clearer picture of the activity patterns.

![App Screenshot](https://i.imgur.com/hgqjxgQ.png)
## Setting Up Alerts
To make the environment more interactive, I configured alerts. I created a custom rule in the Alerts section to monitor for specific queries, like Nmap scans. I defined the severity and set the alert to notify me via email when triggered.