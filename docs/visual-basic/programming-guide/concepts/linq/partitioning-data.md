---
title: "Partitionnement des données (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69c59379-b66e-422c-b324-5b5c07760ef7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0ea305a67765e1b11ceebbf65c48a685024a41f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-visual-basic"></a>Partitionnement des données (Visual Basic)
Le partitionnement dans LINQ désigne l’opération consistant à diviser une séquence d’entrée en deux sections, sans réorganiser les éléments, puis à retourner l’une des sections.  
  
 L’illustration suivante montre les résultats de trois opérations de partitionnement différentes sur une séquence de caractères. La première opération retourne les trois premiers éléments de la séquence. La deuxième opération ignore les trois premiers éléments et retourne les éléments restants. La troisième opération ignore les deux premiers éléments de la séquence et retourne les trois éléments suivants.  
  
 ![Opérations de partitionnement LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")  
  
 Les méthodes d’opérateurs de requête standard qui partitionnent des séquences sont répertoriées dans la section suivante.  
  
## <a name="operators"></a>Opérateurs  
  
|Nom d'opérateur|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-------------------|-----------------|------------------------------------------|----------------------|  
|Ignorer|Ignore les éléments jusqu’à une position spécifiée dans une séquence.|`Skip`|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|SkipWhile|Ignore les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.|`Skip While`|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|Take|Prend les éléments jusqu’à une position spécifiée dans une séquence.|`Take`|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|TakeWhile|Prend les éléments basés sur une fonction de prédicat jusqu’à un élément qui ne remplit pas la condition.|`Take While`|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a>Exemples de syntaxe d'expression de requête  
  
### <a name="skip"></a>Ignorer  
 Le code suivant exemple utilise le `Skip` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour ignorer les quatre premières chaînes dans un tableau de chaînes avant de retourner les chaînes restantes dans le tableau.  
  
 [!code-vb[CsLINQPartitioning#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_1.vb)]  
  
### <a name="skipwhile"></a>SkipWhile  
 Le code suivant exemple utilise le `Skip While` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour ignorer les chaînes dans un tableau lors de la première lettre de la chaîne est « a ». Les chaînes restantes dans le tableau sont retournés.  
  
 [!code-vb[CsLINQPartitioning#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_2.vb)]  
  
### <a name="take"></a>Take  
 Le code suivant exemple utilise le `Take` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour retourner les deux premières chaînes dans un tableau de chaînes.  
  
 [!code-vb[CsLINQPartitioning#3](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_3.vb)]  
  
### <a name="takewhile"></a>TakeWhile  
 Le code suivant exemple utilise le `Take While` clause dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] pour retourner des chaînes à partir d’un tableau pendant que la longueur de la chaîne est inférieur ou égal à cinq.  
  
 [!code-vb[CsLINQPartitioning#4](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/partitioning-data_4.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq>  
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Skip (clause)](../../../../visual-basic/language-reference/queries/skip-clause.md)  
 [Skip While (clause)](../../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take (clause)](../../../../visual-basic/language-reference/queries/take-clause.md)  
 [Take While (clause)](../../../../visual-basic/language-reference/queries/take-while-clause.md)
