---
title: "Comment : regrouper des éléments dans une séquence"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b3cf24760c826cf3dac75305eedb33b732869ff1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="group-elements-in-a-sequence"></a>Comment : regrouper des éléments dans une séquence
L'opérateur <xref:System.Linq.Enumerable.GroupBy%2A> regroupe les éléments d'une séquence. Les exemples suivants utilisent la base de données Northwind.  
  
> [!NOTE]
>  Les valeurs de colonne null dans les requêtes <xref:System.Linq.Enumerable.GroupBy%2A> peuvent parfois lever une exception <xref:System.InvalidOperationException>. Pour plus d’informations, consultez la section « GroupBy InvalidOperationException » de [dépannage](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant partitionne `Products` par `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Enumerable.Max%2A> pour rechercher le prix unitaire maximal pour chaque `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise Average pour rechercher le `UnitPrice` moyen pour chaque `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Queryable.Sum%2A> pour rechercher le `UnitPrice` total pour chaque `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise <xref:System.Linq.Queryable.Count%2A> pour rechercher le nombre de `Products` de fin de série dans chaque `CategoryID`.  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise une clause `where` pour rechercher toutes les catégories comportant au moins 10 produits.  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant regroupe les produits par `CategoryID` et `SupplierID`.  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a>Exemple  
 L'exemple suivant retourne deux séquences de produits. La première séquence contient des produits dont le prix unitaire est inférieur ou égal à 10. La deuxième séquence contient des produits dont le prix unitaire est supérieur à 10.  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a>Exemple  
 L'opérateur <xref:System.Linq.Queryable.GroupBy%2A> ne peut prendre qu'un argument Key. Pour effectuer un regroupement sur plusieurs clés, vous devez créer un type anonyme, comme dans l'exemple suivant :  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples de requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
