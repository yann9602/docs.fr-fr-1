---
title: "==, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "==_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "== (opérateur C#)"
  - "opérateur d'égalité (C#)"
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ==, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Pour les types valeur prédéfinis, l'opérateur d'égalité \(`==`\) retourne true si les valeurs des opérandes sont égales et `false` dans le cas contraire.  Pour les types référence autres que [string](../../../csharp/language-reference/keywords/string.md), `==` retourne `true` si ses deux opérandes font référence au même objet.  Pour le type `string`, `==` compare les valeurs des chaînes.  
  
## Notes  
 Les types valeur définis par l'utilisateur peuvent surcharger l'opérateur `==` \(consultez [operateur](../../../csharp/language-reference/keywords/operator.md)\).  Les types référence définis par l'utilisateur peuvent faire de même, même si par défaut `==` se comporte comme décrit ci\-dessus pour les types référence prédéfinis et définis par l'utilisateur.  Si `==` est surchargé, [\!\=](../../../csharp/language-reference/operators/not-equal-operator.md) doit l'être également.  Les opérations sur les types intégraux sont en général autorisées sur énumération.  
  
## Exemple  
 [!code-cs[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)