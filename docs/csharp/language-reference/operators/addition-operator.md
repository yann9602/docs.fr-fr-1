---
title: "+, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "+_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "+ (opérateur C#)"
  - "opérateur d'addition (C#)"
  - "opérateur de concaténation (C#)"
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# +, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur `+` peut fonctionner comme opérateur unaire ou binaire.  
  
## Notes  
 Les opérateurs `+` unaires sont prédéfinis pour tous les types numériques.  Le résultat d'une opération `+` unaire sur un type numérique correspond simplement à la valeur de l'opérande.  
  
 Les opérateurs `+` binaires sont prédéfinis pour les types numériques et chaîne.  Pour les types numériques, \+ calcule la somme de ses deux opérandes.  Lorsqu'un ou deux opérandes sont de type String, \+ concatène les représentations de chaîne des opérandes.  
  
 Les types délégués fournissent aussi un opérateur `+` binaire, qui effectue la concaténation de délégués.  
  
 Les types définis par l'utilisateur peuvent surcharger les opérateurs `+` unaires et binaires `+`.  Les opérations sur les types intégraux sont en général autorisées sur énumération.  Pour plus d'informations, consultez [d'opérateur](../../../csharp/language-reference/keywords/operator.md).  
  
## Exemple  
 [!code-cs[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [d'opérateur](../../../csharp/language-reference/keywords/operator.md)