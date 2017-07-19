---
title: "Proc&#233;dure&#160;: appeler des fonctions inline d&#233;finies par l&#39;utilisateur | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: appeler des fonctions inline d&#233;finies par l&#39;utilisateur
Bien que vous puissiez appeler des fonctions inline définies par l'utilisateur, les fonctions incluses dans une requête dont l'exécution est différée ne sont pas exécutées tant que la requête n'est pas exécutée.  Pour plus d'informations, consultez [Introduction to LINQ Queries \(C\#\)](../Topic/Introduction%20to%20LINQ%20Queries%20\(C%23\).md).  
  
 Lorsque vous appelez la même fonction à l'extérieur d'une requête, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée une requête simple à partir de l'expression d'appel de méthode.  La syntaxe SQL \(le paramètre `@p0` est lié à la constante passée\) se présente comme suit :  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] crée les éléments suivants :  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## Exemple  
 Dans la requête [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suivante, vous pouvez consulter un appel inline à la méthode de fonction `ReverseCustName` définie par l'utilisateur qui a été générée.  La fonction n'est pas exécutée immédiatement, car l'exécution de la requête est différée.  Le SQL généré pour cette requête se traduit en un appel à la fonction définie par l'utilisateur dans la base de données \(consultez le code SQL suivant la requête\).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## Voir aussi  
 [fonctions définies par l'utilisateur](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)