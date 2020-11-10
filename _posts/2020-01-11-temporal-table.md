---
layout: post
title: Temporal Table
date: 2020-01-11 00:26
author: techforumugm
comments: true
categories: [MS SQLServer]
---
<h2>What is Temporal Table ?</h2>
In a traditional table we can keep data along with CRUD operation but can't view the history of data contained in tables.On the other site, temporal tables allow to automatically keep history of the data in the <b>table</b> A system-versioned table allows you to query updated and deleted data, while a normal table can only return the current data.

Temporal tables are not replace the <em>change data capture (CDC)</em> feature. CDC uses the transaction log to find the changes and typically those changes are kept for a short period of time (depending on your ETL timeframe). Temporal tables store the actual changes in the history table and they are intended to stay there for a much longer time.
<h2>Why to use ?</h2>
<ol>
	<li>Temporal tables captures the lifetime of a record based on the physical dates the record was removed or updated.</li>
	<li>Temporal tables add data auditing features to existing applications or solutions when you need it.</li>
	<li>System-versioned temporal tables store values for period columns in UTC time zone, while it is always more convenient to work with local time zone both for filtering data and displaying results.</li>
	<li>By that user can view how entire data sets changed over time.</li>
	<li>Allow users to transparently keep the full history of changes for later analysis, separately from the current data, with the minimal impact on the main OLTP workload.</li>
</ol>
<img class="alignnone size-full wp-image-969" src="https://techforumugm.files.wordpress.com/2020/03/tt01.png" alt="TT01" width="746" height="290" />
<h2>Why it required ?</h2>
<ul>
	<li><i>Audit</i>. With temporal tables you can find out what values a specific entity has had over its entire lifetime.</li>
	<li><i>Slowly changing dimensions</i>. A system-versioned table exactly behaves like a dimension with type 2 changing behavior for all of its columns.</li>
	<li><i>Repair record-level corruptions</i>. Think of it as a sort of back-up mechanism on a single table. Accidentally deleted a record? Retrieve it from the history table and insert it back into the main table.</li>
</ul>
<h2>How it works ?</h2>
System-versioning for a table is implemented as a pair of tables, a current table and a history table. Within each of these tables, the following two additional datetime2 columns are used to define the period of validity for each row:
<ul>
	<li><u>Period start column</u>: The system records the start time for the row in this column, typically denoted as the <b>SysStartTime</b> column.</li>
	<li><u>Period end column</u>: The system records the end time for the row in this column, typically denoted as the <b>SysEndTime</b> column.</li>
</ul>
The current table contains the current value for each row. The history table contains each previous value for each row, if any, and the start time and end time for the period for which it was valid.

<img class="alignnone size-full wp-image-974" src="https://techforumugm.files.wordpress.com/2020/02/tt02.png" alt="TT02" width="669" height="359" />
<h2><b>How do I query temporal data?</b></h2>
The SELECT statement FROM&lt;table&gt; clause has a new clause FOR SYSTEM_TIME with five temporal-specific sub-clauses to query data across the current and history tables. This new SELECT statement syntax is supported directly on a single table, propagated through multiple joins, and through views on top of multiple temporal tables.

The following query searches for row versions for Employee row with EmployeeID = 1000 that were active at least for a portion of period between 1st January of 2014 and 1st January 2015 (including the upper boundary):
<blockquote>
<p style="padding-left:40px;"><em><span style="color:#333399;">SELECT * FROM Employee FOR SYSTEM_TIME BETWEEN '2014-01-01 00:00:00.0000000' AND '2015-01-01 00:00:00.0000000'                                            </span><span style="color:#333399;">WHERE EmployeeID = 1000 ORDER BY ValidFrom;</span></em></p>
</blockquote>
&nbsp;

<img class="alignnone size-full wp-image-976" src="https://techforumugm.files.wordpress.com/2020/02/tt03.png" alt="TT03" width="609" height="278" />
<h2><b>Prerequisite for creating temporal Table  </b><b>  </b></h2>
<ul>
	<li>A primary key must be defined</li>
	<li>Two columns must be defined to record the start and end date with a data type of datetime2. If needed, these columns can be hidden using the HIDDEN flag. These columns are called the SYSTEM_TIME period columns.</li>
	<li>INSTEAD OF triggers are not allowed. AFTER triggers are only allowed on the current table.</li>
	<li>In-memory OLTP cannot be used in SQL Server 2016. Later on, this limitation has been lifted. Check out the documentation for more information.</li>
	<li>By default, the history table is page compressed.</li>
	<li>ON DELETE/UPDATE CASCADE is not permitted on the current table. This limitation has also been lifted in SQL Server 2017.</li>
</ul>
<h2><b>Limitations Of temporal Table  </b><b> </b></h2>
<ul>
	<li>Temporal and history table cannot be FILETABLE</li>
	<li>The history table cannot have any constraints</li>
	<li>INSERT and UPDATE statements cannot reference the SYSTEM_TIME period columns</li>
	<li>Data in the history table cannot be modified</li>
</ul>
<h2><b> </b></h2>
