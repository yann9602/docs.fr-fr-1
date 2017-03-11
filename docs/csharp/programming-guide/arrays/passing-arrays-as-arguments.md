---
title: "Passage de tableaux en tant qu&#39;arguments (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "tableaux (C#), passer en tant qu'arguments"
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 21
---
# Passage de tableaux en tant qu&#39;arguments (Guide de programmation&#160;C#)
Les tableaux peuvent être passés en tant qu'arguments aux paramètres de méthode.  Étant donné que les tableaux sont des types référence, la méthode peut modifier la valeur des éléments.  
  
## Passage de tableaux unidimensionnels en tant qu'arguments  
 Vous pouvez passer un tableau unidimensionnel initialisé à une méthode.  Par exemple, l'instruction suivante envoie un tableau à une méthode Print.  
  
 [!code-cs[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_1.cs)]  
  
 Le code suivant illustre une implémentation partielle de la méthode Print.  
  
 [!code-cs[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_2.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme illustré dans l'exemple suivant.  
  
 [!code-cs[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_3.cs)]  
  
## Exemple  
  
### Description  
 Dans l'exemple suivant, un tableau de chaînes est initialisé et passé en tant qu'argument à une méthode `PrintArray` pour des chaînes.  La méthode affiche les éléments du tableau.  Ensuite, les méthodes `ChangeArray` et `ChangeArrayElement` sont appelées pour montrer que l'envoi d'un argument de tableau par valeur n'empêche pas les modifications apportées aux éléments de tableau.  
  
### Code  
 [!code-cs[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_4.cs)]  
  
## Passage de tableaux multidimensionnels en tant qu'arguments  
 Vous pouvez passer un tableau multidimensionnel initialisé à une méthode comme un tableau unidimensionnel.  
  
 [!code-cs[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_5.cs)]  
  
 Le code suivant illustre une déclaration partielle d'une méthode Print qui accepte un tableau à deux dimensions en tant qu'argument.  
  
 [!code-cs[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_6.cs)]  
  
 Vous pouvez initialiser et passer un nouveau tableau en une seule étape, comme illustré dans l'exemple suivant.  
  
 [!code-cs[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_7.cs)]  
  
## Exemple  
  
### Description  
 Dans l'exemple suivant, un tableau à deux dimensions d'entiers est initialisé et passé à la méthode `Print2DArray`.  La méthode affiche les éléments du tableau.  
  
### Code  
 [!code-cs[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/csharp/passing-arrays-as-argume_8.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Tableaux](../../../csharp/programming-guide/arrays/index.md)   
 [Tableaux unidimensionnels](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)   
 [Tableaux multidimensionnels](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)   
 [Tableaux en escalier](../../../csharp/programming-guide/arrays/jagged-arrays.md)