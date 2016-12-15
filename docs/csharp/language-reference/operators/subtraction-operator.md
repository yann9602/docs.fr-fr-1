---
title: "-, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "-_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "- (opérateur C#)"
  - "opérateur de soustraction (-) (C#)"
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# -, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur `-` peut fonctionner comme opérateur unaire ou binaire.  
  
## Notes  
 Les opérateurs `-` unaires sont prédéfinis pour tous les types numériques.  Le résultat d'une opération `-` unaire sur un type numérique correspond à l'opposé numérique de l'opérande.  
  
 Les opérateurs `-` binaires sont prédéfinis pour tous les types numériques et d'énumérations pour soustraire le second opérande au premier.  
  
 Les types délégués fournissent aussi un opérateur `-` binaire, qui effectue la suppression de délégués.  
  
 Les types définis par l'utilisateur peuvent surcharger les opérateurs `-` unaires et binaires `-`.  Pour plus d'informations, consultez [d'opérateur](../../../csharp/language-reference/keywords/operator.md).  
  
## Exemple  
 [!code-cs[csRefOperators#40](../../../csharp/language-reference/operators/codesnippet/CSharp/subtraction-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)