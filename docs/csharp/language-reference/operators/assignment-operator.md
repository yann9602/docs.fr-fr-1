---
title: "=, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "=_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "= (opérateur C#)"
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# =, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur d'assignation \(`=`\) stocke la valeur de l'opérande de droite dans l'emplacement de stockage, la propriété ou l'indexeur stipulé par l'opérande de gauche et retourne la valeur comme résultat.  Les opérandes doivent être du même type \(ou l'opérande de droite doit être implicitement convertible au type de l'opérande de gauche\).  
  
## Notes  
 L'opérateur d'assignation ne peut pas être surchargé.  Toutefois, vous pouvez définir des opérateurs de conversion implicites pour un type, qui vous permettent d'utiliser l'opérateur d'assignation avec ces types.  Pour plus d'informations, consultez [Utilisation d'opérateurs de conversion](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## Exemple  
 [!code-cs[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)