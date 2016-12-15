---
title: "Query Syntax and Method Syntax in LINQ (C#) | Microsoft Docs"
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
  - "LINQ [C#], query syntax vs. method syntax"
  - "queries [LINQ in C#], syntax comparisons"
ms.assetid: eedd6dd9-fec2-428c-9581-5b8783810ded
caps.latest.revision: 30
caps.handback.revision: 28
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Query Syntax and Method Syntax in LINQ (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La plupart des requêtes dans la documentation préliminaire de langage Integrated Query \([!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]\) sont écrites à l'aide de la syntaxe déclarative de requête LINQ.  Toutefois, la syntaxe de requête doit être traduite en appels de méthode pour le common langage runtime \(CLR\) .NET lorsque le code est compilé.  Ces appels de méthode appelle les opérateurs de requête standard, qui ont des noms tels qu' `Where`, `Select`, `GroupBy`, `Join`, `Max`, et `Average`.  Vous pouvez les appeler directement à l'aide de la syntaxe de méthode au lieu de la syntaxe de requête.  
  
 La syntaxe de requête et la syntaxe de méthode sont sémantiquement identiques, mais de nombreuses personnes recherchez la syntaxe de requête plus simple et plus facile à lire.  Certaines requêtes doivent être exprimées comme un appel de méthode.  Par exemple, vous devez utiliser un appel de méthode pour exprimer une requête qui récupère le nombre d'éléments qui correspondent à une condition spécifiée.  Vous devez également utiliser un appel de méthode pour une requête qui récupère l'élément qui a la valeur maximale dans une séquence source.  En général, la documentation de référence pour les opérateurs de requête standard dans l'espace de noms <xref:System.Linq> utilise la syntaxe de méthode.  Par conséquent, même lorsque vous commencez à écrire des requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], il est utile de se familiariser avec l'utilisation de la syntaxe de méthode dans les requêtes et dans les expressions de requête elles\-mêmes.  
  
## Méthodes d'extension d'opérateur de requête standard  
 L'exemple suivant présente une *expression de requête* simple et la requête sémantiquement équivalente écrite comme une *requête basée sur une méthode*.  
  
 [!code-cs[csLINQGettingStarted#22](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/query-syntax-and-method-syntax-in-linq_1.cs)]  
  
 La sortie des deux exemples est identique.  Vous pouvez voir que le type de la variable de requête est le même dans les deux formes : <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Pour comprendre la requête basée sur une méthode, examinons\-la plus attentivement.  Du côté droit de l'expression, remarquez que la clause `where` est maintenant exprimée comme une méthode d'instance sur l'objet `numbers`, qui, comme vous pouvez vous en rappeler, a un type `IEnumerable<int>`.  Si vous êtes un habitué de l'interface <xref:System.Collections.Generic.IEnumerable%601> générique, vous savez qu'elle n'a pas de méthode `Where`.  Toutefois, si vous appelez la liste de saisie semi\-automatique IntelliSense dans l'IDE de Visual Studio, vous ne verrez pas seulement une méthode `Where`, mais de nombreuses autres méthodes telles que `Select`, `SelectMany`, `Join` et `Orderby`.  Il s'agit de tous les opérateurs de requête standard.  
  
 ![Opérateurs de requête standard dans Intellisense](../../../../csharp/programming-guide/concepts/linq/media/standardqueryops.png "StandardQueryOps")  
  
 Même s'il semble que <xref:System.Collections.Generic.IEnumerable%601> a été redéfini pour inclure ces méthodes supplémentaires, ce n'est pas le cas, en réalité.  Les opérateurs de requête standard sont implémentés comme nouveau type de méthode appelé *méthodes d'extension*.  Les méthodes d'extensions « étendent » un type existant ; elles peuvent être appelées comme s'il s'agissait de méthodes d'instance sur le type.  Les opérateurs de requête standard étendent <xref:System.Collections.Generic.IEnumerable%601> et c'est pourquoi vous pouvez écrire `numbers.Where(...)`.  
  
 Pour commencer à utiliser [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], tout ce que vous devez savoir sur les méthodes d'extension est la façon de les mettre à portée de votre application à l'aide des directives `using` appropriées.  Cette opération est expliquée plus en détails dans [How to: Create a LINQ Project](../Topic/How%20to:%20Create%20a%20LINQ%20Project.md).  Du point de vue de votre application, une méthode d'extension et une méthode d'instance normale n'ont pas de différence.  
  
 Pour plus d'informations sur les méthodes d'extension, consultez [Méthodes d'extension](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).  Pour plus d'informations sur les opérateurs de requête standard, consultez [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  Certains fournisseurs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], comme [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] et [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], implémentent leurs propres opérateurs de requête standard et leurs propres méthodes d'extension supplémentaires pour d'autres types que <xref:System.Collections.Generic.IEnumerable%601>.  
  
## Expressions lambda  
 Dans l'exemple précédent, notez que l'expression conditionnelle \(`num % 2 == 0`\) est passée comme argument intégré à la méthode d' `Where` : `Where(num => num % 2 == 0).`cette expression inline est appelé une expression lambda.  C'est un moyen pratique d'écrire du code qui devrait normalement être écrit de façon plus fastidieuse comme une méthode anonyme ou un délégué générique ou une arborescence d'expression.  En C\#, `=>` est l'opérateur lambda, qui se lit « est redirigé vers ».  Le `num` à gauche de l'opérateur est la variable d'entrée qui correspond à `num` dans l'expression de requête.  Le compilateur peut déduire le type de `num` car il sait que `numbers` est un type <xref:System.Collections.Generic.IEnumerable%601> générique.  Le corps de l'expression lambda est exactement le même que l'expression dans une syntaxe de requête ou dans toute autre expression ou instruction C\# ; il peut inclure des appels de méthode et une autre logique complexe.  La « valeur de retour » est simplement le résultat de l'expression.  
  
 Vous n'avez pas besoin d'utiliser fréquemment les expressions lambda pour commencer à utiliser [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Toutefois, quelques requêtes peuvent être exprimées uniquement en syntaxe de méthode et certaines d'entre elles requièrent des expressions lambda.  Une fois que vous vous êtes familiarisé avec les expressions lambda, vous constaterez qu'elles sont un outil puissant et flexible dans votre boîte à outils [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Pour plus d'informations, consultez [Expressions lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## Composabilité des requêtes  
 Dans l'exemple de code précédent, notez que la méthode `OrderBy` est appelée en utilisant l'opérateur point sur l'appel de `Where`.  `Where` produit une séquence filtrée, puis `Orderby` fonctionne sur cette séquence en la triant.  Étant donné que les requêtes retournent un `IEnumerable`, vous les composez dans la syntaxe de méthode en chaînant les appels de méthode ensemble.  Le compilateur effectue cette opération en arrière\-plan lorsque vous écrivez des requêtes à l'aide de la syntaxe de requête.  Étant donné qu'une variable de requête ne stocke pas les résultats de la requête, vous pouvez la modifier ou l'utiliser à tout moment comme base d'une nouvelle requête, même après son exécution.  
  
## Voir aussi  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)