---
title: "&#39;&lt;typename&gt;&#39; is a delegate type | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32008"
  - "vbc32008"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32008"
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; is a delegate type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

'\<nomtype\>' est un type délégué.Une construction déléguée accepte une seule expression AddressOf en tant que liste d'arguments.Une expression AddressOf peut souvent être utilisée à la place d'une construction déléguée.  
  
 Une clause `New` qui crée une instance d'une classe déléguée fournit une liste d'arguments non valide au constructeur délégué.  
  
 Vous pouvez fournir seulement une expression `AddressOf` lors de la création d'une nouvelle instance déléguée.  
  
 Cette erreur peut se produire si vous ne passez au constructeur délégué aucun argument, si vous en passez plusieurs ou un seul qui n'est pas une expression `AddressOf` valide.  
  
 **ID d'erreur :** BC32008  
  
### Pour corriger cette erreur  
  
-   Utilisez une seule expression `AddressOf` dans la liste d'arguments pour la classe déléguée dans la clause `New`.  
  
## Voir aussi  
 [New Operator](../../../visual-basic/language-reference/operators/new-operator.md)   
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)   
 [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)