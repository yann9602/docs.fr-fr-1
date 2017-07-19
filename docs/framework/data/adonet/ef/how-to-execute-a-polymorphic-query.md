---
title: "Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te polymorphe | Microsoft Docs"
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
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te polymorphe
Cette rubrique montre comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] polymorphe à l'aide de l'opérateur [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md).  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [School Model](http://msdn.microsoft.com/fr-fr/859a9587-81ea-4a45-9bc0-f8d330e1adac) à votre projet et configurez votre projet de façon à utiliser Entity Framework.  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Modifiez le modèle conceptuel pour avoir un héritage TPH \(table par hiérarchie\) en suivant la procédure décrite dans [Walkthrough: Mapping Inheritance \- Table\-per\-Hierarchy](http://msdn.microsoft.com/fr-fr/49b685cf-9db8-4d6d-b885-8837ed238f55).  
  
## Exemple  
 L'exemple ci\-dessous utilise un opérateur OFTYPE pour obtenir et afficher une collection d'`OnsiteCourses` uniquement, à partir d'une collection de `Courses`.  
  
 [!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
 [!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]  
  
## Voir aussi  
 [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)   
 [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)