---
title: "Requ&#234;tes dans LINQ to DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Requ&#234;tes dans LINQ to DataSet
Une requête est une expression qui récupère des données d'une source de données.  En général, les requêtes sont exprimées dans un langage de requête spécialisé, tel que SQL pour les bases de données relationnelles et Xquery pour XML.  Par conséquent, les développeurs ont dû apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qu'ils interrogent.  [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] offre un modèle simplifié et cohérent qui permet d'utiliser des données de types de sources et de formats diversifiés.  Dans une requête [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], vous travaillez toujours avec des objets de programmation.  
  
 Une opération de requête [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] consiste en trois actions : obtenir la ou les source\(s\) de données, créer la requête, puis l'exécuter.  
  
 Les sources de données qui implémentent l'interface générique de <xref:System.Collections.Generic.IEnumerable%601> peuvent être interrogées via [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)].  L'appel de <xref:System.Data.DataTableExtensions.AsEnumerable%2A> sur une <xref:System.Data.DataTable> retourne un objet qui implémente l'interface générique <xref:System.Collections.Generic.IEnumerable%601>, qui sert de source de données pour les requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].  
  
 Dans la requête, vous spécifiez exactement les informations que vous voulez récupérer à partir de la source de données.  Une requête peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées.  Dans [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)], une requête est stockée dans une variable.  Si la requête est conçue pour retourner une séquence de valeurs, la variable de requête doit elle\-même être de type dénombrable.  Cette variable de requête n'effectue aucune action et ne retourne aucune donnée ; elle stocke uniquement les informations de requête.  Une fois que vous avez créé une requête, vous devez l'exécuter pour extraire des données.  
  
 Dans une requête qui retourne une séquence, la variable de requête elle\-même ne contient jamais les résultats de la requête et stocke uniquement les commandes de requête.  L'exécution de la requête est différée jusqu'à ce que la variable de requête soit itérée au sein d'une boucle `foreach` ou `For Each`.  C'est ce que l'on appelle *exécution différée*. Autrement dit, l'exécution de la requête a lieu un certain temps après sa construction.  Vous pouvez ainsi exécuter une requête aussi souvent que vous le souhaitez.  Cela est utile lorsque, par exemple, l'une de vos bases de données est en cours de mise à jour par d'autres applications.  Dans votre application, vous pouvez créer une requête pour récupérer les informations les plus récentes et l'exécuter à plusieurs reprises, pour retourner chaque fois les informations à jour.  
  
 Contrairement aux requêtes différées qui retournent une séquence de valeurs, les requêtes qui retournent une valeur singleton sont exécutées immédiatement.  Les requêtes <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Average%2A> et <xref:System.Linq.Enumerable.First%2A> en sont quelques exemples.  Elles s'exécutent immédiatement parce que les résultats de la requête sont nécessaires pour calculer le résultat singleton.  Par exemple, pour trouver la moyenne des résultats, la requête doit être exécutée pour que la fonction de moyenne dispose de données sur lesquelles effectuer ses calculs.  Vous pouvez également utiliser les méthodes <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A> sur une requête pour forcer l'exécution immédiate d'une requête qui ne produit pas de valeur singleton.  Ces techniques peuvent être utiles lorsque vous souhaitez mettre en cache les résultats d'une requête.  Pour plus d'informations sur l'exécution de requête différée et immédiate, voir [Getting Started with LINQ](http://msdn.microsoft.com/fr-fr/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9).  
  
## Requêtes  
 Les requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] peuvent être formulées dans deux syntaxes différentes : la syntaxe d'expression de requête et la syntaxe de requête fondée sur une méthode.  
  
### Syntaxe d'expression de requête  
 Les expressions de requête utilisent une syntaxe de requête déclarative.  Cette syntaxe permet au développeur d'écrire des requêtes en C\# ou Visual Basic dans un format similaire à SQL.  En utilisant la syntaxe d'expression de requête, vous pouvez même effectuer des opérations de filtrage, de classement et de regroupement complexes sur des sources de données avec un minimum de code.  Pour plus d’informations, consultez [Expressions de requête \(LINQ\)](../Topic/LINQ%20Query%20Expressions%20\(C%23%20Programming%20Guide\).md) et [Opérations de requête de base \(Visual Basic\)](../Topic/Basic%20Query%20Operations%20\(Visual%20Basic\).md).  
  
 La syntaxe d'expression de requête est une caractéristique nouvelle dans C\# 3.0 et [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)].  Toutefois, le Common Language Runtime \(CLR\) du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ne peut pas lire la syntaxe d'expression de requête proprement dite.  Par conséquent, au moment de la compilation, les expressions de requête sont traduites en appels de méthodes pour que le CLR puisse les comprendre.  Ces méthodes sont appelées *opérateurs de requête standard*.  En tant que développeur, vous pouvez les appeler directement en utilisant la syntaxe de méthode plutôt que la syntaxe de requête.  Pour plus d'informations, consultez [Query Syntax and Method Syntax in LINQ](../Topic/Query%20Syntax%20and%20Method%20Syntax%20in%20LINQ%20\(C%23\).md).  Pour plus d'informations sur l'utilisation des opérateurs de requête standard, voir [NOT IN BUILD: LINQ General Programming Guide](http://msdn.microsoft.com/fr-fr/609c7a6b-cbdd-429d-99f3-78d13d3bc049).  
  
 L'exemple ci\-dessous utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de la table `Product` et afficher les noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### Syntaxe de requête fondée sur une méthode  
 L'autre manière de formuler des requêtes [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] consiste à utiliser des requêtes fondées sur une méthode.  La syntaxe de requête fondée sur une méthode est une séquence d'appels directs de méthodes d'opérateur [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] passant des expressions lambda comme paramètres.  Pour plus d'informations, consultez [Expressions lambda](../Topic/Lambda%20Expressions%20\(C%23%20Programming%20Guide\).md).  
  
 Cet exemple utilise <xref:System.Linq.Enumerable.Select%2A> pour retourner toutes les lignes de `Product` et afficher les noms de produits.  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## Composition de requêtes  
 Comme mentionné précédemment dans cette rubrique, la variable de requête elle\-même ne stocke les commandes de requête que lorsque la requête est conçue pour retourner une séquence de valeurs.  Si la requête ne contient pas de méthode qui déclenche une exécution immédiate, l'exécution effective de la requête est différée jusqu'à ce que vous itériez au sein de la variable de requête dans une boucle `foreach` ou `For Each`.  L'exécution différée permet de combiner plusieurs requêtes ou d'étendre une requête.  Lorsqu'une requête est étendue, elle est modifiée de manière à inclure les nouvelles opérations, et l'exécution finale reflète les modifications.  Dans l'exemple suivant, la première requête retourne tous les produits.  La deuxième requête étend la première en utilisant `Where` pour retourner tous les produits de taille « L » :  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 Après l'exécution d'une requête, aucune requête supplémentaire ne peut être composée, et toutes les requêtes suivantes utilisent les opérateurs [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] en mémoire.  L'exécution de la requête a lieu lorsque vous itérez au sein de la variable de requête dans une déclaration `foreach` ou `For Each`, ou par un appel à l'un des opérateurs de conversion [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] qui provoquent une exécution immédiate.  Ces opérateurs sont notamment : <xref:System.Linq.Enumerable.ToList%2A>, <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToLookup%2A> et <xref:System.Linq.Enumerable.ToDictionary%2A>.  
  
 Dans l'exemple suivant, la première requête retourne tous les produits triés par tarif.  La méthode <xref:System.Linq.Enumerable.ToArray%2A> est utilisée pour forcer l'exécution immédiate de la requête :  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## Voir aussi  
 [Guide de programmation](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)   
 [Interrogation de DataSets](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)   
 [Getting Started with LINQ in C\#](../Topic/Getting%20Started%20with%20LINQ%20in%20C%23.md)   
 [Getting Started with LINQ in Visual Basic](../Topic/Getting%20Started%20with%20LINQ%20in%20Visual%20Basic.md)