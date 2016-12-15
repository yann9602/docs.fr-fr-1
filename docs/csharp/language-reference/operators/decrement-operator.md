---
title: "--, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "--_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-- (opérateur C#)"
  - "-- (opérateur de décrémentation C#)"
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# --, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

L'opérateur de décrémentation \(`--`\) décrémente son opérande d'une unité.  L'opérateur de décrémentation peut figurer avant ou après son opérande : `--variable` et `variable--`.  La première syntaxe correspond à une opération de pré\-décrémentation.  Le résultat de l'opération représente la valeur de l'opérande « après » sa décrémentation.  La seconde syntaxe correspond à une opération de post\-décrémentation.  Le résultat de l'opération représente la valeur de l'opérande « avant » sa décrémentation.  
  
## Notes  
 Les types numériques et d'énumération disposent d'opérateurs de décrément prédéfinis.  
  
 Les types définis par l'utilisateur peuvent surcharger l'opérateur `--` \(consultez [opérateur](../../../csharp/language-reference/keywords/operator.md)\).  Les opérations sur les types intégraux sont en général autorisées sur énumération.  
  
## Exemple  
 [!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)