---
title: "Transactions distribu&#233;es Oracle | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Transactions distribu&#233;es Oracle
L'objet <xref:System.Data.OracleClient.OracleConnection> s'inscrit automatiquement dans une transaction distribuée existante s'il détermine qu'une transaction est active.  L'inscription automatique dans une transaction se produit lorsque la connexion est ouverte et extraite du pool de connexions.  Vous pouvez désactiver l'inscription automatique dans des transactions existantes en spécifiant  
  
```  
Enlist=false  
```  
  
 comme paramètre de chaîne de connexion pour un <xref:System.Data.OracleClient.OracleConnection>.  
  
## Voir aussi  
 [Oracle et ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)