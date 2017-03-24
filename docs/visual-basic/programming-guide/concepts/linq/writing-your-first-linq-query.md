---
title: "Écriture de votre première requête LINQ (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
caps.latest.revision: 56
author: stevehoag
ms.author: shoag
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48f1c5e15654580b6e4d060860a0d7001af5e2ef
ms.lasthandoff: 03/13/2017

---
# <a name="writing-your-first-linq-query-visual-basic"></a>Écriture de votre première requête LINQ (Visual Basic)
A *requête* est une expression qui Récupère des données à partir d’une source de données. Les requêtes sont exprimées dans un langage de requête dédié. Au fil du temps, différents langages ont été développés pour les différents types de sources de données, par exemple, SQL pour les bases de données relationnelles et XQuery pour XML. Il est donc nécessaire pour les développeurs d’applications à apprendre un nouveau langage de requête pour chaque type de source de données ou format de données pris en charge.  
  
 [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]simplifie les choses en proposant un modèle cohérent d’utilisation des données, types de sources et de formats divers. Dans un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête, vous travaillez toujours avec des objets. Vous utilisez les mêmes modèles de codage de base pour interroger et transformer des données dans des documents XML, bases de données SQL, datasets ADO.NET et entités, collections .NET Framework et toute autre source ou le format pour lequel un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fournisseur n’est disponible. Ce document décrit les trois phases de la création et l’utilisation de basic [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requêtes.  
  
## <a name="three-stages-of-a-query-operation"></a>Trois étapes d’une opération de requête  
 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)]opérations de requête sont constituées des trois actions suivantes :  
  
1.  Obtenir la source de données ou les sources.  
  
2.  Créer la requête.  
  
3.  Exécutez la requête.  
  
 Dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], l’exécution d’une requête est distincte de la création de la requête. Vous ne récupérez pas des données en créant une requête uniquement. Ce point est abordé plus en détail plus loin dans cette rubrique.  
  
 L’exemple suivant illustre les trois parties d’une opération de requête. L’exemple utilise un tableau d’entiers en tant que source de données à des fins de démonstration. Toutefois, les mêmes concepts s’appliquent également à d’autres sources de données.  
  
> [!NOTE]
>  Sur le [Page Compiler, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic), assurez-vous que **Option infer** a **sur**.  
  
 [!code-vb[VbLINQFirstQuery n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 Sortie :  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>La Source de données  
 La source de données dans l’exemple précédent est un tableau, elle prend en charge implicitement générique <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601> C’est ce fait qui vous permet d’utiliser un tableau comme source de données pour un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête. Les types qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601>ou une interface dérivée comme générique <xref:System.Linq.IQueryable%601>sont appelés *types requêtables*.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Comme un type implicitement requêtable, le tableau ne nécessite aucune modification ni traitement spécial pour servir une [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] source de données. Cela vaut pour tout type de collection qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>, y compris le générique <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>et d’autres classes dans la bibliothèque de classes .NET Framework.</xref:System.Collections.Generic.Dictionary%602> </xref:System.Collections.Generic.List%601> </xref:System.Collections.Generic.IEnumerable%601>  
  
 Si la source de données n’implémente pas déjà <xref:System.Collections.Generic.IEnumerable%601>, un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fournisseur est nécessaire pour implémenter les fonctionnalités de la *opérateurs de requête standard* pour cette source de données.</xref:System.Collections.Generic.IEnumerable%601> Par exemple, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] gère le travail de chargement d’un document XML dans un requêtable <xref:System.Xml.Linq.XElement>type, comme illustré dans l’exemple suivant.</xref:System.Xml.Linq.XElement> Pour plus d’informations sur les opérateurs de requête standard, consultez [vue d’ensemble Standard des opérateurs de requête (Visual Basic)](standard-query-operators-overview.md).  
  
 [!code-vb[VbLINQFirstQuery n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_2.vb)]  
  
 Avec [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], vous créez tout d’abord un mappage objet-relationnel au moment du design, soit manuellement, soit en utilisant la [LINQ to SQL Tools dans Visual Studio](https://docs.microsoft.com/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2) dans Visual Studio. Vous écrivez vos requêtes sur les objets et au moment de l’exécution [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] gère la communication avec la base de données. Dans l’exemple suivant, `customers` représente une table spécifique dans la base de données et <xref:System.Data.Linq.Table%601>prend en charge les génériques <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Data.Linq.Table%601>  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 Pour plus d’informations sur la création des types de sources de données spécifiques, consultez la documentation pour les divers [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] fournisseurs. (Pour obtenir la liste de ces fournisseurs, consultez [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).) La règle de base est simple : un [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] source de données est un objet qui prend en charge l' <xref:System.Collections.Generic.IEnumerable%601>interface, ou une interface qui hérite de celui-ci.</xref:System.Collections.Generic.IEnumerable%601>  
  
> [!NOTE]
>  Les types tels que <xref:System.Collections.ArrayList>qui prennent en charge non générique <xref:System.Collections.IEnumerable>interface peut également être utilisée en tant que [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] des sources de données.</xref:System.Collections.IEnumerable> </xref:System.Collections.ArrayList> Pour obtenir un exemple qui utilise un <xref:System.Collections.ArrayList>, consultez [Comment : interroger un ArrayList avec LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md).</xref:System.Collections.ArrayList>  
  
## <a name="the-query"></a>La requête  
 Dans la requête, vous spécifiez les informations que vous souhaitez récupérer à partir de la source de données ou les sources. Vous avez également la possibilité de spécifier comment ces informations doivent être triées, regroupées ou structurées avant d’être retournée. Pour activer la création de la requête, Visual Basic a incorporé la nouvelle syntaxe de requête dans la langue.  
  
 Lorsqu’elle est exécutée, la requête dans l’exemple suivant retourne tous les nombres pairs d’un tableau d’entiers, `numbers`.  
  
 [!code-vb[VbLINQFirstQuery n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_1.vb)]  
  
 L’expression de requête contient trois clauses : `From`, `Where`, et `Select`. La fonction spécifique et l’objectif de chaque clause d’expression de requête est indiqué dans [base des opérations de requête (Visual Basic)](basic-query-operations.md). Pour plus d’informations, consultez [requêtes](../../../../visual-basic/language-reference/queries/queries.md). Notez que dans [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)], une définition de requête est souvent stockée dans une variable et exécutée ultérieurement. La requête variable, telles que `evensQuery` dans l’exemple précédent, doit être un type requêtable. Le type de `evensQuery` est `IEnumerable(Of Integer)`, attribué par le compilateur à l’aide de l’inférence de type local.  
  
 Il est important de se rappeler que la variable de requête elle-même n’effectue aucune action et ne retourne aucune donnée. Elle stocke uniquement la définition de requête. Dans l’exemple précédent, il s’agit du `For Each` boucle qui exécute la requête.  
  
## <a name="query-execution"></a>Exécution de la requête  
 Exécution de la requête est distincte de la création de la requête. Création de requête définit la requête, mais l’exécution est déclenchée par un mécanisme différent. Une requête peut être exécutée dès qu’elle est définie (*l’exécution immédiate*), ou la définition peut être stockée et la requête peut être exécutée ultérieurement (*exécution différée*).  
  
### <a name="deferred-execution"></a>Exécution différée  
 Par défaut [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] requête ressemble à celui de l’exemple précédent, dans lequel `evensQuery` est défini. Il crée la requête mais sans l’exécuter immédiatement. En revanche, la définition de requête est stockée dans la variable de requête `evensQuery`. Vous exécutez la requête ultérieurement, généralement en utilisant un `For Each` boucle, qui retourne une séquence de valeurs ou en appliquant un opérateur de requête standard, tels que `Count` ou `Max`. Ce processus est appelé *exécution différée*.  
  
 [!code-vb[VbLINQFirstQuery&#7;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_3.vb)]  
  
 Pour une séquence de valeurs, vous accédez aux données récupérées à l’aide de la variable d’itération dans le `For Each` boucle (`number` dans l’exemple précédent). Étant donné que la variable de requête, `evensQuery`, conserve la définition de requête plutôt que les résultats de la requête, vous pouvez exécuter une requête aussi souvent que vous le souhaitez à l’aide de la variable de requête plusieurs fois. Par exemple, vous pouvez avoir une base de données dans votre application est en cours de mise à jour en permanence par une application distincte. Après avoir créé une requête qui Récupère des données à partir de cette base de données, vous pouvez utiliser un `For Each` boucle pour exécuter la requête à plusieurs reprises, en récupérant les données les plus récentes à chaque fois.  
  
 L’exemple suivant montre comment l’exécution fonctionne. Après avoir `evensQuery2` est définie et exécutée avec un `For Each` en boucle, comme dans les exemples précédents, certains éléments de la source de données `numbers` sont modifiés. Ensuite, une deuxième `For Each` s’exécute en boucle `evensQuery2` à nouveau. Les résultats sont différents la deuxième fois, étant donné que la `For Each` boucle s’exécute la requête, en utilisant les nouvelles valeurs dans `numbers`.  
  
 [!code-vb[VbLINQFirstQuery n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_4.vb)]  
  
 Sortie :  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>Exécution immédiate  
 Dans l’exécution différée des requêtes, la définition de requête est stockée dans une variable de requête pour une exécution ultérieure. Dans l’exécution immédiate, la requête est exécutée au moment de sa définition. L’exécution est déclenchée lorsque vous appliquez une méthode qui requiert l’accès aux éléments individuels du résultat de requête. Fréquence à laquelle l’exécution immédiate est forcée à l’aide d’un des opérateurs de requête standard qui retournent des valeurs uniques. Examples are `Count`, `Max`, `Average`, and `First`. Ces opérateurs de requête standard, exécutez la requête dès qu’elles sont appliquées pour calculer et retourner un résultat singleton. Pour plus d’informations sur les opérateurs de requête standard qui retournent des valeurs uniques, consultez [opérations d’agrégation](aggregation-operations.md), [opérations d’élément](element-operations.md), et [opérations de quantificateur](quantifier-operations.md).  
  
 La requête suivante renvoie un nombre de chiffres pairs dans un tableau d’entiers. La définition de requête n’est pas enregistrée et `numEvens` est un simple `Integer`.  
  
 [!code-vb[VbLINQFirstQuery n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_5.vb)]  
  
 Vous pouvez obtenir le même résultat à l’aide de la `Aggregate` méthode.  
  
 [!code-vb[VbLINQFirstQuery n °&5;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_6.vb)]  
  
 Vous pouvez également forcer l’exécution d’une requête en appelant le `ToList` ou `ToArray` sur une requête (immédiate) ou la variable de requête (différé), comme illustré dans le code suivant.  
  
 [!code-vb[VbLINQFirstQuery n °&6;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/writing-your-first-linq-query_7.vb)]  
  
 Dans les exemples précédents, `evensQuery3` est une requête, mais `evensList` est une liste et `evensArray` est un tableau.  
  
 À l’aide de `ToList` ou `ToArray` pour forcer immédiatement l’exécution est particulièrement utile dans les scénarios dans lesquels vous souhaitez exécuter immédiatement la requête et mettre en cache les résultats dans un objet de collection unique. Pour plus d’informations sur ces méthodes, consultez [convertir les Types de données](converting-data-types.md).  
  
 Vous pouvez également provoquer une requête doit être exécutée à l’aide un `IEnumerable` méthode telle que la <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>(méthode).</xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en route de LINQ en Visual Basic](getting-started-with-linq.md)   
 [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md)   
 [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)   
 [Requêtes](../../../../visual-basic/language-reference/queries/queries.md)
