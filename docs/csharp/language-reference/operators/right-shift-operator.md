---
title: "&gt;&gt;, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - ">>_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ">> (opérateur C#)"
  - "opérateur de décalage vers la droite (>>) (C#)"
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &gt;&gt;, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur de décalage vers la droite \(`>>`\) décale le premier opérande vers la droite du nombre de bits spécifié par le second opérande.  
  
## Notes  
 Si le premier opérande est un [int](../../../csharp/language-reference/keywords/int.md) ou [uint](../../../csharp/language-reference/keywords/uint.md) \(quantité 32 bits\), la valeur du décalage est donnée par les cinq bits de poids faible du second opérande \(second opérande & 0x1f\).  
  
 Si le premier opérande est un [long](../../../csharp/language-reference/keywords/long.md) ou [ulong](../../../csharp/language-reference/keywords/ulong.md) \(quantité 64 bits\), la valeur du décalage est donnée par les cinq bits de poids faible du second opérande \(second opérande & 0x3f\).  
  
 Si le premier opérande est un [int](../../../csharp/language-reference/keywords/int.md) ou [long](../../../csharp/language-reference/keywords/long.md), le décalage vers la droite est un décalage arithmétique \(les bits vierges d'ordre haut prennent la valeur du bit de signe\).  Si le premier opérande est de type [uint](../../../csharp/language-reference/keywords/uint.md)ou [ulong](../../../csharp/language-reference/keywords/ulong.md), le décalage vers la droite est un décalage logique \(les bits de poids fort prennent la valeur zéro\).  
  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `>>` ; le type du premier opérande doit être un type défini par l'utilisateur et le type du second opérande doit être [int](../../../csharp/language-reference/keywords/int.md).  Pour plus d'informations, consultez [operator](../../../csharp/language-reference/keywords/operator.md).  Lorsqu'un opérateur binaire est surchargé, l'opérateur d'assignation correspondant \(s'il y en a un\) est, lui aussi, implicitement surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)