
# 1 Machine Family  and Machine Type


Different Machine Families for Different Workloads 
- General Purpose (E2, N2, N2D, NI) : Best price-performance ratio
    - Web and application servers, Small-medium databases, Dev environments
- Memory Optimized (M2, MI): Ultra high memory workloads
    - Large in-memory databases and In-memory analytics
- Compute Optimized (C2): Compute intensive workloads
    - Gaming applications

Machine Type 
![](image/Pasted%20image%2020241111070314.png)


Let's take an example : e2-standard-2:
e2 - Machine Type Family
standard - Type of workload
2-NumberofCPUs


# 2 Internal and External IP Addresse 

- External (Public) IP addresses are Internet addressable.
- Internal (Private) IP addresses are internal to a corporate network
- You CANNOT have two resources with same public (External) IP address.
    - HOWEVER, two different corporate networks CAN have resources with same Internal (private) IP address
- All VM instances are assigned at least ond Internal IP address
- Creation of External IP addresses can be enabled for VM instances
    - (Remember) When you stop an VM instance, External IP address is lost
    - ==restart vm instance 后, external IP are ressigned , (a different IP addresse)==


# 3 Static IP address 

Static IP address  is a constant External IP Address for a VM instance 

Static IP can be switched to another VM instance in same project
Static IP remains attached even if you stop the instance. You have to manually detach it.
Remember : You are billed for an Static IP when you are NOT using it as well!   不用也是要付钱的


## 3.1 具体操作 

![](image/Pasted%20image%2020241111072814.png)


电视 Reserve Static address 去 创造一个新的 static address 
![](image/Pasted%20image%2020241111072916.png)


点击右边的 change, 然后 attach this static ip address to a vm instance 
![](image/Pasted%20image%2020241111073150.png)





# 4 Startup script 

![](image/Pasted%20image%2020241111074413.png)




# 5 instance Templates 

- Why do you need to specify all the VM instance details (Image, instance type etc) every time you launch an instance?
    - How about creating a Instance template?
    - Define machine type, image, labels, startup script and other properties
- Used to create VM instances and managed instance groups
    - Provides a convenient way to create similar instances
- CANNOT be updated
    - To make a change, copy an existing template and modify it
- (Optional) Image family can be specified (example - debian-9):
    - Latest non-deprecated version of the family is used


![](image/Pasted%20image%2020241111074636.png)


![](image/Pasted%20image%2020241111074829.png)



# 6 Sole-tenant-nodes 

You want dedicated hardware for your compliance, licensing, and management needs
_Sole_-_tenant nodes_ can help you meet dedicated hardware requirements for bring your own license (BYOL) scenarios that require per-core or per-processor licenses.

![](image/Pasted%20image%2020241111104143.png) 

![](image/Pasted%20image%2020241111104237.png)


![](image/Pasted%20image%2020241111104257.png)






