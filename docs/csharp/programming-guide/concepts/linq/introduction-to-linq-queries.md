---
title: "Introduction to LINQ Queries (C#) | Microsoft Docs"
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
  - "deferred execution [LINQ]"
  - "LINQ, queries"
  - "LINQ, deferred execution"
  - "queries [LINQ], about LINQ queries"
ms.assetid: 37895c02-268c-41d5-be39-f7d936fa88a8
caps.latest.revision: 47
caps.handback.revision: 45
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Introduction to LINQ Queries (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Une *requête* est une expression qui récupère des données d'une source de données.  En général, les requêtes sont exprimées dans un langage de requête spécialisé.  Au fil du temps, différents langages ont été développés pour les divers types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour le XML.  Par conséquent, les développeurs ont dû apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qu'ils doivent prendre en charge.  [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] simplifie cette situation en proposant un modèle cohérent qui permet d'utiliser des données de types de sources et de formats divers.  Dans une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], vous travaillez toujours avec des objets.  Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données en documents XML, en bases de données SQL, en groupes de données [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)], en collections .NET et en tout autre format pour lesquels un fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] est disponible.  
  
## Les trois parties d'une opération de requête  
 Toutes les opérations de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] comportent trois actions distinctes :  
  
1.  Obtenir la source de données.  
  
2.  Créer la requête.  
  
3.  Exécuter la requête.  
  
 L'exemple suivant montre comment les trois parties d'une opération de requête sont exprimées dans le code source.  Il utilise un tableau d'entiers comme source de données pour des raisons pratiques, mais les mêmes concepts sont également applicables à d'autres sources de données.  Cet exemple sert de référence dans le reste de cette rubrique.  
  
 [!code-cs[CsLINQGettingStarted#1](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_1.cs)]  
  
 L'illustration suivante présente la totalité de l'opération de requête.  Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]; l'exécution de la requête est distincte de la requête elle\-même. En d'autres termes, vous n'avez pas récupéré de données en créant simplement une variable de requête.  
  
 ![Opération de requête LINQ complète](../../../../csharp/programming-guide/concepts/linq/media/linq_query.png "LINQ\_Query")  
  
## Source de données  
 Dans l'exemple précédent, étant donné que la source de données est un tableau, elle prend en charge implicitement l'interface <xref:System.Collections.Generic.IEnumerable%601> générique.  Cela signifie qu'elle peut être interrogée avec [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Une requête est exécutée dans une instruction `foreach` et `foreach` requiert <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>.  Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, telle que le <xref:System.Linq.IQueryable%601> générique, sont des *types pouvant faire l'objet d'une requête*.  
  
 Un type requêtable ne nécessite aucune modification ni traitement spécial pour servir de source de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Si les données sources ne sont pas déjà en mémoire comme type requêtable, le fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] doit les représenter comme telles.  Par exemple, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] charge un document XML dans un type <xref:System.Xml.Linq.XElement> requêtable :  
  
 [!code-cs[CsLINQGettingStarted#2](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_2.cs)]  
  
 Avec [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], vous créez tout d'abord un mappage objet\/relationnel au moment du design, soit manuellement, soit à l'aide du [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2).  Vous écrivez vos requêtes sur les objets et [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] gère la communication avec la base de données au moment de l'exécution.  Dans l'exemple suivant, `Customers` représente une table spécifique dans la base de données et le type du résultat de la requête, <xref:System.Linq.IQueryable%601>, dérive de <xref:System.Collections.Generic.IEnumerable%601>.  
  
```c#  
Northwnd db = new Northwnd(@"c:\northwnd.mdf");  
  
// Query for customers in London.  
IQueryable<Customer> custQuery =  
    from cust in db.Customers  
    where cust.City == "London"  
    select cust;  
  
```  
  
 Pour plus d'informations sur la création de types de sources de données spécifiques, consultez la documentation des différents fournisseurs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Toutefois, la règle de base est très simple : une source de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] correspond à tout type d'objet qui prend en charge l'interface <xref:System.Collections.Generic.IEnumerable%601> générique ou une interface qui hérite de celle\-ci.  
  
> [!NOTE]
>  Les types tels que <xref:System.Collections.ArrayList> qui prennent en charge l'interface <xref:System.Collections.IEnumerable> non générique peuvent également être utilisés comme source de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  Pour plus d'informations, consultez [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md).  
  
##  <a name="query"></a> Requête  
 La requête spécifie les informations à récupérer de la source ou des sources de données.  Elle peut également spécifier la manière dont ces informations doivent être triées, regroupées et mises en forme avant d'être retournées.  Une requête est stockée dans une variable de requête et initialisée avec une expression de requête.  C\# a introduit une nouvelle syntaxe de requête pour simplifier l'écriture des requêtes.  
  
 La requête de l'exemple précédent retourne tous les nombres pairs du tableau d'entiers.  L'expression de requête contient trois clauses : `from`, `where` et `select`. \(Si vous êtes familiarisé avec SQL, vous aurez remarqué que l'ordre des clauses est inversé par rapport à l'ordre dans SQL.\) La clause `from` spécifie la source de données, la clause `where` applique le filtre et la clause `select` spécifie le type des éléments retournés.  Ces clauses et d'autres clauses de requête sont abordées en détail dans la section [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md).  Pour le moment, le point majeur est que dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], la variable de requête elle\-même n'exécute aucune action et ne retourne pas de données.  Elle stocke simplement les informations requises pour produire les résultats lors de l'exécution ultérieure de la requête.  Pour plus d'informations sur la construction des requêtes en arrière\-plan, consultez [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
> [!NOTE]
>  Les requêtes peuvent également être exprimées à l'aide de la syntaxe de méthode.  Pour plus d'informations, consultez [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).  
  
## Exécution de requête  
  
### Exécution différée  
 Comme indiqué précédemment, la variable de requête elle\-même stocke simplement les commandes de requête.  L'exécution réelle de la requête est différée jusqu'à ce que vous itériez la variable de requête dans une instruction `foreach`.  Ce concept, connu sous le nom d'*exécution différée*, est illustré dans l'exemple suivant :  
  
 [!code-cs[csLinqGettingStarted#4](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_3.cs)]  
  
 L'instruction `foreach` constitue également l'emplacement où les résultats de la requête sont récupérés.  Par exemple, dans la requête précédente, la variable d'itération `num` contient chaque valeur \(une par une\) de la séquence retournée.  
  
 Étant donné que la variable de requête elle\-même ne contient jamais les résultats de la requête, vous pouvez l'exécuter aussi souvent que vous le souhaitez.  Par exemple, vous pouvez mettre à jour une base de données continuellement à l'aide d'une application séparée.  Dans votre application, vous pouvez créer une requête qui récupère les données les plus récentes et l'exécuter à plusieurs reprises à un intervalle donné pour récupérer des résultats différents à chaque fois.  
  
### Forcer l'exécution immédiate  
 Les requêtes qui exécutent des fonctions d'agrégation sur une plage d'éléments sources doivent d'abord itérer sur ces éléments.  Les requêtes `Count`, `Max`, `Average` et `First` en sont quelques exemples.  Elles s'exécutent sans instruction `foreach` explicite car la requête elle\-même doit utiliser `foreach` pour retourner un résultat.  Notez également que ces types de requêtes retournent une valeur unique et non une collection `IEnumerable`.  La requête suivante retourne un décompte des nombres pairs dans le tableau source :  
  
 [!code-cs[csLinqGettingStarted#5](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_4.cs)]  
  
 Pour forcer l'exécution immédiate de toute requête et mettre ses résultats en cache, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.ToList%2A> ou <xref:System.Linq.Enumerable.ToArray%2A>.  
  
 [!code-cs[csLinqGettingStarted#6](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/introduction-to-linq-queries_5.cs)]  
  
 Vous pouvez également forcer l'exécution en plaçant la boucle `foreach` immédiatement après l'expression de requête.  Toutefois, en appelant `ToList` ou `ToArray`, vous mettez également en cache toutes les données d'un objet de collection unique.  
  
## Voir aussi  
 [Getting Started with LINQ in C\#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Walkthrough: Writing Queries in C\#](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)   
 [Exemples LINQ](../Topic/LINQ%20Samples.md)   
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Expressions de requête \(LINQ\)](../../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [foreach, in](../../../../csharp/language-reference/keywords/foreach-in.md)   
 [Mots clés de requête \(LINQ\)](../../../../csharp/language-reference/keywords/query-keywords.md)   
 [Vidéo sur LINQ et l'exécution différée \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=112414)