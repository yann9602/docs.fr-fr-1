---
title: "Écriture de votre première requête LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: "56"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c16bb28189d5525654328da2dc80d868bbe61bf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-your-first-linq-query-visual-basic"></a>Écriture de votre première requête LINQ (Visual Basic)
Une *requête* est une expression qui récupère des données d’une source de données. Les requêtes sont exprimées dans un langage de requête dédié. Au fil du temps, différents langages ont été développés pour différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Il est donc nécessaire pour le développeur d’applications à apprendre un nouveau langage de requête pour chaque type de source de données ou format de données qui est pris en charge.  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]simplifie la situation en proposant un modèle cohérent pour travailler avec des données entre les différents types de sources de données et les formats. Dans une requête [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, bases de données SQL, groupes de données ADO.NET et entités, les collections du .NET Framework et n’importe quel autre source ou le format pour lequel un [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fournisseur n’est disponible. Ce document décrit les trois phases de la création et l’utilisation de base [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requêtes.  
  
## <a name="three-stages-of-a-query-operation"></a>Trois phases d’une opération de requête  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]opérations de requête se composent de trois actions :  
  
1.  Obtenir la source de données ou les sources.  
  
2.  Création de la requête  
  
3.  Exécution de la requête  
  
 Dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], l’exécution d’une requête est distincte de la création de la requête. Vous ne récupérez pas toutes les données en créant une requête uniquement. Ce point est abordé en détail plus loin dans cette rubrique.  
  
 L’exemple suivant illustre les trois parties d’une opération de requête. L’exemple utilise un tableau d’entiers en tant que source de données à des fins de démonstration. Toutefois, les mêmes concepts s’appliquent également à d’autres sources de données.  
  
> [!NOTE]
>  Sur le [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), vérifiez que **Option infer** a la valeur **sur**.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Sortie :  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>Source de données  
 La source de données dans l’exemple précédent est un tableau, il prend en charge implicitement générique <xref:System.Collections.Generic.IEnumerable%601> interface. Il est fait qui vous permet d’utiliser un tableau en tant que source de données pour un [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601> ou une interface dérivée, comme l’interface générique <xref:System.Linq.IQueryable%601>, sont appelés des *types requêtables*.  
  
 Comme un type implicitement requêtable, le tableau ne nécessite aucune modification ni traitement spécial pour servir une [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] source de données. Cela vaut pour tout type de collection qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>, y compris le générique <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>et d’autres classes dans la bibliothèque de classes .NET Framework.  
  
 Si la source de données n’implémente pas déjà <xref:System.Collections.Generic.IEnumerable%601>, un [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] fournisseur est nécessaire pour implémenter les fonctionnalités de la *opérateurs de requête standard* pour cette source de données. Par exemple, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] gère les tâches de chargement d’un document XML dans un requêtable <xref:System.Xml.Linq.XElement> de type, comme illustré dans l’exemple suivant. Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble Standard des opérateurs de requête (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Avec [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], vous créez tout d’abord un mappage objet / relationnel au moment du design, manuellement ou à l’aide de la [LINQ to SQL Tools dans Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) dans Visual Studio. Vous écrivez vos requêtes pour des objets. Ensuite, au moment de l’exécution, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `customers` représente une table spécifique dans la base de données, et <xref:System.Data.Linq.Table%601> prend en charge générique <xref:System.Linq.IQueryable%601>.  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 Pour plus d’informations sur la création de types de sources de données spécifiques, consultez la documentation relative aux différents fournisseurs [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. (Pour obtenir la liste de ces fournisseurs, consultez [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) La règle de base est simple : une [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] source de données est un objet qui prend en charge le type générique <xref:System.Collections.Generic.IEnumerable%601> interface ou une interface qui hérite de celle-ci.  
  
> [!NOTE]
>  Types tels que <xref:System.Collections.ArrayList> qui prennent en charge non générique <xref:System.Collections.IEnumerable> interface peut également être utilisée en tant que [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] des sources de données. Pour obtenir un exemple qui utilise un <xref:System.Collections.ArrayList>, consultez [Comment : interroger un ArrayList avec LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).  
  
## <a name="the-query"></a>La requête  
 Dans la requête, vous spécifiez les informations que vous souhaitez récupérer à partir de la source de données ou les sources. Vous avez également la possibilité de spécifier comment ces informations doivent être triées, regroupées ou structurées avant d’être retournée. Pour activer la création de la requête, Visual Basic a incorporé la nouvelle syntaxe de requête dans la langue.  
  
 Lorsqu’elle est exécutée, la requête dans l’exemple suivant retourne tous les nombres pairs à partir d’un tableau d’entiers, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 L’expression de requête contient trois clauses : `From`, `Where`, et `Select`. La fonction spécifique et l’objet de chaque clause d’expression de requête est décrite dans [base des opérations de requête (Visual Basic)](basic-query-operations.md). Pour plus d’informations, consultez [requêtes](../../../../visual-basic/language-reference/queries/queries.md). Notez que dans [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], une définition de requête est souvent stockée dans une variable et exécutée ultérieurement. La requête variable, telles que `evensQuery` dans l’exemple précédent, doivent être de type requêtable. Le type de `evensQuery` est `IEnumerable(Of Integer)`, attribué par le compilateur à l’aide de l’inférence de type local.  
  
 Il est important de se rappeler que la variable de requête elle-même n’effectue aucune action et ne retourne aucune donnée. Elle stocke uniquement la définition de requête. Dans l’exemple précédent, il s’agit du `For Each` boucle qui exécute la requête.  
  
## <a name="query-execution"></a>Exécution de la requête  
 Exécution de la requête est distincte de la création de la requête. Création de la requête définit la requête, mais l’exécution est déclenchée par un mécanisme différent. Une requête peut être exécutée dès qu’il est défini (*l’exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
### <a name="deferred-execution"></a>Exécution différée  
 Par défaut [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] requête ressemble à celui de l’exemple précédent, dans lequel `evensQuery` est défini. Il crée la requête, mais sans l’exécuter immédiatement. Au lieu de cela, la définition de la requête est stockée dans la variable de requête `evensQuery`. Vous exécutez la requête ultérieurement, généralement en utilisant un `For Each` boucle, qui retourne une séquence de valeurs, ou en appliquant un opérateur de requête standard, tels que `Count` ou `Max`. Ce processus est appelé *exécution différée*.  
  
 [!code-vb[VbLINQFirstQuery#7](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Pour une séquence de valeurs, vous accédez aux données récupérées à l’aide de la variable d’itération dans le `For Each` boucle (`number` dans l’exemple précédent). Étant donné que la variable de requête, `evensQuery`, conserve la définition de requête, plutôt que les résultats de requête, vous pouvez exécuter une requête aussi souvent que vous le souhaitez à l’aide de la variable de requête plusieurs fois. Par exemple, vous pouvez avoir une base de données dans votre application est en cours de mise à jour en permanence par une application distincte. Après avoir créé une requête qui Récupère des données à partir de cette base de données, vous pouvez utiliser un `For Each` boucle pour exécuter la requête à plusieurs reprises, en récupérant les données les plus récentes à chaque fois.  
  
 L’exemple suivant montre comment l’exécution fonctionne. Après avoir `evensQuery2` est définie et exécutée avec un `For Each` de boucle, comme dans les exemples précédents, certains éléments dans la source de données `numbers` sont modifiés. Ensuite, une deuxième `For Each` s’exécute en boucle `evensQuery2` à nouveau. Les résultats sont différents la deuxième fois, étant donné que la `For Each` la boucle s’exécute la requête à nouveau, avec les nouvelles valeurs dans `numbers`.  
  
 [!code-vb[VbLINQFirstQuery#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Sortie :  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Exécution immédiate  
 Dans l’exécution différée des requêtes, la définition de requête est stockée dans une variable de requête pour une exécution ultérieure. Dans l’exécution immédiate, la requête est exécutée au moment de sa définition. L’exécution est déclenchée lorsque vous appliquez une méthode qui requiert l’accès aux éléments individuels du résultat de requête. Fréquence à laquelle l’exécution immédiate est forcée à l’aide d’un des opérateurs de requête standard qui retournent des valeurs uniques. Exemples `Count`, `Max`, `Average`, et `First`. Ces opérateurs de requête standard exécutent la requête dès qu’ils sont appliqués pour calculer et retourner un résultat de singleton. Pour plus d’informations sur les opérateurs de requête standard qui retournent des valeurs uniques, consultez [opérations d’agrégation](aggregation-operations.md), [opérations d’élément](element-operations.md), et [opérations de quantificateur](quantifier-operations.md).  
  
 La requête suivante retourne un décompte des nombres pairs dans un tableau d’entiers. La définition de requête n’est pas enregistrée, et `numEvens` est un simple `Integer`.  
  
 [!code-vb[VbLINQFirstQuery#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Vous pouvez obtenir le même résultat à l’aide de la `Aggregate` (méthode).  
  
 [!code-vb[VbLINQFirstQuery#5](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Vous pouvez également forcer l’exécution d’une requête en appelant le `ToList` ou `ToArray` méthode sur une requête (immédiate) ou d’une variable de requête (différé), comme indiqué dans le code suivant.  
  
 [!code-vb[VbLINQFirstQuery#6](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Dans les exemples précédents, `evensQuery3` est une requête, mais `evensList` est une liste et `evensArray` est un tableau.  
  
 À l’aide de `ToList` ou `ToArray` pour forcer immédiatement l’exécution est particulièrement utile dans les scénarios dans lesquels vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats dans un objet de collection unique. Pour plus d’informations sur ces méthodes, consultez [conversion des Types de données](converting-data-types.md).  
  
 Vous pouvez également provoquer une requête doit être exécutée à l’aide d’un `IEnumerable` méthode telle que la <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer avec LINQ en Visual Basic](getting-started-with-linq.md)  
 [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)  
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)
