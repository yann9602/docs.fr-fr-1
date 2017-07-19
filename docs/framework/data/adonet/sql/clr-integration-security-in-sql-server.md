---
title: "S&#233;curit&#233; d&#39;int&#233;gration du CLR dans SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 489fe096-fd1d-42de-8438-bf7aed46aea2
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# S&#233;curit&#233; d&#39;int&#233;gration du CLR dans SQL Server
Microsoft SQL Server introduit le composant Common Language Runtime \(CLR\) du .NET Framework.  L'intégration du CLR vous permet d'écrire des procédures stockées, des déclencheurs, des types définis par l'utilisateur, des fonctions définies par l'utilisateur, des agrégats définis par l'utilisateur et des fonctions de flux évaluées par une table, en utilisant tout langage .NET Framework, tel que Microsoft Visual Basic .NET ou Microsoft Visual C\#.  
  
 Le CLR prend en charge un modèle de sécurité appelé sécurité d'accès du code \(CAS\) pour le code managé.  Dans ce modèle, les autorisations sont accordées aux assemblys en fonction de la preuve fournie par le code dans les métadonnées.  SQL Server intègre le modèle de sécurité de SQL Server, basé sur l'utilisateur avec le modèle de sécurité du CLR, basé sur l'accès du code.  
  
## Ressources externes  
 Pour plus d'informations sur l'intégration du CLR avec SQL Server, voir les ressources répertoriées ci\-dessous.  
  
|Ressource|Description|  
|---------------|-----------------|  
|[Code Access Security](http://msdn.microsoft.com/fr-fr/23a20143-241d-4fe5-9d9f-3933fd594c03)|Contient des rubriques qui décrivent la sécurité d'accès du code dans le .NET Framework.|  
|[Sécurité de l'intégration du CLR](http://go.microsoft.com/fwlink/?LinkId=59998)|Présente le modèle de sécurité pour le code managé qui s'exécute au sein de SQL Server.|  
  
## Voir aussi  
 [Sécurisation des applications ADO.NET](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [Scénarios de sécurité des applications dans SQL Server](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)   
 [Intégration de Common Language Runtime dans SQL Server](../../../../../docs/framework/data/adonet/sql/sql-server-common-language-runtime-integration.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)