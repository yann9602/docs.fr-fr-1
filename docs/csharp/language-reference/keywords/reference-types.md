---
title: "Types r&#233;f&#233;rence (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.referencetypes"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, types référence"
  - "types référence (C#)"
  - "types (C#), types référence"
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Types r&#233;f&#233;rence (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Il existe deux genres de types en C\# : les types référence et les types valeur.  Les variables des types référence font référence à leurs données \(objets\), tandis que les variables des types valeur contiennent directement leurs données.  Avec les types référence, deux variables peuvent faire référence au même objet ; par conséquent, les opérations sur une variable peuvent affecter le même objet référencé par l'autre variable.  Avec les types valeur, chaque variable possède sa propre copie de données, et les opérations sur une variable ne peuvent absolument pas affecter l'autre \(sauf pour les variables de paramètre ref et out, consultez [ref](../../../csharp/language-reference/keywords/ref.md) et [out, modificateur de paramètre](../../../csharp/language-reference/keywords/out-parameter-modifier.md)\).  
  
 Les mots clés suivants sont utilisés pour déclarer des types référence :  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [délégué](../../../csharp/language-reference/keywords/delegate.md)  
  
 C\# fournit également les types référence intégrés suivants :  
  
-   [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [object](../../../csharp/language-reference/keywords/object.md)  
  
-   [string](../../../csharp/language-reference/keywords/string.md)  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)