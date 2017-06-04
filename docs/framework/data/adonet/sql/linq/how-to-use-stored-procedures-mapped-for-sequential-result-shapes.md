---
title: "Proc&#233;dure&#160;: utiliser des proc&#233;dures stock&#233;es mapp&#233;es pour des formes de r&#233;sultats s&#233;quentielles | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: utiliser des proc&#233;dures stock&#233;es mapp&#233;es pour des formes de r&#233;sultats s&#233;quentielles
Ce type de procédure stockée peut générer plusieurs formes de résultats, mais vous savez dans quel ordre les résultats sont retournés.  Comparez ce scénario à celui dans lequel vous ne connaissez pas la séquence des retours.  Pour plus d'informations, consultez [Procédure : utiliser des procédures stockées mappées pour plusieurs formes de résultats](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).  
  
## Exemple  
 Le T\-SQL d'une procédure stockée qui retourne plusieurs formes de résultats de manière séquentielle est présenté ci\-dessous :  
  
```  
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## Exemple  
 Vous pouvez utiliser un code semblable à celui qui suit pour exécuter cette procédure stockée.  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## Voir aussi  
 [Procédures stockées](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)