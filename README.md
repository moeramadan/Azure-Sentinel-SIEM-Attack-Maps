# Building a SIEM Solution with Azure Sentinel to Visualize Live Cyber Attacks

![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/99d524c5-281a-43ef-ab2b-364a8299d6bb)

## Learning Objectives:
- Configuration & Deployment of Azure resources such as virtual machines, Log Analytics Workspaces, and Azure Sentinel
- Proficiency in utilizing KQL to query logs and extracting valuable insights
- Hands-on experience in visualizing attack data on dynamic dashboards with Workbooks, including the creation of interactive World Maps
- Tools and Requirements:
  - Microsoft Azure Subscription
  - Azure Sentinel
  - Kusto Query Language (KQL)
  - Network Security Groups
  - Remote Desktop Protocol (RDP)
  - 3rd Party API: ipgeolocation.io
  - Custom Powershell Script ([Log Exporter Script](https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1))
- Operating System: Windows 10

## Step-by-Step Guide:

### Step 1: Create a Honeypot Virtual Machine
- Access Azure portal (portal.azure.com)
- Navigate to "virtual machines" and create a new Azure virtual machine in a new resource group named "honeypotlab"
- Configure instance details such as region, security, image, and size, and set up inbound port rules to allow RDP (3389)

![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/1b0f8345-71be-4356-8cef-77b16e7b033a)
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/25564c19-9de9-48e1-86a1-8d95e4990e27)
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/0899800e-c177-4009-9d0f-8c8e6e5bd02f)

### Step 2: Create a Log Analytics Workspace
- Create a Log Analytics workspace in the same resource group as the VM to ingest Windows Event Viewer logs and custom logs

### Step 3: Configure Microsoft Defender for Cloud
- Enable Cloud Security Posture Management and Servers protection in Microsoft Defender for Cloud settings
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/ed54d11e-67ed-48bc-a24a-13db6ace5979)
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/daea03a8-d69e-4703-ac7f-55456fb16eb9)

### Step 4: Connect Log Analytics Workspace to Virtual Machine
- Connect the Log Analytics workspace to the virtual machine to collect security logs
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/1cb7b100-fe6a-4b05-ae3a-75867cdd180f)

### Step 5: Configure Microsoft Sentinel
- Create Microsoft Sentinel and add the Log Analytics workspace to monitor security events
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/707e2b5b-afbd-42ea-8cab-f980f7f8b4a4)

### Step 6: Disable the Firewall in Virtual Machine
- Disable Windows Defender Firewall in the virtual machine settings to allow traffic for logging purposes
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/a63b7f51-f8da-4a88-b621-a603734c4b1a)

### Step 7: Scripting the Security Log Exporter
- Run the [Powershell script](https://github.com/joshmadakor1/Sentinel-Lab/blob/main/Custom_Security_Log_Exporter.ps1) in the virtual machine to continuously export security logs and extract geographic data using IP Geolocation API
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/e3d83222-4f4b-4c03-90c7-8506c9feb0e2)
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/e2f32b2e-93be-49fc-bb7a-d7aee751b39f)


### Step 8: Create Custom Log in Log Analytics Workspace
- Create a custom log in Log Analytics Workspace to import additional data from the IP Geolocation service
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/88f513ed-2b18-4aa5-a339-385c56693403)

### Step 9: Query the Custom Log
- Query the custom log in Log Analytics Workspace to analyze the ingested data
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/04eb62d2-b537-4460-b336-8b6d0858bd2c)
![image](https://github.com/moeramadan/Azure-Sentinel-SIEM-Attack-Maps/assets/155490852/5854e756-43f4-4e65-848b-25c4fc565e1b)


### Step 10: Map Data in Microsoft Sentinel
- Use KQL to query and visualize the data on dynamic dashboards in Microsoft Sentinel, including creating World Maps to pinpoint cyber threats

