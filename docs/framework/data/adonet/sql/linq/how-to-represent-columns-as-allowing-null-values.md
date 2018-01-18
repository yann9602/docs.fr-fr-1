---
title: "Comment : représenter des colonnes en tant que colonnes autorisant les valeurs Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 509c0554c6ce2bd02f1294fe19b1138241864ca9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a>Comment : représenter des colonnes en tant que colonnes autorisant les valeurs Null
Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriété sur le <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier que la colonne de base de données associée peut contenir des valeurs null.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a>Pour désigner une colonne comme autorisant des valeurs null  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à la propriété `true`.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
