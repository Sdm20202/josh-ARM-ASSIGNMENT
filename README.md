# josh-ARM-ASSIGNMENT
# Azure Virtual Machine Deployment Using ARM Template

## Project Overview

This project demonstrates how to deploy an Azure Virtual Machine (VM) using an Azure Resource Manager (ARM) template. The ARM template automates the creation of Azure resources, ensuring consistency, repeatability, and efficient infrastructure deployment.

---

## Objective

The objective of this project is to:

- Create an ARM template using JSON.
- Deploy an Azure Virtual Machine.
- Configure networking resources.
- Apply security using a Network Security Group (NSG).
- Deploy resources automatically using Azure Resource Manager.
- Verify successful deployment.

---

## Resources Created

The ARM template deploys the following Azure resources:

- Resource Group
- Virtual Machine (Ubuntu Server 22.04 LTS)
- Virtual Network (VNet)
- Subnet
- Network Interface (NIC)
- Public IP Address
- Network Security Group (NSG)

---

## Project Files

```
Azure-VM-ARM-Template/

│── azuredeploy.json
│── azuredeploy.parameters.json
│── README.md
│── screenshots/
      │── 01-resource-group.png
      │── 02-template-deployment.png
      │── 03-deployment-success.png
      │── 04-virtual-machine.png
      │── 05-public-ip.png
      │── 06-vnet.png
      │── 07-network-interface.png
      │── 08-network-security-group.png
```

---

## ARM Template Features

The ARM template contains:

### Parameters

- Virtual Machine Name
- Location
- VM Size
- Administrator Username
- Administrator Password
- Virtual Network Name
- Subnet Name
- Public IP Name
- Network Interface Name
- Network Security Group Name

### Variables

The template uses variables to reduce duplication and improve readability.

### Resources

The following resources are deployed:

- Microsoft.Compute/virtualMachines
- Microsoft.Network/publicIPAddresses
- Microsoft.Network/networkInterfaces
- Microsoft.Network/networkSecurityGroups
- Microsoft.Network/virtualNetworks

### Outputs

The deployment returns:

- Virtual Machine Name
- Public IP Address
- Resource ID

---

## Deployment Steps

### Step 1

Log in to the Azure Portal.

### Step 2

Create a new Resource Group.

### Step 3

Open **Deploy a custom template**.

### Step 4

Upload the **azuredeploy.json** template.

### Step 5

Upload or configure the **azuredeploy.parameters.json** file.

### Step 6

Enter required parameter values if prompted.

### Step 7

Review and validate the deployment.

### Step 8

Click **Create**.

### Step 9

Wait for deployment to complete successfully.

### Step 10

Verify all deployed resources.

---

## Networking Configuration

Virtual Network

- Address Space: 10.0.0.0/16

Subnet

- Address Prefix: 10.0.0.0/24

Network Security Group

Inbound Rules:

- SSH (Port 22) for Linux

or

- RDP (Port 3389) for Windows

---

## Virtual Machine Configuration

Operating System

Ubuntu Server 22.04 LTS

VM Size

Standard_B1s

Authentication

Administrator Username and Password

Operating System Disk

Standard SSD

---

## Validation

Deployment was verified by confirming:

- Resource Group created successfully.
- Virtual Machine deployed successfully.
- Public IP assigned.
- Virtual Network created.
- Network Interface attached.
- Network Security Group applied.
- Deployment status shows **Succeeded**.

---

## Screenshots

The repository includes screenshots showing:

- Resource Group
- ARM Template Deployment
- Successful Deployment
- Virtual Machine Overview
- Public IP Address
- Virtual Network
- Network Interface
- Network Security Group

---

## Challenges Encountered

During deployment, template validation errors were resolved by correcting parameter values and ensuring resource dependencies were properly configured using the **dependsOn** property.

---

## Lessons Learned

Through this project, I learned how to:

- Create ARM templates.
- Automate Azure infrastructure deployment.
- Use parameters and variables.
- Configure networking resources.
- Manage Azure Virtual Machines.
- Apply Network Security Groups.
- Validate ARM template deployments.

---

## Conclusion

This project demonstrates how Azure Resource Manager templates can automate cloud infrastructure deployment. Using ARM templates improves consistency, reduces manual configuration, and simplifies Azure resource management.
{
    "apiVersion": "2025-04-01",
    "id": "/subscriptions/3c711d96-fa08-4238-9568-38f3db39c7c5/resourceGroups/JOSH-RG/providers/Microsoft.Compute/virtualMachines/JOSH-VM",
    "name": "JOSH-VM",
    "type": "microsoft.compute/virtualmachines",
    "location": "eastus",
    "zones": [
        "2"
    ],
    "properties": {
        "hardwareProfile": {
            "vmSize": "Standard_D2s_v3"
        },
        "provisioningState": "Succeeded",
        "vmId": "b4894618-3338-49d4-90dd-eeb64b33c8ec",
        "additionalCapabilities": {
            "hibernationEnabled": false
        },
        "storageProfile": {
            "imageReference": {
                "publisher": "canonical",
                "offer": "ubuntu-24_04-lts",
                "sku": "server",
                "version": "latest",
                "exactVersion": "24.04.202606060"
            },
            "osDisk": {
                "osType": "Linux",
                "name": "JOSH-VM_OsDisk_1_2c613353a4904cc3b75912ecf16cec64",
                "createOption": "FromImage",
                "caching": "ReadWrite",
                "managedDisk": {
                    "storageAccountType": "Premium_LRS",
                    "id": "/subscriptions/3c711d96-fa08-4238-9568-38f3db39c7c5/resourceGroups/JOSH-RG/providers/Microsoft.Compute/disks/JOSH-VM_OsDisk_1_2c613353a4904cc3b75912ecf16cec64"
                },
                "deleteOption": "Delete",
                "diskSizeGB": 30
            },
            "dataDisks": [],
            "diskControllerType": "SCSI"
        },
        "osProfile": {
            "computerName": "JOSH-VM",
            "linuxConfiguration": {
                "disablePasswordAuthentication": false,
                "provisionVMAgent": true,
                "patchSettings": {
                    "patchMode": "ImageDefault",
                    "assessmentMode": "ImageDefault"
                }
            },
            "secrets": [],
            "allowExtensionOperations": true,
            "requireGuestProvisionSignal": true,
            "adminUsername": "sdglobal"
        },
        "networkProfile": {
            "networkInterfaces": [
                {
                    "id": "/subscriptions/3c711d96-fa08-4238-9568-38f3db39c7c5/resourceGroups/JOSH-RG/providers/Microsoft.Network/networkInterfaces/josh-vm836_z2",
                    "properties": {
                        "deleteOption": "Delete"
                    }
                }
            ]
        },
        "diagnosticsProfile": {
            "bootDiagnostics": {
                "enabled": true
            }
        },
        "timeCreated": "2026-07-02T21:06:04.97Z"
    },
    "etag": "\"2\""
}
