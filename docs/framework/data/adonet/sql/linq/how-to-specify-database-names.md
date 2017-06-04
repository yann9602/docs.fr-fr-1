---
title: "Proc&#233;dure&#160;: sp&#233;cifier des noms de bases de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: sp&#233;cifier des noms de bases de donn&#233;es
Utilisez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> sur un attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> pour spécifier le nom d'une base de données lorsque la connexion ne fournit pas de nom.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### Pour spécifier le nom de la base de données  
  
1.  Ajoutez l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> à la déclaration de classe de la base de données.  
  
2.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> à l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
3.  Affectez le nom que vous souhaitez spécifier à la valeur de propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
## Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)