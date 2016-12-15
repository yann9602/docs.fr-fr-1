---
title: "Passage de param&#232;tres (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arguments (C#)"
  - "langage C#, paramètres de méthodes"
  - "méthodes (C#), passer des paramètres"
  - "paramètres (C#), passer"
  - "passer des paramètres (C#)"
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Passage de param&#232;tres (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

En C\#, les arguments peuvent être passés aux paramètres par valeur ou par référence.  Le passage de paramètres par référence permet aux fonctions membres, méthodes, propriétés, indexeurs, opérateurs et constructeurs de changer la valeur des paramètres et de rendre persistantes ces modifications dans l'environnement d'appel.  Pour passer un paramètre par référence, utilisez le mot clé `ref` ou `out`.  Par souci de simplicité, seul le mot clé `ref` est utilisé dans les exemples de cette rubrique.  Pour plus d'informations sur la différence entre `ref` et `out`, consultez [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md) et [Passage de tableaux à l'aide de paramètres ref et out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).  
  
 L'exemple suivant illustre la différence entre paramètres de valeur et de référence.  
  
 [!code-cs[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 Pour plus d'informations, consultez les rubriques suivantes :  
  
-   [Passage de paramètres de type valeur](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [Passage de paramètres de type référence](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)