# Build a Powerful Home SIEM Lab Elastic SIEM 
# Build a Home SIEM Lab (Elastic SIEM)

In this guide, you will learn how to set up a home lab for Elastic Stack Security Information and Event Management (SIEM) using the Elastic Web portal and a Kali Linux VM. The guide includes steps to generate security events on the Kali VM, set up an agent to send data to the SIEM, and query and analyze the logs in the SIEM. Completing this project can enhance your resume and provide valuable experience to discuss in interviews.

## Prerequisites
Before we get started, make sure you have the following:
- VirtualBox or VMware
- Basic knowledge of Linux and virtualization software

## Overview of the steps
1. Set up a free Elastic account.
2. Install the Kali VM.
3. Configure the Elastic Agent on the Linux VM to collect the logs and forward them to the SIEM.
4. Generate security events on the Kali VM.
5. Query to find the security events in the Elastic SIEM.
6. Create a Dashboard to visualize security events.
7. Create alerts for security events.

## Step 1: Set up an Elastic Account

To begin, you need to create a free Elastic Cloud account to run the SIEM. Follow these steps:
1. Sign up for a free trial at [Elastic Cloud](https://cloud.elastic.co/).
2. Log in to the Elastic Cloud console.
3. Click on “Start your free trial.”
4. Click “Create Deployment” and choose “Elasticsearch” as the deployment type.
5. Select a region and deployment size that fits your needs, then click “Create Deployment.”
6. Wait for the deployment configuration to complete.
7. Once ready, click “Continue.”

## Step 2: Setting Up the Linux VM

To set up the Linux VM, follow these steps:
1. Download the Kali Linux VM from the [official Kali website](https://www.kali.org/downloads/).
2. Create a new VM using the Kali VM file in your chosen virtualization software such as VirtualBox or VMware.
3. Start the VM and follow the installation prompts.
4. Once the installation is complete, log in using "kali" as both the username and password.

*Note: If you encounter difficulties, search for "How to create a virtual machine using VirtualBox/VMware with a Kali VM file" on YouTube for additional guidance.*

## Step 3: Setting Up the Agent to Collect Logs

1. Log in to your Elastic SIEM instance.
2. Navigate to the Integrations page by clicking on the Kibana main menu at the top left and selecting “Integrations” at the bottom.

![Integrations Page](images/integrations_page.png)

3. Search for “Elastic Defend” and click on it to open the integration page.

![Elastic Defend](images/elastic_defend.png)

4. Click on “Add Elastic Defend” and follow the on-screen instructions to install the agent on your Kali VM.

![Add Elastic Defend](images/add_elastic_defend.png)

5. Under Linux Tar, copy the command which will be pasted in the Kali terminal.

![Linux Tar Command](images/linux_tar_command.png)

6. Confirm incoming data at the Add the Integration stage.

![Confirm Incoming Data](images/confirm_incoming_data.png)

7. Paste the command into the Kali terminal.

8. After installing the agent, which takes a few minutes, a message will confirm the successful installation. The agent will then start collecting and forwarding logs to your Elastic SIEM instance.

9. You can check if the agent is installed correctly by running the command: `sudo systemctl status elastic-agent.service`.

*Note: If you encounter an error while installing the agent, ensure that your Kali is connected to the internet by pinging google.com before continuing.*

## Step 4: Generating Security Events on the Kali VM

To ensure the agent is functioning properly, you can generate some security-related events on your Kali VM using Nmap:
1. If you're not using Kali, install Nmap on your Linux VM (`sudo apt-get install nmap`).
2. To scan the Kali machine, run the command: `sudo nmap <vm-ip>`.
3. To generate more data, conduct additional Nmap scans using commands such as `nmap -sS <ip address>`, `nmap -sT <ip address>`, and `nmap -p- <ip address>`.

## Step 5: Query to Find the Security Events in the Elastic SIEM

1. Within your Elastic Deployment, click on the menu icon at the top-left corner (three horizontal lines).
2. Navigate to the "Logs" tab under "Observability" to view the logs from the Kali VM.

![Observability Logs](images/observability_logs.png)

3. In the search bar, enter a search query to filter the logs (e.g., `event.action: "nmap_scan"` or `process.args: "sudo"`).

![Search Query](images/search_query.png)

4. Click the "Search" button to execute the query.
5. The search results will be displayed in the table below. To view more details about a specific event, click on the three dots next to it.

## Step 6: Create a Dashboard to Visualize the Events

1. Navigate to the Elastic web portal.
2. Click on the menu icon at the top-left corner.
3. Under "Analytics," click on "Dashboards."

![Dashboards](images/dashboards.png)

4. Click on the "Create dashboard" button at the top right to start a new dashboard.
5. Click on the "Create Visualization" button to add a new visualization to the dashboard.
6. Select "Area" or "Line" as the visualization type.
7. In the “Metrics” section of the visualization editor, select “Count” as the vertical field type and “Timestamp” as the horizontal field.

![Create Visualization](images/create_visualization.png)

8. Click the "Save" button to save the visualization and complete the settings.

## Step 7: Create an Alert

1. Click on the menu icon at the top-left corner, then under “Security” click on “Alerts.”
2. Click on “Manage rules” at the top right.

![Manage Rules](images/manage_rules.png)

3. Click on the "Create new rule" button at the top right.

![Create New Rule](images/create_new_rule.png)

4. In the "Define rule" section, select the "Custom query" option from the dropdown menu.
5. Under "Custom query," set the conditions for the rule (e.g., `event.action: "nmap_scan"`).
6. In the "About rule" section, give your rule a name and a description (e.g., Nmap Scan Detection).
7. Set the severity level for the alert and keep all the other default settings under "Schedule rule."
8. In the "Actions" section, select the action you want to take when the rule is triggered (e.g., send an email notification).
9. Finally, click the "Create and enable rule" button to create the alert.

## Conclusion

In this project, we set up a home lab using Elastic SIEM and a Kali VM. We forwarded data from the Kali VM to the SIEM using the Elastic Beats agent, generated security events on the Kali VM using Nmap, and queried and analyzed the logs in the SIEM through the Elastic web interface. We also created a dashboard to visualize security events and set up an alert to detect specific security events.

This home lab offers a valuable environment for learning and practicing skills necessary for effective security monitoring and incident response using Elastic SIEM. By following these steps, you can gain hands-on experience with a SIEM, enhancing your security monitoring skills and helping you become a proficient security analyst or engineer.

## Next Steps
1. Generate and query different security events.
2. Test the alert by running Nmap scans on the Kali VM.
3. Learn analysis and visualization tools provided by Elastic SIEM.
4. Explore integrations and data sources available for Elastic SIEM.

### Add to Your CV:
- **Elastic Stack SIEM Configuration and Management:** Successfully set up and configured Elastic Stack SIEM in a home lab environment.
- **Visualization and Alerting in SIEM:** Developed a custom dashboard in Elastic SIEM and created and tested alert rules for detecting specific security events.
