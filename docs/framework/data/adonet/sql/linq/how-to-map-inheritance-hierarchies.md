---
title: "Proc&#233;dure&#160;: mapper des hi&#233;rarchies d&#39;h&#233;ritage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Proc&#233;dure&#160;: mapper des hi&#233;rarchies d&#39;h&#233;ritage
Pour implémenter un mappage d'héritage dans [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)], vous devez spécifier les attributs et les propriétés d'attribut sur la classe racine de la hiérarchie d'héritage, comme décrit dans les étapes suivantes.  Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent utiliser le [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] pour mapper des hiérarchies d'héritage.  Consultez [Procédure : configurer l'héritage à l'aide du Concepteur O\/R](../Topic/How%20to:%20Configure%20inheritance%20by%20using%20the%20O-R%20Designer.md).  
  
> [!NOTE]
>  Les sous\-classes ne requièrent pas de propriétés ni d'attributs spéciaux.  Notez surtout que les sous\-classes n'ont pas l'attribut <xref:System.Data.Linq.Mapping.TableAttribute>.  
  
### Pour mapper une hiérarchie d'héritage  
  
1.  Ajoutez l'attribut <xref:System.Data.Linq.Mapping.TableAttribute> à la classe racine.  
  
2.  Ajoutez\-lui également un attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> pour chaque classe dans la structure hiérarchique.  
  
3.  Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, définissez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
     Cette propriété contient une valeur qui apparaît dans la table de base de données dans la colonne <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour indiquer à quelle classe ou sous\-classe appartient cette ligne de données.  
  
4.  Pour chaque attribut <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute>, ajoutez également une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A>.  
  
     Cette propriété contient une valeur qui spécifie la classe ou la sous\-classe que la valeur de clé désigne.  
  
5.  Ajoutez une propriété <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> à un seul des attributs <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A>.  
  
     Cette propriété sert à désigner un mappage de *secours* lorsque la valeur de discriminateur de la table de base de données ne correspond à aucune valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> dans les mappages d'héritage.  
  
6.  Ajoutez une propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> pour un attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
     Cette propriété signifie qu'il s'agit de la colonne qui contient la valeur <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>.  
  
## Exemple  
  
> [!NOTE]
>  Si vous utilisez [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], vous pouvez configurer l'héritage à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  Consultez [Procédure : configurer l'héritage à l'aide du Concepteur O\/R](../Topic/How%20to:%20Configure%20inheritance%20by%20using%20the%20O-R%20Designer.md).  
  
 Dans l'exemple de code suivant, `Vehicle` est défini comme classe racine. Les étapes précédentes ont été implémentées pour décrire la hiérarchie de [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## Voir aussi  
 [Prise en charge de l'héritage](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)   
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)