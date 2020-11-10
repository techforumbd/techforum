---
layout: post
title: Resource Governor
date: 2020-02-22 00:21
author: techforumugm
comments: true
categories: [MS SQLServer]
---
<h2>What is RG ?</h2>
Resource Governor (RG) is a mechanism by that specific resources are allocated to resource groups, where we can define groups based on applications or users and therefore limit how much resources are used.

Think a situation, where application and reporting use same database server.Request are coming from application and report end.For executing analytical reports (high concurrent users presence ) then significant amount of resource can be consumed by report processing .Application users feels transaction execution slowness.

Another situation, multiple application usages same database server then using RG you govern on the physical resources. Assign specify resources(Memory,CPU,IO) for individual application.

<img class="alignnone size-full wp-image-1062" src="https://techforumugm.files.wordpress.com/2020/02/rg03.png" alt="RG03" width="593" height="294" />
<h2>How it works ?</h2>
RG in SQL Server which enable us to control physical Resources means CPU , memory and IO usage.We can classify request , session coming from application A to a group Workload group A.Next step we'll configure resource pool A and it run the workload A defined earlier.After that resource can be assigned to the resource pool say memory 30% and CPU 50%. Steps are as below :
<ol>
	<li>Enable SQL Server Resource Governor</li>
	<li>Create Resource Governor Workload Group</li>
	<li>Create Resource Governor Classifier Function</li>
	<li>Assign Resource Governor Classifier Function to Use</li>
	<li>Define Resource Governor Pool Settings</li>
	<li>Testing SQL Server Resource Governor Settings</li>
</ol>
<h3><b>Configuring Resource Governor:</b></h3>
SSMS, go to Management &gt; Resource Governor, right click and select <b>New Resource Pool</b>.Manage Resource Governor settings by right clicking on <b>Resource Governor</b> and selecting <b>Properties </b>and you will get a screen like below where you can set the values:

<img class="alignnone size-full wp-image-964" src="https://techforumugm.files.wordpress.com/2020/03/rg01.png" alt="RG01" width="964" height="444" />
<h2>Limitation :</h2>
<ol>
	<li>It work on user sessions only not the system sessions.</li>
	<li>It will works data read operation from data files in a OLTP system but not writing data to log files.</li>
	<li>Resource Governor can only be applied to SQL Server database engine services. You cannot enable Resource Governor for SQL Server Analysis Services (SSAS), SQL Server Integration Service (SSIS) or SQL Server Reporting Services (SSRS).</li>
	<li>Resource Governor is available only with Enterprise Edition and Developer Edition. Since Enterprise Edition is costly, unfortunately, you need to pay more money to use this feature</li>
</ol>
<h2>Where is it implementable :</h2>
<ol>
	<li>Not all resources can be governed by the Resource Governor. IO, CPU, Memory, Degree of Parallelism are the resources you can control from Resource Governor.</li>
	<li>Resource Governor (RG) supports SQL Server and Azure SQL Database (Managed Instance). It does not support Azure SQL Data Warehouse and Parallel Data Warehouse.</li>
	<li>RG may create balanced situation (of resources )where multiple application usage same database.</li>
</ol>
&nbsp;

&nbsp;
