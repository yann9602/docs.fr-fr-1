---
title: "&#201;criture de votre premi&#232;re requ&#234;te LINQ (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "requêtes [LINQ en Visual Basic], écrire"
  - "requêtes LINQ [Visual Basic]"
  - "LINQ [Visual Basic], écrire des requêtes"
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 54
---
# &#201;criture de votre premi&#232;re requ&#234;te LINQ (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Une *requête* est une expression qui récupère des données d'une source de données.  Les requêtes sont exprimées dans un langage de requête dédié.  Au fil du temps, différents langages ont été développés pour les différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour le XML.  Les développeurs d'applications doivent donc apprendre un nouveau langage de requête pour chaque type de source de données ou de format de données pris en charge.  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext-md.md)] simplifie les choses en proposant un modèle cohérent qui permet d'utiliser des données de types de sources et de formats divers.  Dans une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], vous travaillez toujours avec des objets.  Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, des bases de données SQL, des groupes de données et des entités ADO.NET, des collections .NET Framework et les autres sources ou formats pour lesquels un fournisseur [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] est disponible.  Ce document décrit les trois phases de création et d'utilisation de requêtes [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] de base.  
  
 ![lien vers la vidéo](../../../../csharp/programming-guide/concepts/linq/media/playvideo.png "PlayVideo") Pour une démonstration vidéo connexe, consultez [Comment faire pour démarrer avec LINQ ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=133021).  
  
## Trois étapes d'une opération de requête  
 Les opérations de requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] incluent trois opérations :  
  
1.  Obtenir la source ou les sources de données.  
  
2.  Créer la requête.  
  
3.  Exécuter la requête.  
  
 Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], l'exécution d'une requête est distincte de la création de la requête.  Vous ne récupérez aucune donnée en créant uniquement une requête.  Ce point est abordé plus en détail ultérieurement dans cette rubrique.  
  
 L'exemple suivant présente les trois parties d'une opération de requête.  Un tableau d'entiers est utilisé comme source de données, à des fins de démonstration.  Toutefois, ces concepts s'appliquent également à d'autres sources de données.  
  
> [!NOTE]
>  Dans [Page Compiler, Concepteur de projets \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic), assurez\-vous que **L'option déduisent** a la valeur **Dans**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Sortie :  
  
 `0 2 4 6`  
  
## Source de données  
 La source de données de l'exemple précédent étant un tableau, elle prend en charge implicitement l'interface <xref:System.Collections.Generic.IEnumerable%601> générique.  Cela vous permet d'utiliser un tableau comme source de données pour une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée telle qu' <xref:System.Linq.IQueryable%601> générique sont *des types pouvant être interrogés*.  
  
 En tant que type implicitement requêtable, le tableau ne nécessite aucune modification ni traitement spécial pour servir de source de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Il en va de même pour tout type de collection prenant en charge <xref:System.Collections.Generic.IEnumerable%601>, y compris <xref:System.Collections.Generic.List%601>générique, <xref:System.Collections.Generic.Dictionary%602>, et d'autres classes de la bibliothèque de classes.NET Framework.  
  
 Si les données sources n'implémentent pas déjà <xref:System.Collections.Generic.IEnumerable%601>, un fournisseur d' [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] est nécessaire pour implémenter les fonctionnalités *des opérateurs de requête standard* pour cette source de données.  Par exemple, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq-md.md)] gère le chargement d'un document XML dans un type <xref:System.Xml.Linq.XElement> requêtable, comme présenté dans l'exemple suivant.  Pour plus d'informations sur les opérateurs de requête standard, consultez [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Avec [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)], vous créez tout d'abord un mappage objet\/relationnel au moment du design, soit manuellement, soit à l'aide du [Concepteur Objet\/Relationnel \(Concepteur O\/R\)](/visual-studio/data-tools/linq-to-sql-tools-in-visual-studio2).  Vous écrivez vos requêtes sur les objets et [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq-md.md)] gère la communication avec la base de données au moment de l'exécution.  Dans l'exemple suivant, `customers` représente une table spécifique dans la base de données et <xref:System.Data.Linq.Table%601> prend en charge le <xref:System.Linq.IQueryable%601> générique.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Pour plus d'informations sur la création de types de sources de données spécifiques, consultez la documentation des différents fournisseurs [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Pour obtenir la liste de ces fournisseurs, consultez [LINQ \(Language\-Integrated Query\)](../Topic/LINQ%20\(Language-Integrated%20Query\).md). La règle de base est simple : une source de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] correspond à tout type d'objet qui prend en charge l'interface <xref:System.Collections.Generic.IEnumerable%601> générique ou une interface qui hérite de celle\-ci.  
  
> [!NOTE]
>  Les types tels que <xref:System.Collections.ArrayList> qui prennent en charge l'interface <xref:System.Collections.IEnumerable> non générique peuvent également être utilisés comme sources de données [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)].  Pour obtenir un exemple qui utilise un <xref:System.Collections.ArrayList>, consultez [How to: Query an ArrayList with LINQ](../Topic/How%20to:%20Query%20an%20ArrayList%20with%20LINQ.md).  
  
## Requête  
 Dans la requête, vous spécifiez les informations à récupérer de la source ou des sources de données.  Vous pouvez également spécifier comment ces informations doivent être triées, regroupées ou structurées avant d'être retournées.  Pour permettre la création de requêtes, Visual Basic a incorporé une nouvelle syntaxe de requête dans le langage.  
  
 Lorsqu'elle est exécutée, la requête de l'exemple suivant retourne tous les nombres pairs d'un tableau d'entiers, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 L'expression de requête contient trois clauses : `From`, `Where` et `Select`.  La fonction et le but spécifiques de chaque clause d'expression de requête sont expliqués dans [Opérations de requête de base \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  Pour plus d'informations, consultez [Queries](../../../../visual-basic/language-reference/queries/queries.md).  Notez que dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)], une définition de requête est souvent stockée dans une variable et exécutée ultérieurement.  La variable de requête, telle qu' `evensQuery` dans l'exemple précédent, doit être un type requêtable. Le type d' `evensQuery` est `IEnumerable(Of Integer)`, assigné par le compilateur à l'aide de l'inférence de type locale.  
  
 Rappelez\-vous que la variable de requête elle\-même n'effectue aucune action et ne retourne pas de données.  Elle stocke seulement la définition de la requête.  Dans l'exemple précédent, c'est la boucle `For Each` qui exécute la requête.  
  
## Exécution de requête  
 L'exécution de requête est distincte de la création de requête.  La création de requête définit la requête mais l'exécution est déclenchée par un mécanisme différent.  Une requête peut être exécutée dès qu'elle est définie \(*exécution immédiate*\) ou la définition peut être stockée et la requête peut être exécutée ultérieurement \(*exécution différée*\).  
  
### Exécution différée  
 Une requête [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq-md.md)] type est semblable à celle de l'exemple précédent, dans lequel `evensQuery` est défini.  La requête est créée mais n'est pas exécutée immédiatement.  À la place, la définition de la requête est stockée dans la requête de variable `evensQuery`.  Vous exécutez la requête ultérieurement, en général à l'aide d'une boucle `For Each` qui retourne une séquence de valeurs ou en appliquant un opérateur de requête standard tel que `Count` ou `Max`.  Ce processus est connu sous le nom d'*exécution différée*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Pour une séquence de valeurs, vous accédez aux données récupérées à l'aide de la variable d'itération dans la boucle `For Each` \(`number` dans l'exemple précédent\).  Comme la variable de requête, `evensQuery`, conserve la définition de la requête plutôt que les résultats, vous pouvez exécuter une requête aussi souvent que vous le souhaitez en utilisant la variable de requête plusieurs fois.  Par exemple, vous pouvez avoir une base de données dans votre application mise à jour continuellement par une application séparée.  Après avoir créé une requête qui récupère des données de cette base de données, vous pouvez utiliser une boucle `For Each` pour exécuter la requête à plusieurs reprises, en récupérant à chaque fois les données les plus récentes.  
  
 L'exemple suivant présente le fonctionnement de l'exécution différée.  Une fois que vous avez défini et exécuté `evensQuery2` avec une boucle `For Each`, comme dans les exemples précédents, certains éléments de la source de données `numbers` sont modifiés.  Ensuite, une deuxième boucle `For Each` exécute encore `evensQuery2`.  Les résultats sont différents la deuxième fois car la boucle `For Each` exécute encore la requête, à l'aide des nouvelles valeurs dans `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Sortie :  
  
 `Evens in original array:`  
  
 `0 2 4 6`  
  
 `Evens in changed array:`  
  
 `0 10 2 22 8`  
  
### Exécution immédiate  
 Dans l'exécution différée de requêtes, la définition de la requête est stockée dans une variable de requête en vue d'une exécution ultérieure.  Dans l'exécution immédiate, la requête est exécutée au moment de sa définition.  L'exécution est déclenchée lorsque vous appliquez une méthode qui requiert l'accès aux éléments individuels du résultat de la requête.  L'exécution immédiate est souvent forcée à l'aide de l'un des opérateurs de requête standard qui retournent des valeurs uniques.  `Count`, `Max`, `Average` et `First` en sont quelques exemples.  Ces opérateurs de requête standard exécutent la requête dès leur application pour calculer et retourner un résultat singleton.  Pour plus d'informations sur les opérateurs de requête standard qui retournent des valeurs uniques, consultez [Aggregation Operations](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md), [Element Operations](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md) et [Quantifier Operations](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md).  
  
 La requête suivante retourne un décompte des nombres pairs dans un tableau d'entiers.  La définition de la requête n'est pas enregistrée et `numEvens` est un `Integer` simple.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Vous pouvez obtenir le même résultat à l'aide de la méthode `Aggregate`.  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Vous pouvez également forcer l'exécution d'une requête en appelant la méthode `ToList` ou `ToArray` sur une requête \(exécution immédiate\) ou sur une variable de requête \(exécution différée\), comme présenté dans le code suivant.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Dans les exemples précédents, `evensQuery3` est une variable de requête, mais `evensList` est une liste et `evensArray` un tableau.  
  
 L'utilisation de `ToList` ou de `ToArray` pour forcer l'exécution immédiate est particulièrement utile lorsque vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats dans un objet de collection singleton.  Pour plus d'informations sur ces méthodes, consultez [Converting Data Types](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).  
  
 Vous pouvez également exécuter une requête en utilisant une méthode `IEnumerable` telle que la méthode <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>.  
  
## Démonstrations vidéo connexes  
 [Comment faire pour démarrer avec LINQ ? \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkId=133021)  
  
 [Vidéo : Comment écrire des requêtes en Visual Basic \(page éventuellement en anglais\)](http://go.microsoft.com/fwlink/?LinkID=100356)  
  
## Voir aussi  
 [Getting Started with LINQ in Visual Basic](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Exemples LINQ](../Topic/LINQ%20Samples.md)   
 [Vue d'ensemble du Concepteur O\/R](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Standard Query Operators Overview](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Queries](../../../../visual-basic/language-reference/queries/queries.md)