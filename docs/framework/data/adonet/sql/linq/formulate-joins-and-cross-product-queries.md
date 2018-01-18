---
title: "Comment : formuler des jointures et des requêtes de produit croisé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a>Comment : formuler des jointures et des requêtes de produit croisé
Les exemples suivants expliquent comment combiner les résultats de plusieurs tables.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la navigation de clé étrangère dans la `From` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause en c#) pour sélectionner toutes les commandes des clients de Londres.  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la navigation de clé étrangère dans la `Where` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` clause en c#) pour filtrer en rupture de stock `Products` dont `Supplier` est aux États-Unis.  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la navigation de clé étrangère dans la clause `From` dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (clause`from` dans C#) pour effectuer un filtrage sur les employés de Seattle et répertorier leurs territoires.  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la navigation de clé étrangère dans la `Select` clause dans [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause en c#) pour filtrer les paires d’employés où un employé est subordonné à l’autre et où les deux employés sont de la même `City`.  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a>Exemple  
 Les éléments suivants [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] exemple recherche tous les clients et commandes, permet de s’assurer que les commandes sont mis en correspondance avec les clients et garantit que chaque client de cette liste, un nom de contact est fourni.  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant joint explicitement deux tables et projette les résultats des deux tables.  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant joint explicitement trois tables et projette les résultats de chacune d'elles.  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment réaliser une `LEFT OUTER JOIN` en utilisant `DefaultIfEmpty()`. La méthode `DefaultIfEmpty()` retourne null en l'absence de `Order` pour l'`Employee`.  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant projette une expression `let` qui résulte d'une jointure.  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant affiche une `join` avec une clé composite.  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant indique comment construire une `join` où un côté est Nullable et l'autre ne l'est pas.  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
