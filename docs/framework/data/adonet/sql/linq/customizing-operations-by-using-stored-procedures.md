---
title: "Personnalisation d'opérations à l'aide de procédures stockées"
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
ms.assetid: aedbecc1-c33c-4fb4-8861-fdf7e1dc6b8a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5433ef17ec2eec7fe80145a6356d230b9d01a7d5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-by-using-stored-procedures"></a>Personnalisation d'opérations à l'aide de procédures stockées
Les procédures stockées représentent une approche courante de la substitution du comportement par défaut. Les exemples de cette rubrique vous indiquent comment utiliser des wrappers de méthodes générés pour les procédures stockées et comment appeler directement des procédures stockées.  
  
 Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour assigner des procédures stockées afin d'effectuer des insertions, des mises à jour et des suppressions.  
  
> [!NOTE]
>  Pour relire des valeurs générées par une base de données, utilisez des paramètres de sortie dans vos procédures stockées. Si vous ne pouvez pas utiliser de paramètres de sortie, écrivez une implémentation de méthode partielle au lieu de compter sur les substitutions générées par [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]. Les membres mappés aux valeurs générées par une base de données doivent avoir des valeurs appropriées une fois que les opérations `INSERT` ou `UPDATE` ont abouti avec succès. Pour plus d’informations, consultez [responsabilités du développeur de remplacement par défaut comportement](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Dans l'exemple suivant, supposez que la classe `Northwind` contient deux méthodes pour appeler des procédures stockées qui sont utilisées pour les substitutions dans une classe dérivée.  
  
### <a name="code"></a>Code  
 [!code-csharp[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#1)]
 [!code-vb[DLinqOverrideDefaultSproc#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#1)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 La classe suivante utilise ces méthodes pour la substitution.  
  
### <a name="code"></a>Code  
 [!code-csharp[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/northwind.cs#2)]
 [!code-vb[DLinqOverrideDefaultSproc#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/northwind.vb#2)]  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 Vous pouvez utiliser `NorthwindThroughSprocs` exactement comme vous utiliseriez `Northwnd`.  
  
### <a name="code"></a>Code  
 [!code-csharp[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqOverrideDefaultSproc/cs/Program.cs#3)]
 [!code-vb[DLinqOverrideDefaultSproc#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqOverrideDefaultSproc/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi  
 [Responsabilités du développeur en matière de substitution du comportement par défaut](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)
