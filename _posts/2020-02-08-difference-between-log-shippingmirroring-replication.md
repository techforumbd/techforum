---
layout: post
title: Difference between Log Shipping,Mirroring & Replication
date: 2020-02-08 12:28
author: techforumugm
comments: true
categories: [MS SQLServer]
---
In this article,we're going to explored what why when to use of Log Shipping,Mirroring &amp; Replication.

<span style="color:var(--color-text);">Architecture of Log Shipping and Mirroring :</span>

<img class="alignnone size-full wp-image-1048" src="https://techforumugm.files.wordpress.com/2020/02/lmr01.png" alt="LMR01" width="1004" height="294" />

<span style="color:var(--color-text);">Architecture of Replication :</span>

<img class="alignnone size-full wp-image-1050" src="https://techforumugm.files.wordpress.com/2020/02/lmr02.png" alt="LMR02" width="1004" height="584" />

&nbsp;
<table style="height:5075px;" width="744">
<tbody>
<tr>
<td width="135">Explanation Point</td>
<td width="166">Log Shipping</td>
<td width="167">Mirroring</td>
<td width="156">Replication</td>
</tr>
<tr>
<td width="135">What</td>
<td width="166">In Log shipping mechanism, periodically take log backups of the primary database, copy the backup files to one or more secondary server instances, and restore the backups into the secondary database(s) which is based on SQL Server Agent jobs. Log shipping supports an unlimited number of secondaries for each primary database</td>
<td width="167">Database mirroring is SQL Server engine reads from the transaction log and copies transactions from the production server instance to the mirror server instance.</td>
<td width="156">It is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency. Using replication, you can distribute data to different locations and to remote or mobile users over local and wide area networks, dial-up connections, wireless connections, and the Internet.</td>
</tr>
<tr>
<td width="135">Data synchronization</td>
<td width="166">Log shipping is always asynchrony. Log shipping totally depends on the log backup and restore schedule

T-Logs are backed up and transferred to secondary server</td>
<td width="167">Database mirroring can operate synchronously or asynchronously. The transaction on the production database will not be committed until it is hardened to disk on the mirror.</td>
<td width="156">It can be transactional, snapshot or Merge which is defined by requirements &amp; DBA.</td>
</tr>
<tr>
<td width="135">Data Transfer

&nbsp;</td>
<td width="166">Logs are backed up and transferred to secondary server

&nbsp;

&nbsp;</td>
<td width="167">Individual Transaction Log records are transferred from production Database to mirrored instance using TCP endpoints

&nbsp;</td>
<td width="156">In this mechanism, system are tracking/detecting changes (either by triggers or by scanning the log) and shipping the changes.</td>
</tr>
<tr>
<td width="135">Requirements</td>
<td width="166">In log shipping, production database, secondary server and monitor server (Optional) required</td>
<td width="167">Production Database, mirror server, and witness server (Optional) are needed to setup.</td>
<td width="156">Production database is Publisher, Subscribers, Distributor (Optional).</td>
</tr>
<tr>
<td width="135">Transactional Consistency</td>
<td width="166">All committed and un-committed transaction are transferred</td>
<td width="167">Transfer only committed Transactions no uncommitted transaction are allowed transferred. No uncommitted transaction are allowed</td>
<td width="156">Committed transactions are transferred to the subscriber database.</td>
</tr>
<tr>
<td width="135">Reporting Server</td>
<td width="166">In log shipping the secondary database will be in Read-only mode so that it can be used for reporting purposes.</td>
<td width="167">In database mirroring the mirror database will be in Restoring state and hence cannot be used for accessing.

If you want it for reporting purposes then make use of database snapshot.</td>
<td width="156">The Subscriber Database is open to reads and writes.</td>
</tr>
<tr>
<td width="135">Server Limitation</td>
<td width="166">Log shipping can be applied to multiple stand-by servers</td>
<td width="167">Mirrored server only one.</td>
<td width="156">Central publisher/distributor, multiple subscribers.

Central Distributor, multiple publishers, multiple subscribers.

Central Distributer, multiple publishers, single subscriber.

Mixed Topology.</td>
</tr>
<tr>
<td width="135">Failover</td>
<td width="166">Log Shipping supports only manual failover</td>
<td width="167">Both automatic and manual failover supports.</td>
<td width="156">Manual failover</td>
</tr>
<tr>
<td width="135">Failover Duration</td>
<td width="166">it takes more than 30 mins</td>
<td width="167">Failover is fast within 3 to 10 seconds but it depends on current situation.

&nbsp;</td>
<td width="156">Failover concept is not available.</td>
</tr>
<tr>
<td width="135">Client Re-direction</td>
<td width="166">Client Re-direction:  Manual changes required</td>
<td width="167">Client Re-direction:  Fully automatic as it uses .NET 2.0</td>
<td width="156">&nbsp;</td>
</tr>
<tr>
<td width="135">Recovery model.</td>
<td width="166">Log shipping supports both Bulk Logged Recovery Model and Full Recovery Model</td>
<td width="167">Mirroring supports only Full Recovery model</td>
<td width="156">It supports Full Recovery model.</td>
</tr>
<tr>
<td width="135">Restoring State</td>
<td width="166">The restore can be completed using either the NORECOVERY or STANDBY option.</td>
<td width="167">The restore can be completed using with NORECOVERY</td>
<td width="156">The restore can be completed using With RECOVERY.</td>
</tr>
<tr>
<td width="135">Backup/Restore</td>
<td width="166">This can be done manually or

through Log Shipping options.</td>
<td width="167">User make backup &amp; Restore manually</td>
<td width="156">User create an empty database with the same name</td>
</tr>
<tr>
<td width="135">&nbsp;</td>
<td width="166">In case of standby mode: read only database.

In case of restoring with no recovery: Restoring state.</td>
<td width="167">In Recovery state, no user can make any operation.
You can take snapshot.</td>
<td width="156">Snapshot (read-only).

Other types (Database are available)</td>
</tr>
<tr>
<td width="135">Primary key</td>
<td width="166">No need</td>
<td width="167">No Need</td>
<td width="156">All replicated table should have Primary Key</td>
</tr>
<tr>
<td width="135">latency</td>
<td width="166">There will be data transfer latency. &gt;1min.</td>
<td width="167">There will not be data transfer latency.</td>
<td width="156">Potentially as low as a few seconds.</td>
</tr>
<tr>
<td width="135">DDL Operations</td>
<td width="166">DDL changes are applied automatically.</td>
<td width="167">DDL changes are applied automatically.</td>
<td width="156">only DML changes to the tables you have published will be replicated.</td>
</tr>
<tr>
<td width="135">Requirement</td>
<td width="166">§  The servers involved in log shipping should have the same logical design and collation setting.

§  The databases in a log shipping configuration must use the full recovery model or bulk-logged recovery model.

§  The SQL server agent should be configured to start up automatically.

§  You must have sysadmin privileges on each computer running SQL server to configure log shipping.

&nbsp;</td>
<td width="167">§  Verify that there are no differences in system collation settings between the principal and mirror servers.

§  Verify that the local windows groups and SQL Server logins definitions are the same on both servers.

§  Verify that external software components are installed on both the principal and the mirror servers.

§  Verify that the SQL Server software version is the same on both servers.

§  Verify that global assemblies are deployed on both the principal and mirror server.

§  Verify that for the certificates and keys used to access external resources, authentication and encryption match on the principal and mirror server.

&nbsp;</td>
<td width="156">§  Verify that there are no differences in system collation settings between the servers.

§  Verify that the local windows groups and SQL Server Login definitions are the same on both servers.

§  Verify that external software components are installed on both servers.

§  Verify that CLR assemblies deployed on the publisher are also deployed on the subscriber.

§  Verify that SQL agent jobs and alerts are present on the subscriber server, if these are required.

§  Verify that for the certificates and keys used to access external resources, authentication and encryption match on the publisher and subscriber server.

&nbsp;</td>
</tr>
<tr>
<td width="135">Components</td>
<td width="166">§  Primary server, secondary server and monitor server (Optional)</td>
<td width="167">§  Principal server, mirror server, and witness server (Optional).</td>
<td width="156">§  Publisher, Subscribers, Distributor (Optional).</td>
</tr>
</tbody>
</table>
