---
title: "%, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "%_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "% (opérateur C#)"
  - "opérateur modulo (C#)"
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# %, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

l'opérateur d' `%` calcule le reste après avoir divisé son premier opérande par sa seconde.  Tous les types numériques disposent intégré des opérateurs de reste.  
  
## Notes  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `%` \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  Lorsqu'un opérateur binaire est surchargé, l'opérateur d'assignation correspondant \(s'il y en a un\) est, lui aussi, implicitement surchargé.  
  
## Exemple  
 [!code-cs[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## Commentaires  
 Notez les erreurs d'arrondi associées au type double.  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)