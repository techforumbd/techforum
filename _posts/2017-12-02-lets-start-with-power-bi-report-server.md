---
layout: post
title: Let’s Start with Power BI Report Server
date: 2017-12-02 03:07
author: techforumugm
comments: true
categories: [Business Intelligence, Power BI]
---
<h2><em>At a Glance </em></h2>
<h5><em>Introduction </em></h5>
<h5><em>What Why How…</em></h5>
<h5><em>Installation </em></h5>
<h5><em>Configuration </em></h5>
<h3></h3>
<h3>Introduction</h3>
The Power BI Report Server is a new, standalone product that allows organizations to host Power BI Reports on an on-premises report server. Additionally, the Power BI Report Server is built upon the same architecture as SQL Server Reporting Services, allowing you to also use the server to host paginated reports, mobile reports, and key performance indicators (KPIs), thus creating a “one-stop shop” for all your reporting assets.

What

<em>Power BI Desktop</em> as a powerful tool for self-service BI and creating interactive reports. It offers data warehouse capabilities, including data preparation, data discovery and interactive dashboards.

Self-service BI using Power BI provides the tools you need to find data, shape and filter it how you want, model it, and visualize. Data visualization is a quick and easy way to convey concepts or information in a universal manner. Data visualization can help to:
<ul>
	<li>Analysis capabilities of business processes or activities</li>
	<li>Get factors that give better insights.</li>
	<li>Drive better decision making</li>
	<li>Make proper predictions.</li>
	<li>Providing an integrated view</li>
</ul>
Why

Power BI gives cloud-based BI services, known as “<em>Power BI Services</em>”, along with a desktop based interface, called “Power BI Desktop”. Sharing reports with business users the on-premises solution requirement arrived. On-premises solution to host Power BI Reports are required due to several reasons:
<ul>
	<li>Complement the Power BI Service</li>
	<li>Highly Regulated Customers</li>
	<li>Integrate into existing investment in Reporting Services</li>
</ul>
Power BI reports in SQL Server Reporting Services combination of Power BI Desktop’s interactive report capability with SQL Server Reporting Services’ on-premises server platform.SQL Server 2017 will continue to include Reporting Services for on-premises enterprise reporting.Comparison view :

<img class="alignnone size-full wp-image-822" src="https://techforumugm.files.wordpress.com/2017/12/comparision.png" alt="comparision" width="617" height="308" />

Source: <a href="https://blogs.msdn.microsoft.com/sqlrsteamblog/2017/05/17/a-closer-look-at-power-bi-report-server/">SQL Server Reporting Services Team Blog</a>

With Power BI Desktop and Power BI Report Server, you can
<ol>
	<li>Create beautiful, interactive reports using Power BI Desktop</li>
	<li>Publish reports to Power BI Report Server</li>
	<li>View and interact with reports in your web browser or in Power BI Mobile on your phone or tablet</li>
</ol>
How :

Power BI Report Server. With its small file size and simplified wizard, you can download and install Power BI Report Server in minutes. because it’s separate from SQL Server setup, you can install Power BI Report Server updates knowing they’ll have zero impact on your SQL Server deployments and databases.

The same Power BI reports you create for Power BI Report Server can work in the Power BI service and even continue to query your on-premises data via the On-premises Data Gateway.

<img class="alignnone size-full wp-image-826" src="https://techforumugm.files.wordpress.com/2017/12/publish.png" alt="Publish" width="1366" height="768" />
<h3>Install Power BI Report Server</h3>
<a href="https://docs.microsoft.com/en-us/power-bi/report-server/release-notes">Power BI Report Server release notes</a> : It's better to take a look on release notes to

<a href="https://docs.microsoft.com/en-us/power-bi/report-server/system-requirements">Hardware and software requirements:</a> It’s an important to know &amp; check the installation requirement from Microsoft site.

Download Free trial form Power BI site:

1. <a href="https://powerbi.microsoft.com/report-server/">On-premises reporting with Power BI Report Server</a> October 2017

2. <a href="https://www.microsoft.com/en-us/download/details.aspx?id=56136">Power BI Desktop (October 2017)</a>

3. For Sample Data (if required to explore) you can download Dataware House WideWorldImporters database backup .

<img class="alignnone size-full wp-image-831" src="https://techforumugm.files.wordpress.com/2017/12/download-file.png" alt="download file" width="597" height="93" />

Step 1 :Run the PowerBIReportServer file that you downloaded .Now you have to select the edition from the drop down.

<img class="alignnone size-full wp-image-832" src="https://techforumugm.files.wordpress.com/2017/12/p1.png" alt="p1" width="1249" height="590" />

Step 2 :It's simple installation steps within that step you have to agree Licencing teems , assign Installation path .

[gallery ids="834,835,836,837" type="rectangular" link="file"]

Step 3 :After installation completion ,run the <em>Report Server configuration manager</em> to setting up ReportServer catalog database as well as confirm the web portal and web service URLs.

[gallery ids="839,838,840" type="rectangular" link="file"]

Step 4: To get the Power BI Web portal Go to Browser &gt; Write &gt; http://localhost/reports

<img class="alignnone size-full wp-image-843" src="https://techforumugm.files.wordpress.com/2017/12/browse-pbi_rs.png" alt="browse PBI_RS" width="1362" height="227" />

Power BI reports on premises can store in Power BI reports Server or Power BI service (<a href="https://powerbi.com/">https://powerbi.com</a>). You create and edit reports in Power BI Desktop, and publish them to the web portal. It can view able from browser or in a Power BI mobile app on a mobile device.
<h4>Power BI reports for Power BI Report Server:</h4>
Power BI Desktop optimized is required for Power BI Report Server. It's important to remember that this one release is different from the Power BI Desktop used with the Power BI service.

Step 1: There is download link is in the Web portal.

<img class="alignnone size-full wp-image-847" src="https://techforumugm.files.wordpress.com/2017/12/pd1.png" alt="PD1" width="1358" height="334" />

Step 2: Now you have select the required installer .Installation steps are very easy.Main problem is that you have to careful on the version it should be October 2017.First time I've installed wrong version :( but Right one is "Optimized for Power BI Report Server - October 2017".Download link has give on download section of above of  present article.

[gallery ids="852,853,854,855,856,857,858,859" type="rectangular" link="file"]

It's will better for new one to go through the article :

"<a href="https://docs.microsoft.com/en-us/power-bi/report-server/user-handbook-overview">User handbook overview for Power BI Report Server</a>"

Hopefully this article objective is to help professionals. Have a nice day !

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;

&nbsp;
