---
title: "Ajout d'une logique métier à l'aide de méthodes partielles"
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
ms.assetid: 3a73991e-fd4e-4610-93fb-7ced4dc6b7f9
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9704ad7d4030ee85701f1f95f87c539c1fbd0122
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-business-logic-by-using-partial-methods"></a>Ajout d'une logique métier à l'aide de méthodes partielles
Vous pouvez personnaliser [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] et c# généré le code dans votre [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projets à l’aide de *méthodes partielles*. Le code généré par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] définit des signatures comme faisant partie d'une méthode partielle. Si vous souhaitez implémenter la méthode, vous pouvez ajouter votre propre méthode partielle. Si vous n'ajoutez pas votre propre implémentation, le compilateur ignore la signature de méthodes partielles et appelle les méthodes par défaut dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour ajouter une validation et d'autres personnalisations aux classes d'entité.  
  
 Par exemple, le mappage par défaut pour la classe `Customer` dans l'exemple de base de données Northwind inclut la méthode partielle suivante :  
  
 [!code-csharp[DLinqOverrideDefault#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefault#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#2)]  
  
 Vous pouvez implémenter votre propre méthode en ajoutant du code tel que le suivant à votre propre classe `Customer` partielle :  
  
 [!code-csharp[DLinqOverrideDefault#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefault#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/Module1.vb#3)]  
  
 Cette approche est généralement utilisée dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] à substituer les méthodes par défaut pour `Insert`, `Update`, `Delete`et pour valider les propriétés pendant les événements de cycle de vie d’objet.  
  
 Pour plus d’informations, consultez [méthodes partielles](~/docs/visual-basic/programming-guide/language-features/procedures/partial-methods.md) ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) ou [partielle (méthode) (référence c#)](~/docs/csharp/language-reference/keywords/partial-method.md) (c#).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple suivant montre d'abord `ExampleClass` tel qu'il pourrait être défini par un outil de génération de code tel que SQLMetal, puis comment vous pouvez implémenter l'une des deux méthodes seulement.  
  
### <a name="code"></a>Code  
 [!code-csharp[DLinqSubmittingChanges#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#4)]
 [!code-vb[DLinqSubmittingChanges#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#4)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple suivant utilise la relation entre les entités `Shipper` et `Order`. Notez parmi les méthodes celles qui sont partielles, `InsertShipper` et `DeleteShipper`. Ces méthodes substituent les méthodes partielles par défaut fournis par [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappage.  
  
### <a name="code"></a>Code  
 [!code-csharp[DLinqOverrideDefault#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefault/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefault#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefault/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [Personnalisation des opérations d’insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
