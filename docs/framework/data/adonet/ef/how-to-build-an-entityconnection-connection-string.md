---
title: "Proc&#233;dure&#160;: g&#233;n&#233;rer une cha&#238;ne de connexion pour EntityConnection | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: 5bd1a748-3df7-4d0a-a607-14f25e3175e9
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: g&#233;n&#233;rer une cha&#238;ne de connexion pour EntityConnection
Cette rubrique fournit un exemple de génération d'un objet <xref:System.Data.EntityClient.EntityConnection>.  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurez votre projet pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## Exemple  
 L'exemple ci\-dessous initialise l'objet <xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=fullName> pour le fournisseur sous\-jacent, puis initialise l'objet <xref:System.Data.EntityClient.EntityConnectionStringBuilder?displayProperty=fullName> avant de le passer au constructeur de l'objet <xref:System.Data.EntityClient.EntityConnection>.  
  
 [!code-csharp[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#buildingconnectionstringwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#BuildingConnectionStringWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#buildingconnectionstringwithentitycommand)]  
  
## Voir aussi  
 [How to: Use EntityConnection with an Object Context](http://msdn.microsoft.com/fr-fr/2140fe7b-b88b-47c8-a749-d7f142eb1080)   
 [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)