---
title: "How to: Sort An Array in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Array.Sort"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arrays [Visual Basic], sorting"
  - "examples [Visual Basic], arrays"
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Sort An Array in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cet exemple déclare un tableau d'objets `String` nommé `zooAnimals`, le remplit et le trie par ordre alphabétique.  
  
## Exemple  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## Compilation du code  
 Cet exemple nécessite :  
  
-   Accès à Mscorlib.dll et à l'espace de noms <xref:System>.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le tableau est vide \(classe <xref:System.ArgumentNullException>\).  
  
-   Le tableau est multidimensionnel \(classe <xref:System.RankException>\).  
  
-   Un ou plusieurs éléments du tableau n'implémentent pas l'interface <xref:System.IComparable> \(classe <xref:System.InvalidOperationException>\).  
  
## Voir aussi  
 <xref:System.Array.Sort%2A?displayProperty=fullName>   
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)   
 [Troubleshooting Arrays](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)   
 [Collections](../Topic/Collections%20\(C%23%20and%20Visual%20Basic\).md)   
 [For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)