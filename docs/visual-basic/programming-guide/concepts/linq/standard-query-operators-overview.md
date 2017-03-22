---
title: "Vue d’ensemble des opérateurs de requête standard (Visual Basic) | Documents Microsoft"
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
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: eb28988ef49e0583fb7e9197c4e13c84665074ac
ms.lasthandoff: 03/13/2017

---
# <a name="standard-query-operators-overview-visual-basic"></a>Vue d’ensemble des opérateurs de requête standard (Visual Basic)
Le *opérateurs de requête standard* sont les méthodes qui forment le modèle LINQ. La plupart de ces méthodes fonctionnent sur des séquences, une séquence étant un objet dont le type implémente le <xref:System.Collections.Generic.IEnumerable%601>interface ou <xref:System.Linq.IQueryable%601>interface.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> Les opérateurs de requête standard fournissent des fonctions de requête, notamment le filtrage, la projection, l’agrégation, le tri et bien plus encore.  
  
 Il existe deux ensembles d’opérateurs de requête standard LINQ qui opère sur des objets de type <xref:System.Collections.Generic.IEnumerable%601>et l’autre qui opère sur des objets de type <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> Les méthodes qui composent chaque ensemble sont des membres statiques de la <xref:System.Linq.Enumerable>et <xref:System.Linq.Queryable>des classes, respectivement.</xref:System.Linq.Queryable> </xref:System.Linq.Enumerable> Ils sont définis en tant que *les méthodes d’extension* du type lequel elles fonctionnent. Cela signifie qu’elles peuvent être appelées à l’aide de la syntaxe de méthode statique ou de syntaxe de méthode d’instance.  
  
 En outre, plusieurs méthodes d’opérateur de requête standard opèrent sur des types autres que ceux basés sur <xref:System.Collections.Generic.IEnumerable%601>ou <xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601> </xref:System.Collections.Generic.IEnumerable%601> Le <xref:System.Linq.Enumerable>type définit deux méthodes telles que les deux fonctionnent sur les objets de type <xref:System.Collections.IEnumerable>.</xref:System.Collections.IEnumerable> </xref:System.Linq.Enumerable> Ces méthodes, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29>et <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, laissez vous activez une collection non paramétrée, ou non générique, à interroger dans le modèle LINQ.</xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29> </xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> Ils cela en créant une collection fortement typée d’objets. La <xref:System.Linq.Queryable>classe définit deux méthodes similaires <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29>et <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, qui opèrent sur des objets de type <xref:System.Linq.Queryable>.</xref:System.Linq.Queryable> </xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> </xref:System.Linq.Queryable>  
  
 Les opérateurs de requête standard diffèrent dans le déroulement de leur exécution, selon qu’ils retournent une valeur singleton ou une séquence de valeurs. Les méthodes qui retournent une valeur singleton (par exemple, <xref:System.Linq.Enumerable.Average%2A>et <xref:System.Linq.Enumerable.Sum%2A>) s’exécutent immédiatement.</xref:System.Linq.Enumerable.Sum%2A> </xref:System.Linq.Enumerable.Average%2A> Les méthodes qui retournent une séquence de différer l’exécution de la requête et retournent un objet énumérable.  
  
 Dans le cas des méthodes qui fonctionnent sur les collections en mémoire, autrement dit, les méthodes qui étendent <xref:System.Collections.Generic.IEnumerable%601>, l’objet énumérable retourné capture les arguments passés à la méthode.</xref:System.Collections.Generic.IEnumerable%601> Lorsque cet objet est énuméré, la logique de l’opérateur de requête est employée et les résultats de requête sont retournés.  
  
 En revanche, les méthodes qui étendent <xref:System.Linq.IQueryable%601>n’implémentent pas aucun comportement d’interrogation, mais créer une arborescence d’expression qui représente la requête à exécuter.</xref:System.Linq.IQueryable%601> Le traitement de requête est contrôlé par la source de <xref:System.Linq.IQueryable%601>objet.</xref:System.Linq.IQueryable%601>  
  
 Les appels aux méthodes de requête peuvent être chaînés ensemble dans une seule requête, ce qui permet aux requêtes de devenir arbitrairement complexes.  
  
 L’exemple de code suivant illustre l’utilisation des opérateurs de requête standard pour obtenir des informations sur une séquence.  
  
```vb  
Dim sentence = "the quick brown fox jumps over the lazy dog"  
' Split the string into individual words to create a collection.  
Dim words = sentence.Split(" "c)  
  
Dim query = From word In words   
            Group word.ToUpper() By word.Length Into gr = Group   
            Order By Length _  
            Select Length, GroupedWords = gr  
  
Dim output As New System.Text.StringBuilder  
For Each obj In query  
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))  
    For Each word As String In obj.GroupedWords  
        output.AppendLine(word)  
    Next  
Next  
  
'Display the output  
MsgBox(output.ToString())  
  
' This code example produces the following output:  
'  
' Words of length 3:  
' THE  
' FOX  
' THE  
' DOG  
' Words of length 4:  
' OVER  
' LAZY  
' Words of length 5:  
' QUICK  
' BROWN  
' JUMPS   
```  
  
## <a name="query-expression-syntax"></a>Syntaxe d'expression de requête  
 Certains des opérateurs de requête standard plus fréquemment utilisées sont dédiées à c# et Visual Basic syntaxe de mot clé de langage qui leur permet d’être appelée dans le cadre d’un *requête* *expression*. Pour plus d’informations sur les opérateurs de requête standard qui sont dédiées des mots clés et leurs syntaxes correspondantes, consultez [syntaxe d’Expression de requête pour les opérateurs de requête Standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md).  
  
## <a name="extending-the-standard-query-operators"></a>Extension des opérateurs de requête Standard  
 Vous pouvez augmenter l’ensemble des opérateurs de requête standard en création méthodes spécifiques au domaine qui sont appropriés pour votre domaine ou technologie cible. Vous pouvez également remplacer les opérateurs de requête standard par vos propres implémentations qui fournissent des services supplémentaires tels que l’évaluation à distance, traduction de requête et l’optimisation. Consultez <xref:System.Linq.Enumerable.AsEnumerable%2A>pour obtenir un exemple.</xref:System.Linq.Enumerable.AsEnumerable%2A>  
  
## <a name="related-sections"></a>Rubriques connexes  
 Les liens suivants vous renvoient vers des rubriques qui fournissent des informations supplémentaires sur les divers opérateurs de requête standard basée sur la fonctionnalité.  
  
 [Tri des données](../../../../visual-basic/programming-guide/concepts/linq/sorting-data.md)  
  
 [Opérations ensemblistes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/set-operations.md)  
  
 [Filtrage des données (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/filtering-data.md)  
  
 [Opérations de quantificateur (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/quantifier-operations.md)  
  
 [Opérations de projection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)  
  
 [Partitionnement des données (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/partitioning-data.md)  
  
 [Joindre des opérations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md)  
  
 [Regroupement de données (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/grouping-data.md)  
  
 [Opérations de génération (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/generation-operations.md)  
  
 [Opérations d’égalité (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/equality-operations.md)  
  
 [Opérations d’élément (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/element-operations.md)  
  
 [Conversion des Types de données (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)  
  
 [Opérations de concaténation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concatenation-operations.md)  
  
 [Opérations d’agrégation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq.Enumerable></xref:System.Linq.Enumerable>   
 <xref:System.Linq.Queryable></xref:System.Linq.Queryable>   
 [Introduction à LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)   
 [Syntaxe d’Expression de requête pour les opérateurs de requête Standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/query-expression-syntax-for-standard-query-operators.md)   
 [Classification des opérateurs de requête Standard en mode d’exécution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/classification-of-standard-query-operators-by-manner-of-execution.md)   
 [Méthodes d’extension](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
