---
title: "&lt;&lt;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "<<_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<< (opérateur C#)"
  - "opérateur de décalage vers la gauche (<<) (C#)"
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;&lt;, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur de décalage vers la gauche \(`<<`\) décale le premier opérande vers la gauche du nombre de bits spécifié par le second opérande.  Le type du second opérande doit être un [int](../../../csharp/language-reference/keywords/int.md) ou un type qui a une conversion numérique implicite prédéfinie sur `int`.  
  
## Notes  
 Si le premier opérande est [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) \(quantité de 32 bits\), le nombre de décalage est donné par les cinq bits de poids faible du second opérande.  Autrement dit, le nombre de décalage réel est 0 à 31 bits.  
  
 Si le premier opérande est [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) \(quantité de 64 bits\), le nombre de décalage est donné par les six bits de poids faible du second opérande.  Autrement dit, le nombre de décalage réel est 0 à 63 bits.  
  
 Les bits de poids fort qui ne figurent pas dans la plage du type du premier opérande après le décalage sont ignorés, et les bits vides de poids faible sont remplis à l'aide de zéros.  Les opérations de décalage ne causent jamais de dépassement de capacité.  
  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `<<` \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\) ; le type du premier opérande doit être un type défini par l'utilisateur et le type du second opérande doit être `int`.  Lorsqu'un opérateur binaire est surchargé, l'opérateur d'assignation correspondant \(s'il y en a un\) est, lui aussi, implicitement surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## Commentaires  
 Notez que `i<<1` et `i<<33` fournissent le même résultat, car 1 et 33 possèdent les cinq mêmes bits d'ordre bas.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)