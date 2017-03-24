---
title: "Opérations de quantificateur (Visual Basic) | Documents Microsoft"
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
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
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
ms.openlocfilehash: 7f69aed2e0e6791ca7f17c3420ff75a1ba220187
ms.lasthandoff: 03/13/2017

---
# <a name="quantifier-operations-visual-basic"></a>Opérations de quantificateur (Visual Basic)
Opérations de quantificateur retournent un <xref:System.Boolean>valeur qui indique si certains ou tous les éléments d’une séquence remplissent une condition.</xref:System.Boolean>  
  
 L’illustration suivante représente deux opérations de quantificateur différentes sur deux séquences source différentes. La première opération demande si un ou plusieurs des éléments sont le caractère 'A' et le résultat est `true`. La deuxième opération demande si tous les éléments sont le caractère 'A' et le résultat est `true`.  
  
 ![Opérations de quantificateur LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")  
  
 Les méthodes d’opérateur de requête standard qui effectuent des opérations de quantificateur sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|Tout|Détermine si tous les éléments d’une séquence remplissent une condition.|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=fullName></xref:System.Linq.Enumerable.All%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=fullName></xref:System.Linq.Queryable.All%2A?displayProperty=fullName>|  
|Any|Détermine si tous les éléments d’une séquence remplissent une condition.|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Any%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=fullName></xref:System.Linq.Queryable.Any%2A?displayProperty=fullName>|  
|Contient|Détermine si une séquence contient un élément spécifié.|Non applicable.|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Contains%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName></xref:System.Linq.Queryable.Contains%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
 Ces exemples utilisent la `Aggregate` clause dans Visual Basic en tant que partie de la condition de filtrage dans une requête LINQ.  
  
 L’exemple suivant utilise le `Aggregate` clause et la <xref:System.Linq.Enumerable.All%2A>méthode d’extension pour retourner à partir d’une collection de ces personnes dont les animaux domestiques ont tous dépassés un âge spécifié.</xref:System.Linq.Enumerable.All%2A>  
  
 [!code-vb[CsLINQAnyAll n °&1;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 L’exemple suivant utilise le `Aggregate` clause et la <xref:System.Linq.Enumerable.Any%2A>méthode d’extension à retourner à partir d’une collection les personnes qui ont au moins un animal domestique qui a dépassé un âge spécifié.</xref:System.Linq.Enumerable.Any%2A>  
  
 [!code-vb[CsLINQAnyAll n °&2;](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Aggregate (Clause)](../../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Comment : rechercher des phrases qui contiennent un jeu spécifié de mots (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
