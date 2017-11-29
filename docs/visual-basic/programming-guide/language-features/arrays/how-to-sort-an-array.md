---
title: "Comment : trier un tableau dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: Array.Sort
helpviewer_keywords:
- arrays [Visual Basic], sorting
- examples [Visual Basic], arrays
ms.assetid: 9289aeaa-9626-4698-94a7-1d1fd3702b87
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 310c2dacb384de49c80073840c6c58d37f3937d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-sort-an-array-in-visual-basic"></a>Comment : trier un tableau dans Visual Basic
Cet exemple déclare un tableau de `String` objets nommés `zooAnimals`, il remplit, puis le tri par ordre alphabétique.  
  
## <a name="example"></a>Exemple  
  
```  
Private Sub sortAnimals()  
    Dim zooAnimals(2) As String  
    zooAnimals(0) = "lion"  
    zooAnimals(1) = "turtle"  
    zooAnimals(2) = "ostrich"  
    Array.Sort(zooAnimals)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   Accès à Mscorlib.dll et <xref:System> espace de noms.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le tableau est vide (<xref:System.ArgumentNullException> classe)  
  
-   Le tableau est multidimensionnel (<xref:System.RankException> classe)  
  
-   Un ou plusieurs éléments du tableau n’implémentent pas le <xref:System.IComparable> interface (<xref:System.InvalidOperationException> classe)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Dépannage des tableaux](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)  
 [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [For Each...Next (instruction)](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
