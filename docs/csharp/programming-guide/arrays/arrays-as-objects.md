---
title: "Tableaux en tant qu&#39;objets (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux (C#), sous forme d'objets"
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Tableaux en tant qu&#39;objets (guide de programmation C#)
En C\#, les tableaux sont en fait des objets, et pas simplement des régions adressables de mémoire contiguë comme en C et C\+\+.  <xref:System.Array> est le type de base abstrait de tous les types de tableau.  Vous avez la possibilité d'utiliser les propriétés et les autres membres de classe de ce <xref:System.Array>.  Vous pourriez, par exemple, utiliser la propriété <xref:System.Array.Length%2A> pour obtenir la longueur d'un tableau.  Le code suivant assigne la longueur du tableau `numbers`, c'est\-à\-dire la valeur `5`, à une variable intitulée `lengthOfNumbers` :  
  
 [!code-cs[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 La classe <xref:System.Array> fournit beaucoup d'autres méthodes et propriétés utiles pour trier, rechercher et copier des tableaux.  
  
## Exemple  
 Cet exemple utilise la propriété <xref:System.Array.Rank%2A> pour afficher le nombre de dimensions d'un tableau.  
  
 [!code-cs[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)