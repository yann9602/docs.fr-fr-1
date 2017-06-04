---
title: "Proc&#233;dure&#160;: mettre entre parenth&#232;ses des soumissions de donn&#233;es &#224; l&#39;aide de transactions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94044a31-de90-479b-935a-8159b4ae5c5a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: mettre entre parenth&#232;ses des soumissions de donn&#233;es &#224; l&#39;aide de transactions
Vous pouvez utiliser <xref:System.Transactions.TransactionScope> pour mettre entre parenthèses vos soumissions à la base de données.  Pour plus d'informations, consultez [Prise en charge des transactions](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md).  
  
## Exemple  
 Le code suivant place la soumission de base de données dans un <xref:System.Transactions.TransactionScope>.  
  
 [!code-csharp[DLinqSubmittingChanges#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#3)]
 [!code-vb[DLinqSubmittingChanges#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#3)]  
  
## Voir aussi  
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)   
 [Prise en charge des transactions](../../../../../../docs/framework/data/adonet/sql/linq/transaction-support.md)