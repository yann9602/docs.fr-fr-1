---
title: "Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te qui retourne des r&#233;sultats StructuralType | Microsoft Docs"
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
ms.assetid: 2314f2a2-b1c3-40c4-95bb-cdf9b21a7b53
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te qui retourne des r&#233;sultats StructuralType
Cette rubrique montre comment exécuter une commande par rapport à un modèle conceptuel en utilisant un objet <xref:System.Data.EntityClient.EntityCommand> et comment récupérer les résultats de <xref:System.Data.Metadata.Edm.StructuralType> en utilisant un objet <xref:System.Data.EntityClient.EntityDataReader>.  Les classes <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.RowType> et <xref:System.Data.Metadata.Edm.ComplexType> sont dérivées de la classe <xref:System.Data.Metadata.Edm.StructuralType>.  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurez votre projet pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## Exemple  
 Cet exemple exécute une requête qui retourne des résultats <xref:System.Data.Metadata.Edm.EntityType>.  Si vous transmettez la requête suivante en tant qu'argument à la fonction `ExecuteStructuralTypeQuery`, celle\-ci affiche des détails sur l'objet `Products` :  
  
 [!code-csharp[DP EntityServices Concepts#SelectProduct](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#selectproduct)]
 [!code-sql[DP EntityServices Concepts#SelectProduct](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#selectproduct)]  
  
 Si vous transmettez une requête paramétrable, telle que la suivante, ajoutez les objets <xref:System.Data.EntityClient.EntityParameter> à la propriété <xref:System.Data.EntityClient.EntityCommand.Parameters%2A> sur l'objet <xref:System.Data.EntityClient.EntityCommand>.  
  
 [!code-csharp[DP EntityServices Concepts#GREATER_OR_EQUALS](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#greater_or_equals)]
 [!code-sql[DP EntityServices Concepts#GREATER_OR_EQUALS](../../../../../samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#greater_or_equals)]  
  
 [!code-csharp[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#esqlstructuraltypes)]
 [!code-vb[DP EntityServices Concepts#eSQLStructuralTypes](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#esqlstructuraltypes)]  
  
## Voir aussi  
 [Référence Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)   
 [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)