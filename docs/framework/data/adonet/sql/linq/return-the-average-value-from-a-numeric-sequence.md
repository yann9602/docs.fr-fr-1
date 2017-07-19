---
title: "Retourner la valeur moyenne d&#39;une s&#233;quence num&#233;rique | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Retourner la valeur moyenne d&#39;une s&#233;quence num&#233;rique
L'opérateur <xref:System.Linq.Enumerable.Average%2A> calcule la moyenne d'une séquence de valeurs numériques.  
  
> [!NOTE]
>  La traduction [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] de la `Average` de valeurs entières est calculée comme un entier, non comme un double.  
  
## Exemple  
 L'exemple suivant retourne la moyenne de valeurs `Freight` dans la table `Orders`.  
  
 Les résultats de l'exemple de base de données Northwind seraient `78.2442`.  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## Exemple  
 L'exemple suivant retourne le prix unitaire moyen de tous les produits \(`Products`\) dans la table `Products`.  
  
 Les résultats de l'exemple de base de données Northwind seraient `28.8663`.  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## Exemple  
 L'exemple suivant utilise l'opérateur `Average` pour rechercher ces `Products` dont le prix unitaire est plus élevé que le prix unitaire moyen de la catégorie à laquelle il appartient.  L'exemple affiche ensuite les résultats par groupes.  
  
 Notez que cet exemple requiert l'utilisation du mot clé `var` en C\#, car le type de retour est anonyme.  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 Si vous exécutez cette requête sur l'exemple de base de données Northwind, les résultats doivent se présenter comme suit :  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## Voir aussi  
 [Requêtes d'agrégation](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)