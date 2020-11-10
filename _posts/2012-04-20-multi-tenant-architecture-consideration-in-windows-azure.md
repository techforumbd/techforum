---
layout: post
title: Multi-tenant Architecture Consideration in Windows Azure
date: 2012-04-20 16:27
author: techforumugm
comments: true
categories: [Cloud Computing, Microsoft Azure]
---
<span>In multi-tenant application single instance is used by users of different organization. Failure impacts all users, Windows Azure reduces the risk giving the facility to deploy multiple, and identical copies of your application into multiple Windows Azure role instances.</span><br /><span></span><br /><strong><span>Scalability</span></strong><br /><span>Scalability of web application depends running on Windows Azure mainly depend on ability to deploy multiple instances of your web and worker roles to multiple compute nodes while being able to access the same data from those nodes. Both single-tenant and multi-tenant applications use this feature to scale out when they run on Windows Azure.</span><br /><span></span><br /><strong><span>SLA (Service Level Agreement)</span></strong><br /><span>If SLA with customers differ from each other then all SLA content need to be meat in the instance. As a result all level of customer’s requirement will be cover .Otherwise you need to make same SLA for all clients.</span><br /><span></span><br /><strong><span>Legal and Regulatory Environment</span></strong><br /><span>Whenever SLA differs from customer in the context like customer specific database storage, storage location differs, functionality differs then it should be notify to client.</span><br /><span></span><br /><strong><span>Handling Authentication and Authorization</span></strong><br /><span>Multi-tenant application need to have security option so that client can use application level security with active directory level also.</span>
