---
title: "Définir des opérations (Visual Basic) | Documents Microsoft"
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
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
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
ms.openlocfilehash: e835737b388427445a15b6658c7d148801f29b79
ms.lasthandoff: 03/13/2017

---
# <a name="set-operations-visual-basic"></a>Opérations ensemblistes (Visual Basic)
Opérations de définition dans LINQ font référence aux opérations de requête qui produisent un jeu de résultats qui est basé sur la présence ou l’absence d’éléments équivalents dans la même ou distinct collections (ou ensembles).  
  
 Les méthodes d’opérateur de requête standard qui effectuent des opérations de jeu répertoriés dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|distinct|Supprime les doublons d’une collection.|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName></xref:System.Linq.Queryable.Distinct%2A?displayProperty=fullName>|  
|À l'exception|Retourne la différence définie, ce qui signifie que les éléments d’une collection qui n’apparaissent pas dans une deuxième collection.|Non applicable.|<xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=fullName></xref:System.Linq.Queryable.Except%2A?displayProperty=fullName>|  
|Définir une intersection|Retourne l’intersection, ce qui signifie que les éléments qui apparaissent dans chacun des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName></xref:System.Linq.Queryable.Intersect%2A?displayProperty=fullName>|  
|Union|Retourne l’union, ce qui signifie que les éléments uniques qui apparaissent dans une des deux collections.|Non applicable.|<xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Union%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=fullName></xref:System.Linq.Queryable.Union%2A?displayProperty=fullName>|  
  
## <a name="comparison-of-set-operations"></a>Comparaison d’opérations ensemblistes  
  
### <a name="distinct"></a>distinct  
 L’illustration suivante représente le comportement de la <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName>méthode sur une séquence de caractères.</xref:System.Linq.Enumerable.Distinct%2A?displayProperty=fullName> La séquence retournée contient les éléments uniques de la séquence d’entrée.  
  
 ![Graphique illustrant le comportement de Distinct(). ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinctes")  
  
### <a name="except"></a>À l'exception  
 L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Except%2A?displayProperty=fullName> La séquence retournée contienne uniquement les éléments de la première séquence d’entrée qui ne sont pas dans la deuxième séquence d’entrée.  
  
 ![Graphique montrant l’action de Except(). ](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")  
  
### <a name="intersect"></a>Définir une intersection  
 L’illustration suivante représente le comportement de <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName>.</xref:System.Linq.Enumerable.Intersect%2A?displayProperty=fullName> La séquence retournée contient les éléments qui sont communs aux deux séquences d’entrée.  
  
 ![Graphique illustrant l’intersection de deux séquences. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Se croisent")  
  
### <a name="union"></a>Union  
 L’illustration suivante représente une opération d’union de deux séquences de caractères. La séquence retournée contient les éléments uniques des deux séquences d’entrée.  
  
 ![Graphique illustrant l’union de deux séquences. ](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe de requête Expression  
 L’exemple suivant utilise le `Distinct` clause dans une requête LINQ pour retourner les nombres uniques d’une liste d’entiers.  
  
 [!code-vb[CsLINQSetOps n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Clause distinct](../../../../visual-basic/language-reference/queries/distinct-clause.md)   
 [Comment : combiner et comparer des Collections de chaînes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)   
 [Comment : rechercher la différence définie entre deux listes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
