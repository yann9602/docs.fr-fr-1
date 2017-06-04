---
title: "Proc&#233;dure&#160;: repr&#233;senter des colonnes calcul&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: repr&#233;senter des colonnes calcul&#233;es
Utilisez la propriété [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> sur un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> pour représenter une colonne dont le contenu est le résultat de calculs.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge les colonnes calculées en tant que clés primaires.  
  
### Pour représenter une colonne calculée  
  
1.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2.  Assignez une représentation sous forme de chaîne de la formule à la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.  
  
## Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)