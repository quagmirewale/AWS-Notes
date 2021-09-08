## Create a VPC using the console

1. In the navigation pane, choose "Your VPCs", Create VPC.

2. Specify the following VPC details as needed.

```
Name tag: (Optional) provide a name for your VPC.

IPv4 CIDR block: Specify an IPv4 CIDR block for the VPC. The smallest CIDR block you can specify is /28, and the largest is /16\. For example, 10.0.0.0/16, or 192.168.0.0/16.

IPv6 CIDR block: (Optional/Default) associate an IPv6 CIDR block with your VPC. Choose one of the following options, and then choose Select CIDR:

Tenancy: (Optional/Default) Select a tenancy option. Dedicated tenancy ensures that your instances run on single-tenant hardware.

Click Create.
```
## Create a subnet in your VPC

* To add a new subnet to your VPC, you must specify an IPv4 CIDR block for the subnet from the range of your VPC. You can specify the Availability Zone in which you want the subnet to reside. You can have multiple subnets in the same Availability Zone.

* You can optionally specify an IPv6 CIDR block for your subnet if an IPv6 CIDR block is associated with your VPC.

* To create the subnet in a Local Zone, or a Wavelength Zone, you must enable the Zone.

To add a subnet to your VPC using the console
````
1. Open the Amazon VPC console.

2. In the navigation pane, choose Subnets, Create subnet.

3. Specify the subnet details as necessary and choose Create.

    -VPC ID: Choose the VPC for which you're creating the subnet.

    -Subnet name: Optionally provide a name for your subnet.
    
    -Availability Zone: Optionally choose a Zone in which your subnet will reside, or leave the default No Preference to let AWS choose an Availability Zone for you.

    -IPv4 CIDR block: Specify an IPv4 CIDR block for your subnet, for example, 10.0.1.0/24. 

    - IPv6 CIDR block: (Optional) If you've associated an IPv6 CIDR block with your VPC, choose Specify a custom IPv6 CIDR. Specify the hexadecimal pair value for the subnet, or leave the default value.

    (Optional) If required, repeat the steps above to create more subnets in your VPC.
````

After you create a subnet, you can do the following:
````
    Make your subnet a public subnet: 
        1. Open the Amazon VPC console.
        2. In the navigation pane, choose Internet Gateway, click create Internet Gateway
        3. In the name tag type in name.
        4. Click create Internet Gateway
        5. Go back to Internet Gateway navigation pane
        6. Select the newly created Internet Gateway, click Actions, from the drop down click Attach to VPC
        7. In the VPC navigation pane click Route Tables
        8. Select the Route Table for the VPC, click Actions and select Edit Routes.
        9. In the destination section select Add Route, in Destination add 0.0.0.0/0, in Target add the Internet Gateway attached to the VPC and click save changes.
        Add route to the internet gateway. 
        Create a custom route table.

    Modify the subnet settings to specify that all instances launched in that subnet receive a public IPv4 address, or an IPv6 address, or both. 

    Create or modify your security groups as needed. 

    Create or modify your network ACLs as needed. 

    Share the subnet with other accounts. 
````