---
title: "Proc&#233;dure&#160;: afficher le code SQL g&#233;n&#233;r&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 626492c0-5ee3-4675-88e8-8c40379510b6
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: afficher le code SQL g&#233;n&#233;r&#233;
Vous pouvez consulter le code SQL généré pour les requêtes et modifier le traitement à l'aide de la propriété <xref:System.Data.Linq.DataContext.Log%2A>.  Cette approche peut être utile pour comprendre les fonctionnalités de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] et déboguer des problèmes spécifiques.  
  
## Exemple  
 L'exemple suivant utilise la propriété <xref:System.Data.Linq.DataContext.Log%2A> pour afficher le code SQL dans la fenêtre de console avant que son exécution.  Vous pouvez utiliser cette propriété avec les commandes de requête, d'insertion, de mise à jour et de suppression.  
  
 Les lignes de la fenêtre de console sont celles qui s'affichent lorsque vous exécutez le code [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] ou C\# suivant.  
  
```  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
-- @p0: Input String (Size = 6; Prec = 0; Scale = 0) [London]  
-- Context: SqlProvider(Sql2005) Model: AttributedMetaModel Build: 3.5.20810.0  
```  
  
```  
AROUT  
BSBEV  
CONSH  
EASTC  
NORTS  
SEVES  
```  
  
 [!code-csharp[DLinqDebuggingSupport#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#1)]
 [!code-vb[DLinqDebuggingSupport#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#1)]  
  
## Voir aussi  
 [Prise en charge du débogage](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)