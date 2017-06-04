---
title: "Donn&#233;es binaires et de valeur &#233;lev&#233;e SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# Donn&#233;es binaires et de valeur &#233;lev&#233;e SQL&#160;Server
SQL Server fournit le spécificateur `max`, qui étend la capacité de stockage des types de données `varchar`, `nvarchar` et `varbinary`.  `varchar(max)`, `nvarchar(max)` et `varbinary(max)` sont désignés par le terme générique de *types de données de valeur élevée*.  Les types de données de valeur élevée permettent de stocker jusqu'à 2^31\-1 octets de données.  
  
 SQL Server 2008 introduit l'attribut FILESTREAM, qui n'est pas un type de données, mais plutôt un attribut pouvant être défini sur une colonne et permettant alors de stocker des données de valeur élevée dans le système de fichiers et non dans la base de données.  
  
## Dans cette section  
 [Modification des données de valeur élevée \(max\) dans ADO.NET](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 Décrit comment utiliser les types de données de valeur volumineux.  
  
 [Données FILESTREAM](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 Décrit comment utiliser les données de valeur élevée stockées dans SQL Server 2008 avec l'attribut FILESTREAM.  
  
## Voir aussi  
 [Types de données SQL Server et ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)   
 [Opérations de données SQL Server dans ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)   
 [Extraction et modification de données dans ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)