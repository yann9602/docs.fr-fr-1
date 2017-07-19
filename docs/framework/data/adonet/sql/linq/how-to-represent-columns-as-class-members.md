---
title: "Proc&#233;dure&#160;: repr&#233;senter des colonnes en tant que membres de classe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: repr&#233;senter des colonnes en tant que membres de classe
Utilisez l'attribut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> pour associer un champ ou une propriété à une colonne de base de données.  
  
### Pour mapper un champ ou une propriété à une colonne de base de données  
  
-   Ajoutez l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute> à la déclaration de propriété ou de champ.  
  
## Exemple  
 Le code suivant mappe le champ `CustomerID` de la classe `Customer` à la colonne `CustomerID` de la table de base de données `Customers`.  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 Il n'est pas nécessaire de spécifier la propriété <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> si le nom peut être déduit.  Si vous ne spécifiez pas de nom, on considère qu'il s'agit du même nom que pour la propriété ou le champ.  
  
## Voir aussi  
 [Modèle objet LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)   
 [Procédure : personnaliser des classes d'entité à l'aide de l'éditeur de code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)