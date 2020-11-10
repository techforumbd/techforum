---
layout: post
title: Best Practices for Database Design-Development-Deployment
date: 2014-08-19 12:56
author: techforumugm
comments: true
categories: [MS SQLServer]
---
<div class="MsoListParagraphCxSpFirst" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><div class="separator" style="clear:both;text-align:center;"><a href="https://techforumugm.files.wordpress.com/2014/08/18b53-best2bpratice.jpg" style="margin-left:1em;margin-right:1em;"><img border="0" src="https://techforumugm.files.wordpress.com/2014/08/18b53-best2bpratice.jpg" /></a></div><span lang="EN"><br /><br /><span><span style="font-family:Calibri;"></span><br /><span>           <span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpFirst" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.1</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Database Tables should be normalized. But you have to be remember that over-normalization will cause excessive joins across too many tables.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.2</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Tables name should be consistent and expressive.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.3</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Columns data type should be properly define. It is not better to store image files in tables. Instead of that keep paths or URLs. Also you don’t want to keep blob data types in select list.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.4</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Whenever you want to keep boolean value in table use bit data type.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.5</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Better to use integer data type or less character length as for keys and make index using integer data type. Use constraints (foreign key, check, not null ...) for data integrity.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.6</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Keep the tables in different file group based on its behavior (transactional table, master data keeping tables ).</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.7</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Plan for table partition where large volume of transactional data will be stored.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.8</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Always try to specific number of columns rather than all column selection.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.9</span><span>            </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Use join rather than sub queries. It increase performance .Use ’LIKE’ whenever required.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.10</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Documentation is very much important , it should be include ER diagram ,performance guide line, database convention. <span> </span></span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.11</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Authentication is an important part use role based authentication to all users.Security and resource availability database server and the web server must be placed in different machines. By that security and performance will be improved .</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.12</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Keep passwords as encrypted for security. Decrypt them in application when required.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.13</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Keep your stored procedure encrypted at the time of deployment.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpMiddle" style="margin:0 0 0 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.14</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Use disaster recovery and security services like failover clustering, auto backups, replication etc.</span></span></span></div><span style="font-size:small;"> </span><br /><div class="MsoListParagraphCxSpLast" style="margin:0 0 8pt 31.5pt;text-indent:-31.5pt;"><!--[if !supportLists]--><span lang="EN"><span><span style="font-family:Calibri;font-size:small;">1.15</span><span>         </span></span></span><!--[endif]--><span lang="EN"><span style="font-family:Calibri;"><span style="font-size:small;">Database source should be keep under source controls. Also make backup plan for deployment. </span></span></span></div></span> </span> </span> </div>