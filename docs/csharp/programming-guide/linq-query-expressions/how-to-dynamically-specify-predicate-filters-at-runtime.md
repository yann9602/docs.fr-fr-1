---
title: "Comment&#160;: sp&#233;cifier dynamiquement des filtres de pr&#233;dicat au moment de l&#39;ex&#233;cution (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "requêtes dynamiques (LINQ en C#)"
  - "filtres de prédicats (C#)"
  - "prédicats (C#)"
  - "requêtes (LINQ en C#), filtres de prédicats"
  - "expressions de requête (LINQ en C#), filtres de prédicats"
ms.assetid: 52f2dc7a-8353-4c6e-98d3-eec99a907a5f
caps.latest.revision: 22
caps.handback.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: sp&#233;cifier dynamiquement des filtres de pr&#233;dicat au moment de l&#39;ex&#233;cution (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans certains cas vous ne savez pas, jusqu'à l'exécution, combien de prédicats vous devez appliquer aux éléments source dans la clause `where`.  Une façon de spécifier plusieurs filtres de prédicat de manière dynamique est d'utiliser la méthode <xref:System.Linq.Enumerable.Contains%2A>, comme indiqué dans l'exemple suivant.  L'exemple est construit de deux façons.  En premier lieu, le projet est exécuté en filtrant sur les valeurs fournies dans le programme.  Le projet est ensuite à nouveau exécuté à l'aide de l'entrée fourni au moment de l'exécution.  
  
### Pour filtrer à l'aide de la méthode Contains  
  
1.  Ouvrez un projet d'application console dans Visual Studio.  Nommez\-le `PredicateFilters`.  
  
2.  Copiez la classe `StudentClass` à partir de [Comment : interroger une collection d'objets](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) et collez\-la dans `PredicateFilters` l'espace de noms sous la classe `Program`.  `StudentClass` fournit une liste d'objets `Student`.  
  
3.  Commentez la méthode `Main` dans `StudentClass`.  
  
4.  Remplacez la classe `Program` par le code suivant.  
  
     [!code-cs[csProgGuideLINQ#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Ajoutez la ligne suivante à la méthode `Main` dans la classe `DynamicPredicates`, sous la déclaration d'`ids`.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
6.  Appuyez sur F5 pour exécuter le projet.  
  
7.  La sortie suivante est affichée dans une fenêtre d'invite de commandes :  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  L'étape suivante consiste à exécuter à nouveau le projet, en utilisant cette fois l'entrée datant du moment de l'exécution au lieu du tableau `ids`.  Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur **PredicateFilters**, puis cliquez sur **Propriétés**.  
  
9. Cliquez sur l'onglet **Débogage**.  
  
10. Dans la fenêtre **Arguments de la ligne de commande**, tapez 122, 117, 120 et 115, séparés par des espaces : `122 117 120 115`.  Lorsque le projet est exécuté, ces valeurs deviennent des éléments d'`args`, le paramètre de la méthode `Main`.  
  
11. Remplacez `QueryByID(ids)` par `QueryByID(args)` dans la méthode `Main`.  
  
12. Appuyez sur F5 pour exécuter le projet.  
  
13. La sortie suivante est affichée dans une fenêtre d'invite de commandes :  
  
     Adams: 120  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
### Pour filtrer à l'aide d'une instruction switch  
  
1.  Vous pouvez utiliser une instruction `switch` pour effectuer une sélection parmi d'autres requêtes prédéterminées.  Dans l'exemple suivant, `studentQuery` utilise une clause `where` différente selon le niveau ou l'année, spécifiée au moment de l'exécution.  
  
2.  Copiez la méthode suivante et collez\-la dans la classe `DynamicPredicates`.  
  
     [!code-cs[csProgGuideLINQ#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  Dans la fenêtre **Arguments de la ligne de commande**, remplacez les numéros d'ID de la procédure précédente par une valeur entière comprise entre 1 et 4.  
  
4.  Dans la méthode `Main`, remplacez l'appel à `QueryByID` par l'appel suivant, qui envoie le premier élément à partir du tableau `args` en tant que son argument : `QueryByYear(args[0])`.  
  
5.  Appuyez sur F5 pour exécuter le projet.  
  
### Pour utiliser cette méthode dans vos propres applications  
  
-   Lorsque vous adaptez cette méthode à votre propre application, souvenez\-vous que LINQ requiert la version 3.5 ou 4 du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et que le projet doit contenir une référence à System.Core.dll et une directive `using` pour `System.Linq`.  Les types LINQ to SQL, LINQ to XML et LINQ to DataSet requièrent des directives et des références `using` supplémentaires.  Pour plus d'informations, consultez [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  
  
## Voir aussi  
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [where, clause](../../../csharp/language-reference/keywords/where-clause.md)