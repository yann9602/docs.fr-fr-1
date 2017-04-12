---
title: "Filtrage des données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3751164b7697b63937611c77d9fda0e2873625d8
ms.lasthandoff: 03/13/2017

---
# <a name="filtering-data-visual-basic"></a>Filtrage des données (Visual Basic)
Le filtrage fait référence à l’opération de restriction du jeu de résultats à contenir uniquement les éléments qui satisfont une condition spécifiée. Il est également appelé.  
  
 L’illustration suivante montre les résultats du filtrage d’une séquence de caractères. Le prédicat de l’opération de filtrage Spécifie que le caractère doit être « A ».  
  
 ![Opération de filtrage de LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")  
  
 Les méthodes d’opérateur de requête standard qui effectuent une sélection sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|OfType|Sélectionne des valeurs, en fonction de leur capacité à être casté en un type spécifié.|Non applicable.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName></xref:System.Linq.Enumerable.OfType%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName></xref:System.Linq.Queryable.OfType%2A?displayProperty=fullName>|  
|Où|Sélectionne les valeurs qui sont basées sur une fonction de prédicat.|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName></xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName></xref:System.Linq.Queryable.Where%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe de requête Expression  
 L’exemple suivant utilise le `Where` à filtrer dans un tableau les chaînes qui ont une longueur spécifique.  
  
```vb  
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}  
  
Dim query = From word In words   
            Where word.Length = 3   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' the  
' fox  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [Où Clause](../../../../visual-basic/language-reference/queries/where-clause.md)   
 [Comment : filtrer les résultats de la requête](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)   
 [Comment : interroger les métadonnées d’un Assembly avec réflexion (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)   
 [Comment : interroger des fichiers possédant un attribut spécifié ou un nom (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)   
 [Comment : trier ou filtrer des données texte par mot ou par champ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
