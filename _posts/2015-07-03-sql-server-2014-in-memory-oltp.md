---
layout: post
title: SQL Server 2014 In-Memory OLTP
date: 2015-07-03 17:52
author: techforumugm
comments: true
categories: [MS SQLServer, Performance Tuning]
---
<h2 class="projectSummary" style="background-color:white;border:0;clear:both;color:#2a2a2a;font-family:'Segoe UI', 'Lucida Grande', Verdana, Arial, Helvetica, sans-serif;font-size:1.1em;font-weight:normal;line-height:1.4;margin:4px 0 11px;outline:0;padding:0;word-wrap:break-word;"><img class="alignnone size-full wp-image-367" src="https://techforumugm.files.wordpress.com/2015/07/microsoft-sql-server-2016-in-memory-oltp.jpg" alt="microsoft-sql-server-2016-in-memory-oltp" width="716" height="493" />In-memory OLTP is a memory-optimized database engine integrated with SQL Server engine. It optimized OLTP operations. It massively improve performance and scalability of databases and by that applications will be speed up.</h2>
Its main mechanism is that it allows you to declare a table to be stored in main memory which is called memory optimized table. That reduce OLTP workload and provide faster accessibility. Different data and index structure are introduced in memory optimized tables and no data pages, no locking or latching, index pages or buffer pool are used. SQL Server was designed to store data in the disk based tables for persistence and bring data in memory when needed for serving query requests. In memory optimized tables data are already stored in the memory.
<div><a href="https://gallery.technet.microsoft.com/SQL-Server-2014In-Memory-ea7c6e6e">Details on </a></div>
