---
title: "Basic LINQ Query Operations (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "orderby clause [LINQ in C#]"
  - "ordering data [LINQ in C#]"
  - "selecting data [LINQ in C#]"
  - "queries [LINQ in C#], basic operations"
  - "grouping data [LINQ in C#]"
  - "data sources [LINQ in C#]"
  - "sorting data [LINQ in C#]"
  - "projections [LINQ in C#]"
  - "filtering data [LINQ in C#]"
  - "joining data [LINQ in C#]"
  - "select clause [LINQ in C#]"
  - "LINQ [C#], basic query operations"
  - "join clause [LINQ in C#]"
  - "group clause [LINQ in C#]"
ms.assetid: a7ea3421-1cf4-4df7-832a-aa22fe6379e9
caps.latest.revision: 39
caps.handback.revision: 37
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Basic LINQ Query Operations (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cette rubrique présente brièvement les expressions de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] et quelques\-uns des types d'opérations classiques que vous effectuez dans une requête.  Vous trouverez des informations plus détaillées dans les rubriques suivantes :  
  
 [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
  
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
  
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
  
> [!NOTE]
>  Si vous êtes déjà familiarisé avec un langage de requête comme SQL ou XQuery, vous pouvez ignorer la majorité de cette rubrique.  Consultez le paragraphe « Clause `from` » de la section suivante pour en savoir plus sur l'ordre des clauses dans les expressions de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  
  
## Obtention d'une source de données  
 Dans une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], la première étape consiste à spécifier la source de données.  En C\# comme dans la plupart des langages de programmation, une variable doit être déclarée avant de pouvoir être utilisée.  Dans une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], la clause `from` apparaît en premier pour introduire la source de données \(`customers`\) et la *variable de portée* \(`cust`\).  
  
 [!code-cs[csLINQGettingStarted#23](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_1.cs)]  
  
 La variable de portée est similaire à la variable d'itération dans une boucle `foreach`, à la différence qu'aucune itération réelle ne se produit dans une expression de requête.  Lorsque la requête est exécutée, la variable de portée servira de référence à chaque élément consécutif dans `customers`.  Étant donné que le compilateur peut déduire le type de `cust`, vous n'avez pas à le spécifier explicitement.  Des variables de portée supplémentaires peuvent être introduites par une clause `let`.  Pour plus d'informations, consultez [let, clause](../../../../csharp/language-reference/keywords/let-clause.md).  
  
> [!NOTE]
>  Pour les sources de données non génériques telles que <xref:System.Collections.ArrayList>, la variable de portée doit être explicitement typée.  Pour plus d'informations, consultez [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md) et [from, clause](../../../../csharp/language-reference/keywords/from-clause.md).  
  
## Filtrage  
 L'opération de requête la plus courante est probablement l'application d'un filtre sous forme d'expression booléenne.  Du fait du filtre, la requête retourne uniquement les éléments pour lesquels l'expression a la valeur true.  Le résultat est produit à l'aide de la clause `where`.  Le filtre activé spécifie les éléments à exclure de la séquence source.  Dans l'exemple suivant, seuls les `customers` qui ont une adresse à Londres sont retournés.  
  
 [!code-cs[csLINQGettingStarted#24](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_2.cs)]  
  
 Vous pouvez utiliser les opérateurs logiques C\# `AND` et `OR` habituels pour appliquer autant d'expressions de filtre que nécessaire dans la clause `where`.  Par exemple, pour retourner uniquement les clients de « Londres » ET `AND` dont le nom est « Devon », vous écrirez le code suivant :  
  
 [!code-cs[csLINQGettingStarted#25](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_3.cs)]  
  
 Pour retourner les clients de Londres ou Paris, vous écrirez le code suivant :  
  
 [!code-cs[csLINQGettingStarted#26](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_4.cs)]  
  
 Pour plus d'informations, consultez [where, clause](../../../../csharp/language-reference/keywords/where-clause.md).  
  
## Ordering  
 Souvent, il est utile de trier les données retournées.  La clause `orderby` triera les éléments de la séquence retournée d'après le comparateur par défaut pour le type qui est trié.  Par exemple, la requête suivante peut être étendue pour trier les résultats selon la propriété `Name`.  Étant donné que `Name` est une chaîne, le comparateur par défaut effectue un tri alphabétique de A à Z.  
  
 [!code-cs[csLINQGettingStarted#27](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_5.cs)]  
  
 Pour classer les résultats dans l'ordre inverse, de Z à A, utilisez la clause `orderby…descending`.  
  
 Pour plus d'informations, consultez [orderby, clause](../../../../csharp/language-reference/keywords/orderby-clause.md).  
  
## Regroupement  
 La clause `group` vous permet de grouper vos résultats selon une clé que vous spécifiez.  Par exemple, vous pouvez spécifier un regroupement des résultats par `City` de sorte que tous les clients de Londres ou Paris soient dans des groupes individuels.  Dans ce cas, `cust.City` est la clé.  
  
 [!code-cs[csLINQGettingStarted#28](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_6.cs)]  
  
 Lorsque vous terminez une requête avec une clause `group`, vos résultats prennent la forme d'une liste de listes.  Chaque élément de la liste est un objet qui a un membre `Key` et une liste d'éléments groupés sous cette clé.  Lorsque vous itérez sur une requête qui produit une séquence de groupes, vous devez utiliser une boucle `foreach` imbriquée.  La boucle externe itère sur chaque groupe et la boucle interne itère au sein des membres de chaque groupe.  
  
 Si vous devez faire référence aux résultats d'une opération de groupe, vous pouvez utiliser le mot clé `into` pour créer un identificateur qui peut être interrogé ultérieurement.  La requête suivante retourne uniquement les groupes qui contiennent plus de deux clients :  
  
 [!code-cs[csLINQGettingStarted#29](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_7.cs)]  
  
 Pour plus d'informations, consultez [group, clause](../../../../csharp/language-reference/keywords/group-clause.md).  
  
## Jointure  
 Les opérations de jointure créent des associations entre les séquences qui ne sont pas modelées explicitement dans les sources de données.  Par exemple, vous pouvez effectuer une jointure pour rechercher tous les clients et distributeurs qui ont le même emplacement.  Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], la clause `join` fonctionne toujours par rapport à des collections d'objets plutôt que directement par rapport à des tables de base de données.  
  
 [!code-cs[csLINQGettingStarted#36](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/basic-linq-query-operations_8.cs)]  
  
 Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], il n'est pas nécessaire d'utiliser `join` aussi souvent que vous le faites dans SQL, car les clés étrangères dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] sont représentées dans le modèle objet comme des propriétés qui stockent une collection d'éléments.  Par exemple, un objet `Customer` contient une collection d'objets `Order`.  Au lieu d'effectuer une jointure, vous accédez aux commandes en utilisant la notation par point :  
  
```  
from order in Customer.Orders...  
```  
  
 Pour plus d'informations, consultez [join, clause](../../../../csharp/language-reference/keywords/join-clause.md).  
  
## Sélection \(projections\)  
 La clause `select` produit les résultats de la requête et spécifie la « forme » ou le type de chaque élément retourné.  Par exemple, vous pouvez spécifier si vos résultats se composeront d'objets `Customer` complets, d'un seul membre, d'un sous\-ensemble de membres ou d'un type de résultat complètement différent basé sur un calcul ou une création d'objet.  Lorsque la clause `select` produit autre chose qu'une copie de l'élément source, l'opération est appelée *projection*.  L'utilisation de projections pour transformer des données est une fonction puissante des expressions de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Pour plus d'informations, consultez [Transformations de données avec LINQ \(C\#\)](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md) et [select, clause](../../../../csharp/language-reference/keywords/select-clause.md).  
  
## Voir aussi  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Mots clés de requête \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [Types anonymes](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)   
 [Opérations de requête de base \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)