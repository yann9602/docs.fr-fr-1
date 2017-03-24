---
title: "Partitionnement des données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
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
ms.openlocfilehash: a746ce3e24812d1df6b6e221cca0364bf2cc7f1c
ms.lasthandoff: 03/13/2017

---
# <a name="partitioning-data-visual-basic"></a>Partitionnement des données (Visual Basic)
Partitionnement dans LINQ fait référence à l’opération de division d’une séquence d’entrée en deux sections, sans réorganiser les éléments, puis retourner une des sections.  
  
 L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères. La première opération retourne les trois premiers éléments de la séquence. La deuxième opération ignore les trois premiers éléments et retourne les éléments restants. La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments.  
  
 ![LINQ, opérations de partitionnement](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Les méthodes d’opérateur de requête standard qui partitionnent les séquences sont répertoriées dans la section suivante.  
  
## <a name="operators"></a>Opérateurs  
  
|Nom d'opérateur|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Ignorer|Ignore les éléments jusqu'à une position spécifiée dans une séquence.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Skip%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName></xref:System.Linq.Queryable.Skip%2A?displayProperty=fullName>|  
|SkipWhile|Ignore les éléments basés sur une fonction de prédicat jusqu'à ce qu’un élément ne remplit pas la condition.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=fullName>|  
|Take|Prend les éléments jusqu'à une position spécifiée dans une séquence.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Take%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=fullName></xref:System.Linq.Queryable.Take%2A?displayProperty=fullName>|  
|TakeWhile|Prend les éléments basés sur une fonction de prédicat jusqu'à ce qu’un élément ne remplit pas la condition.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName></xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="skip"></a>Ignorer  
 Le code suivant exemple utilise le `Skip` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour ignorer les quatre premières chaînes d’un tableau de chaînes avant de retourner les chaînes restantes dans le tableau.  
  
 [!code-vb[CsLINQPartitioning n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Le code suivant exemple utilise le `Skip While` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour ignorer les chaînes dans un tableau dont la première lettre de la chaîne est « a ». Les chaînes restantes dans le tableau sont retournés.  
  
 [!code-vb[CsLINQPartitioning n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Le code suivant exemple utilise le `Take` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour retourner les deux premières chaînes dans un tableau de chaînes.  
  
 [!code-vb[CsLINQPartitioning n °&3;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Le code suivant exemple utilise le `Take While` clause dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour renvoyer des chaînes à partir d’un tableau dont la longueur de la chaîne est inférieur ou égal à cinq.  
  
 [!code-vb[CsLINQPartitioning n °&4;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Skip (Clause)](../../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Skip While, Clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take, Clause](../../../../visual-basic/language-reference/queries/take-clause.md)   
 [Take While (clause)](../../../../visual-basic/language-reference/queries/take-while-clause.md)
