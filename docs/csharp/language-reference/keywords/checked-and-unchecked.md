---
title: "Checked et Unchecked (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "checked (instruction C#)"
  - "exceptions (C#), contrôle de dépassement de capacité"
  - "opérateurs (C#), checked et unchecked"
  - "contrôle de dépassement de capacité (C#)"
  - "instructions (C#), checked et unchecked"
  - "unchecked (instruction C#)"
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Checked et Unchecked (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les instructions C\# peuvent s'exécuter dans un contexte vérifié \(checked\) ou non vérifié \(unchecked\).  Dans un contexte vérifié, un dépassement de capacité arithmétique lève une exception.  Dans un contexte non vérifié, un dépassement de capacité arithmétique et le résultat sont tronqués.  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md) Indique un contexte vérifié.  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md) Indique un contexte non vérifié.  
  
 Si ni `checked`, ni `unchecked` n'est spécifié, le contexte par défaut dépend de facteurs externes, notamment les options du compilateur.  
  
 Les opérations suivantes sont concernées par la vérification du dépassement de capacité :  
  
-   Expressions utilisant les opérateurs prédéfinis suivants dans des types intégraux :  
  
     `++`  `--` \- \(unaire\)   `+` \-   `*` `/`  
  
-   Conversions numériques explicites entre types intégraux.  
  
 L'option du compilateur [\/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) vous permet d'indiquer le contexte vérifié ou non vérifié pour toutes les instructions arithmétiques entières qui ne figurent pas explicitement dans l'étendue d'un mot clé `checked` ou `unchecked`.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d'instructions](../../../csharp/language-reference/keywords/statement-keywords.md)