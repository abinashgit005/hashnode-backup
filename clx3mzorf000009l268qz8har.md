---
title: "Green Cloud Computing"
datePublished: Sun Jan 14 2024 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clx3mzorf000009l268qz8har
slug: green-cloud-computing
tags: cloud-computing, data-center, green-cloud-computing

---

## **Abstract:**

Green computing refers to environmentally sustainable computing which minimizes the consumption of electricity as well as energy. It also reduces the harmful impact on the environment. Now a days cloud computing is growing faster than expected. Most of the companies are adapting cloud computing services as it provides high scalability and cost-effective infrastructure for any enterprises and web-applications, whereas green cloud computing emphasizes on making the cloud computing  more  energy efficient and reduce carbon footprints as well as (-e)waste.

Datacenters which provides cloud computing services have some factors like, huge amount of energy consumption, high operational cost and pollutes environment by carbon footprints which lead to energy shortage and global climate change. Our focus should be on maximizing utilization at minimum energy cost of the datacenter, so that we can get high service level at minimal cost.

#### Introduction:

In this era one of the major challenges to the mankind is dwindling of natural resources. The more we focus on developing technologies, the less we focus on the environment. As this paper is about green cloud computing, datacenters are the main constituent of it. Those large  scale data center comprises of hundreds and thousands of servers with other infrastructures such as cooling, storage and network systems. Cloud computing service providers deliver the services on the basis of a pay-as-you-go. cloud caters Iaas, Paas, [SaaS.It](http://SaaS.It) meets fluctuating demand by varying the resources and service requirements need of customer. It's very essential to structure a Service Level Agreement(SLA) and also Quality of Service(QoS) to provide reliable service to the customers. Cloud service providers have to meet the SLA and also maintain their Qos which focuses on availability, security and reliability.

#### What is Cloud Computing:

cloud computing is the on-demand available service model which provides computing resources (networks, servers, storage, applications and services) to the users. By using cloud computing users can use required services and pay as per their usage. This approach allows the user to use only that much of resources as they want instead of unnecessarily renting a complete setup, It also  provide facilities to modify the services as per their requirement.

They can either scale-up or scale-down as they need. It delivers services like Infrastructure as a service (IaaS), platform as a service (PaaS) and software as service (SaaS).

IaaS provides the computing infrastructure which includes servers, storage, networking infrastructure. In other words we can say it is a virtual datacenter. Clients can use the resources for multiple purposes. Client install operating system and their required tools on the infrastructure provided by the vender.

It is easier, cost-efficient and  convenient for a client to manage workloads without buying, managing and supporting the underlying infrastructure. Example : AWS, Microsoft Azure, Google compute engine

SaaS allows people to use cloud based web applications. Here a third party vender hosts  the applications  and make them available for  customers over the internet. Customers need not to install, configure the applications. SaaS providers take care about it.

SaaS provides facilities to the customers which reduces time as well as money spent on installing, managing, upgrading software. Example : Salesforce

PaaS allows third party vendor to deliver  hardware and software tools which can be used by clients to develop applications. It provides a platform for developing, testing, managing applications.

Example : Azure Functions, Azure Logic Apps

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717700619530/b182812e-c7ff-45f2-b4b3-a937c1856baf.png align="center")

#### Need of Cloud Computing :

Moving to cloud rather than establishing their own infrastructure is more convenient. The organizations can share their resources  geographically by cloud and they do not need different infrastructures for different locations. It saves time and resources which can be utilized in some other areas. Clients can get on-Demand Scalability options Where they can modify their requirement list.

Cloud computing has many advantages like Accessibility, cost efficiency, disaster recovery, Security and Scalability. Apart from that Cloud is leading today’s IT world as well as providing solutions for  problems in the fields of big data, cyber security and also has a platform for trending technologies like artificial intelligence.

It allows employees to telecommute. Companies hardly allows their staffs to work remotely because of the security risk which can arise while trying to connect to the enterprise network from outside. Cloud offers enterprises ability to secure their network  so that no security risk will arise. It helps to increase collaboration and productivity as well.

#### Making the Cloud green :

Although Datacenter plays an immense role in cloud computing, the other part is also much transparent where we can see how it effects the environment adversely. Data centers are rapidly growing  and they are also consuming 10 to 100 times more energy per square foot than typical office building.

Our Day to day activities, specially which involves technology produce carbon footprints. For example: an average spam email produces 0.3 g CO2e(carbon dioxide equivalent), a standard email produces 4g Co2e and an email with “long and tiresome attachments” produces 50 g CO2e carbon footprints. This indicates that it is our prime responsibility to observe the number of carbon footprints getting generated. Hence it is necessary for data centers, other organizations to implement green cloud computing.

Green Cloud computing is envisioned to achieve not only efficient processing and utilization of computing infrastructure, but to minimize energy consumption also. It's quite impossible to completely reduce carbon footprints produced by our daily activities, but it can be done incase of large data centers up to some extent. As the number of cloud users growing gradually, Cloud provider’s focus is on to fulfill the requirement.

Green data center is getting momentum as service providers realizing it’s importance in energy conservation. It can help to cut down data center’s energy costs and saves energy which results to save money.

Computing device manufacturer using such materials and chemicals which may cause nerve and immune reaction in human health whereas, the  green cloud computing techniques emphasize on using renewable energy source and less hazardous materials in computing devices which reduce the health risk. As it focuses on energy conservation means less energy used to produce, use and dispose the products which leads less expenditure of capitals

#### Some Energy conservation steps :

Since large number of computing devices are used in cloud data centers, increase in the number of devices is directly proportional to increase in energy consumption. Hence the energy conservation steps comes into picture. Computer system can reduce energy consumption and carbon emissions, but this potential reduction is partially offset by the power used by data centers and computer networks which runs into billions of dollars or euros. Thus a small number of power savings in computer systems could cause significant financial and carbon savings.Many approaches have been tried to make the cloud computing platform more environmental friendly. Some are described below.

#### Dynamic Voltage Frequency Scaling (DVFS):

Dynamic voltage frequency scaling is one of the technology for energy conservation, which allows software to dynamically alter the voltage of the processor. DVFS optimized the energy consumption of the server by changing the CPU voltage/frequency with out causing an adverse impact on performance. For example, let's consider a system has one task to complete and the workload requires only 10 cycles to execute, but the deadline associated with the task is 100s. Here the processor can slow down to 1/10 cycles/s, this leads to save the power as well as meet the deadline.

In DVFS the inappropriate rise in voltage/frequency may demand for more power. As the voltage/frequency decreases the number of instructions executed by the processor also may decrease, which increase the run time of CPU bound program segments. The execution time of a I/O bound program has no effect by the change of CPU speed. So changing in frequency of the server varies from task to task\[5\]. DVFS of CPU is applied for improving the energy consumption of the datacentre. The frequency of CPU is decided according to the workload by the resource controller, which is installed on each server\[6\]. DVFS has many limitation and still researchers on their way for it's improvision.

#### Catamos Server :

A catamos server(Zombie server) is a server that is powered and uses electrical energy without delivering any useful service. It has no external communications and visibility and contributes no compute resources. such servers may have been left when a certain project ended or a business process changed and since then the servers were no removed and no one is tracking them. other causes includes redundant and legacy applications and services that had been replaced. Lack of focus to identify  and removing the catamos servers cause to increase the number of catamos servers in the datacenters.

In some cases some organization perceived that, by removing any previously installed servers, they may effect the application functions that occasionally run on the servers.

#### Thermal Management :

In every Datacenter thermal management plays a vital role as it's very important to maintain a favorable temperature so that the servers will perform efficiently. High energy costs and huge carbon footprints are incurred due to the massive amount of electricity used to power and cool the numerous servers hosted in these data centers.

Thermal management is taken care by cooling process in the data centers by cooling units and fans, whose actions are controlled by the ambient temperature of a data center. Any increase in temperature would cause an increase in cooling energy. Therefore, the amount of heat produced by a server is an important consideration to manage energy consumption in data centers.

Datacenter authorities must adapt advanced cooling technologies rather than conventional methods, the air flow inside a datacenter has a significant impact on the cooling procedures. It must ensured that the needy servers only getting cooled instead of unnessaryly cooling all the servers which is  inefficacious.

Some DCs use their surrounding environment to transfer some part or even all of the produced heat. To avail this facility  some companies locate their DCs in colder climates (eg. Google’s Datacenter in Hamina, Finland ) In this DC, cold sea water is drwan  and passed  through the heat exchanger connected to the cooling loop of the DC. It is done in oredr to remove heat and then recombinine it with the sea water to bring its temperature down before allowing it to the sea.

There are different methods to maintain the thermal stability inside the data center.

#### Liquid Cooling :

Liquid cooling leads to reduce in energy consumption as liquid has high thermal capacity as compare to air. Once heat has been transferred to a liquid, it can be removed from the data center efficiently. The latest generation has come up with more efficient and effective cooling solutions. Liquid cooling system is not only cleaner but also more targeted and scalable. Compared with a traditional air-cooled system, the water-cooled system provides 30% energy savings. Taking a 40RT (Refrigeration Ton) system as an example, the power consumption can be decreased from 1.25kW/RT to 0.89kW/RT.\[9\]

The most common cooling designs are full immersion cooling and direct-to-chip cooling. Immersion systems involve submerging the hardware itself into a bath of non-conductive, non-flammable dielectric fluid. Both the fluid and the hardware are contained inside a leak-proof case. Dielectric fluid absorbs heat far more efficiently than air, and as heated water turns to vapor, it condenses and falls back into the fluid to aid in cooling.

Direct-to-chip cooling uses pipes that deliver liquid coolant directly into a cold plate that sits atop a motherboard’s processors to draw off heat. The extracted heat is then fed into a chilled-water loop to be transported back to the facility’s cooling plant and expelled into the outside atmosphere.

Both methods offer far more efficient cooling solutions for power hungry data center deployments.

#### Evaporative cooling :

Evaporative cooling is also known as SWAMP cooling , It comprises of a large fan that draws warm air through water-moistened [pads. As](http://pads.As) the water in the pads evaporate, the air is chilled and let out to the room. The temperature can be controlled by adjusting the airflow of the cooler. Evaporative works best in dry climates.  At lower relative humidity, moisture easily  evaporate from the pads.

Evaporative cooling is relatively new to the data center, but it's been used for years in homes as an environmentally-friendly alternative to traditional air conditioning. Unlike an air conditioner (AC), an evaporative cooler doesn't use refrigerants, which can be hazardous to the environment. Installation costs are significantly lower, electricity usage is significantly lower and the units themselves are simpler to maintain and operate.

#### Free Cooling :

Free cooling technique is benificial for the data center as this technique has high efficiency and low emissions. When the out door temperature is low, the out door air can be drawn inside the data center directly through the ventilation for cooling purpose.

The hurdle in direct free fresh air cooling system,  is  to maintain the indoor air quality requirement due to indoor-outdoor air mixing. To avoid these type of problems data center often install air filters, dehumidification devices, air cleaners etc to reduce moisture,polutants or dusts. Free cooling can offer markable energy cost savings

for data centers. several methods of free cooling options are available and the data center operators can choose the option that best meets their specific requirements.

Precautions :

Many datacenters uses airside economizer systems or free air-side cooling to improve energy efficiency.But when the air from outside enters in to the data center it often carries moisture with it. In side the data center environment if the moisture content in the air increases it leads to condensation which will damage, corrode and eventually lead to equipment failure. On the otherhand if the air is too dry, static electricity can build up, which may cause equipment damage.

High humidity appears to pose a realistic threat to ITE.  The primary threat is something called hygrometric dust particles. Basically, higher humidity can make dust in the air more likely to stick to electrical components in the computer. When dust sticks, it can reduce heat transfer and possibly cause corrosion to those components. The effect of reduced heat transfer is very similar to that caused by high temperatures. There are several threats related to contamination. Dust can coat electronic components, reducing heat transfer. Certain types of dust, called zinc whiskers, are conductive. Zinc whiskers have been most commonly found in electroplated raised floor tiles. The zinc whiskers can become airborne and land inside a computer. Since they are conductive, they can actually cause damaging shorts in tiny internal components.

#### Trigeneration system :

Tri-generation concepts can be used in the data centers as these generation systems are cost effective and economical as well. It has the capacity of producing electricity, heating and cooling simultaneously. It increases fuel efficiency while reducing energy costs and also reduces greenhouse gas emissions (up to 2/3) As it uses natural gas to produce electricity on site, there will be no charge for electrical network consumption(more the distance between DC and generating station more will be the loss of energy and cost as well). it reduces site co2 emissions, provides energy efficient cooling using waste heat and also Achieves thermal efficiency up to 85% of the system.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1717701426180/b0ff3f8f-3577-4cf7-8743-08ed6e2839e6.png align="center")

  

#### Microsoft Capsule Data Center :

Project Natick lead by Ben Cutler(Microsoft's ) 40-foot long Northern Isles datacenter is loaded with 12 racks containing a total of 864 servers and associated cooling system infrastructure. The datacenter was assembled and tested in France and shipped on a flatbed truck to Scotland where it was attached to a ballast-filled triangular base for deployment on the seabed. The data center looks like a cylindrical capsule and made by an ocean engineering company named Naval Group.

After deploying the datacenter on the seabed, parameters like : temperature, humidity, noise creation, power consumption are under observation. Once it is feasible Microsoft allow it's customer to use it. To shrink the datacenter in water has it's own advantages, As more than half of the population of the world live within 120 mile of the costal areas, So the distance to travel the data would reduce which results fastest and smooth connection as well as video streaming and web browsing.

#### Virtualization :

Virtualization became the key concept of datacenters. In computing we can refer virtualization as to create virtual version of hardware resources so that, we can minimize the number of hardware equipment’s in a significant way. Virtual machine refers to virtualized environment with predefined resources such as CPU, Memory storage and Bandwidth to support application performance. It exhibits the behavior of a separate computer and multiple VMs can run in one single physical machine referred as 'Host'. Virtualization lets a single computer do handle the task of multiple computers by distributing the resources of a single computer across multiple settings.

As data center power consumption has a huge expenditure, virtualization can reduce the the number of physical resources used in the data center as a result it gives a way to consume less energy. Virtualization not only allows the providers to serve the clients on pay-as-you-go basis but also helps in scal-up and scale down of resource utilization as per the customer requirements.

Virtualization results more efficient use of resources including energy. Installing virtual infrastructure permits several operating systems and applications to run on a lesser number of servers which helps to reduce overall energy used for the data center and for it's cooling process. virtualization was not restricted to the servers, it could also be implemented at the network layer. Network virtualization help to avoid the traditional method of providing network resources in the hardware. It can provide multiple physical networks in to one virtual network or one physical network to multiple independent virtual network. Data virtualization is a process of accumulating data from different sources and present a logical and virtual view of that data. Data virtualization leads to significant lower cost of infrastructure. Storage virtualization is to keep multiple copy of a physical storage device and each of them behaves as a separate storage device. It provides a better storage utilization also it helps in disaster recovery, storage tiering.

VM Migration :

VM migration can be defined as to migrate a VM from one physical machine to another. It is a resource-intensive task as it continuously requires adequate CPU cycle, cache memory, communication bandwidth, memory capacity etc.

Live Migration :

In live migration, VM can be transferred form source server to target server without disrupting the [service.it](http://service.it) can be accomplished by following two approaches

Pre copy :

Pre copy approach starts by transferring the memory states of the VM to the target machine first, While the VM is still running in the source machine. Then the other states like processor states are getting transfered to the destination machine.

it can be described in a better way as below :-

\=&gt; Initiation of migration by selecting the target VM.

\=&gt; Pre-copying the memory state of the VM to the Destination while VM is still in running state at the source.

\=&gt; Quiescing the VM and sending non-memory state.

\=&gt; Transferring control of VM to the destination and resuming the VM in the destination.("down time range in milliseconds to some seconds")

\=&gt; Removing the dependency of the source machine.

Post copy :

Post copy approach can be explained as the opposite process of pre-copy approach. Here the CPU state transfers first and then memory state transfers to the destination.

Non-Live  or Cold Migration :

Non-live migration process pause the VM and won't allow the VM to be resumed until all the states of the VM must transferred to the target server. Once transfer done it will resume the VM in the new host. The only advantage of this process is it is simple one but the disadvantage is the downtime is more.