---
title: "Regroupement de données (Visual Basic) | Documents Microsoft"
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
ms.assetid: 8f3a0871-6958-4aef-8f6f-493e189fd57d
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
ms.openlocfilehash: d89ae6d155ab901b03cf92a7508261fb147b97b7
ms.lasthandoff: 03/13/2017

---
# <a name="grouping-data-visual-basic"></a>Regroupement de données (Visual Basic)
Le regroupement consiste à placer des données dans des groupes afin que les éléments de chaque groupe partagent un attribut commun.  
  
 L’illustration suivante montre les résultats du regroupement d’une séquence de caractères. La clé pour chaque groupe est le caractère.  
  
 ![Opérations de regroupement LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_group.png "LINQ_Group")  
  
 Les méthodes d’opérateur de requête standard qui regroupent des éléments de données sont répertoriées dans la section suivante.  
  
## <a name="methods"></a>Méthodes  
  
|Nom de la méthode|Description|Syntaxe d’Expression de requête Visual Basic|Informations complémentaires|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|GroupBy|Regroupe les éléments qui partagent un attribut commun. Chaque groupe est représenté par un <xref:System.Linq.IGrouping%602>objet.</xref:System.Linq.IGrouping%602>|`Group … By … Into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=fullName><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName></xref:System.Linq.Queryable.GroupBy%2A?displayProperty=fullName>|  
|ToLookup|Insère des éléments dans un <xref:System.Linq.Lookup%602>(un dictionnaire de type un-à-plusieurs) basé sur une fonction de sélection de clé.</xref:System.Linq.Lookup%602>|Non applicable.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName></xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=fullName>|  
  
## <a name="query-expression-syntax-example"></a>Exemple de syntaxe de requête Expression  
 Le code suivant exemple utilise le `Group By` clause pour regrouper des entiers dans une liste selon qu’ils sont pairs ou impairs.  
  
```vb  
Dim numbers As New System.Collections.Generic.List(Of Integer)(  
     New Integer() {35, 44, 200, 84, 3987, 4, 199, 329, 446, 208})  
  
Dim query = From number In numbers   
            Group By Remainder = (number Mod 2) Into Group  
  
Dim sb As New System.Text.StringBuilder()  
For Each group In query  
    sb.AppendLine(If(group.Remainder = 0, vbCrLf & "Even numbers:", vbCrLf & "Odd numbers:"))  
    For Each num In group.Group  
        sb.AppendLine(num)  
    Next  
Next  
  
' Display the results.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' Odd numbers:  
' 35  
' 3987  
' 199  
' 329  
  
' Even numbers:  
' 44  
' 200  
' 84  
' 4  
' 446  
' 208  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Linq></xref:System.Linq>   
 [Vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)   
 [GROUP BY, Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md)   
 [Comment : regrouper des fichiers par Extension (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)   
 [Comment : fractionner un fichier en plusieurs fichiers à l’aide de groupes (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
