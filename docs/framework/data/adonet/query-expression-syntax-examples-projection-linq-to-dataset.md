---
title: "Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: projection (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Exemples de syntaxe d&#39;expression de requ&#234;te&#160;: projection (LINQ to DataSet)
Les exemples de cette rubrique montrent comment utiliser les méthodes <xref:System.Linq.Enumerable.Select%2A> et <xref:System.Linq.Enumerable.SelectMany%2A> pour interroger un <xref:System.Data.DataSet> à l'aide de la syntaxe d'expression de requête.  
  
 La méthode `FillDataSet` utilisée dans ces exemples est spécifiée dans [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).  
  
 Les exemples de cette rubrique utilisent les tables Contact, Address, Product, SalesOrderHeader et SalesOrderDetail de l'exemple de base de données AdventureWorks.  
  
 Les exemples de cette rubrique utilisent les instructions `using`\/`Imports` suivantes :  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 Pour plus d'informations, consultez [Procédure : créer un projet LINQ to DataSet dans Visual Studio](../../../../docs/framework/data/adonet/how-to-create-a-linq-to-dataset-project-in-vs.md).  
  
## Sélectionner  
  
### Exemple  
 Cet exemple utilise la méthode <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de la table `Product` et afficher les noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### Exemple  
 Cet exemple utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner une séquence comportant uniquement des noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## SelectMany  
  
### Exemple  
 Cet exemple utilise `From …, …` \(l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>\) pour sélectionner toutes les commandes où le `TotalDue` est inférieur à 500.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### Exemple  
 Cet exemple utilise `From …, …` \(l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>\) pour sélectionner toutes les commandes qui ont été passées le 1er octobre 2002 ou après.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### Exemple  
 Cet exemple utilise un `From …, …` \(l'équivalent de la méthode <xref:System.Linq.Enumerable.SelectMany%2A>\) pour sélectionner toutes les commandes dont le total est supérieur à 10 000 et utilise l'assignation `From` pour éviter de demander deux fois le total.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## Voir aussi  
 [Chargement de données dans un DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)   
 [Exemples de LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)   
 [Standard Query Operators Overview](../../../../ocs/visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)