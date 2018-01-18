---
title: "Comment : représenter des colonnes en tant que colonnes générées par une base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a404451b1dca085707d05d1db54047cd0db0c986
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-represent-columns-as-database-generated"></a>Comment : représenter des colonnes en tant que colonnes générées par une base de données
Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriété sur le <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant d’une colonne de base de données générée.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a>Pour désigner un champ ou une propriété comme représentant d'une colonne générée par une base de données  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Affectez la valeur `true`.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Guide pratique pour personnaliser des classes d’entité à l’aide de l’éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
