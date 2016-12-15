---
title: "++, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "++_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "++ (opérateur C#)"
  - "++ (opérateur d'incrémentation C#)"
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ++, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L’opérateur d’incrément \(`++`\) incrémente son opérande de 1. L’opérateur d’incrément peut figurer avant ou après son opérande : `++variable` et `variable++`.  
  
## Notes  
 La première forme est une opération d’incrément préfixé. Le résultat de l’opération est la valeur de l’opérande après qu’il a été incrémenté.  
  
 La deuxième forme est une opération d’incrément suffixé. Le résultat de l’opération est la valeur de l’opérande avant qu’il ait été incrémenté.  
  
 Les types numériques et d’énumération ont des opérateurs d’incrément prédéfinis. Les types définis par l’utilisateur peuvent surcharger l’opérateur `++`. Les opérations sur les types intégraux sont en général autorisées sur l’énumération.  
  
## Exemple  
 [!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)