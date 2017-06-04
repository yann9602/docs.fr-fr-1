---
title: "Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te Entity&#160;SQL param&#233;trable &#224; l&#39;aide d&#39;EntityCommand | Microsoft Docs"
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
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: ex&#233;cuter une requ&#234;te Entity&#160;SQL param&#233;trable &#224; l&#39;aide d&#39;EntityCommand
Cette rubrique indique comment exécuter une requête [!INCLUDE[esql](../../../../../includes/esql-md.md)] dotée de paramètres en utilisant un objet <xref:System.Data.EntityClient.EntityCommand>.  
  
### Pour exécuter le code de cet exemple  
  
1.  Ajoutez le [AdventureWorks Sales Model](http://msdn.microsoft.com/fr-fr/f16cd988-673f-4376-b034-129ca93c7832) à votre projet et configurez votre projet pour utiliser [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Dans la page de codes de votre application, ajoutez les instructions `using` \(`Imports` en Visual Basic\) suivantes :  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## Exemple  
 L'exemple suivant montre comment construire une chaîne de requête comportant deux paramètres.  Il crée ensuite un objet <xref:System.Data.EntityClient.EntityCommand>, ajoute deux paramètres à la collection <xref:System.Data.EntityClient.EntityParameter> de cet objet <xref:System.Data.EntityClient.EntityCommand>, puis itère au sein de la collection d'éléments `Contact`.  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## Voir aussi  
 [How to: Execute a Parameterized Query](http://msdn.microsoft.com/fr-fr/42048f03-c65c-4d98-b50a-3e7d537a63e8)   
 [Langage Entity SQL](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)