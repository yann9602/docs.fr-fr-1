---
title: "#else (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "#else"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "#else (directive C#)"
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# #else (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

`#else` vous permet de créer une directive conditionnelle composée, afin que, si aucune des expressions dans les directives [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ou \(facultatif\) [\#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) à `true`, le compilateur évalue tout le code entre `#else` et la directive `#endif` suivante.  
  
## Notes  
 [\#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) doit être la prochaine directive de préprocesseur après `#else`.  Pour obtenir un exemple d'utilisation de `#else`, consultez [\#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Directives de préprocesseur C\#](../../../csharp/language-reference/preprocessor-directives/index.md)