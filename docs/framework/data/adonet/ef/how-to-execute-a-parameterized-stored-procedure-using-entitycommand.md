---
title: "Proc&#233;dure&#160;: ex&#233;cuter une proc&#233;dure stock&#233;e param&#233;trable &#224; l&#39;aide d&#39;EntityCommand | Microsoft Docs"
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
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: ex&#233;cuter une proc&#233;dure stock&#233;e param&#233;trable &#224; l&#39;aide d&#39;EntityCommand
Cette rubrique indique comment exécuter une procédure stockée paramétrable à l'aide de la classe <xref:System.Data.EntityClient.EntityCommand>.  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [School Model](http://msdn.microsoft.com/fr-fr/859a9587-81ea-4a45-9bc0-f8d330e1adac) à votre projet et configurez votre projet pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Importez la procédure stockée `GetStudentGrades` et spécifiez des entités `CourseGrade` comme type de retour.  Pour plus d'informations sur la manière d'importer une procédure stockée, consultez [How to: Import a Stored Procedure](http://msdn.microsoft.com/fr-fr/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).  
  
## Exemple  
 Le code suivant exécute la procédure stockée `GetStudentGrades` dans laquelle `StudentId` est un paramètre requis.  Les résultats sont alors lus par un <xref:System.Data.EntityClient.EntityDataReader>.  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## Voir aussi  
 [Fournisseur EntityClient pour Entity Framework](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)