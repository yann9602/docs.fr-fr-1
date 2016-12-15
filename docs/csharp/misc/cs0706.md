---
title: "Erreur du compilateur CS0706 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0706"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0706"
ms.assetid: bc3ac5c0-8c96-43c8-b10a-69bd31b38e4a
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0706
Type de contrainte non valide. Un type utilisé comme contrainte doit être une interface, une classe non\-sealed ou un paramètre de type.  
  
 Cette erreur se produit quand une construction non valide est utilisée dans une clause de contrainte. Pour éviter cette erreur, utilisez une interface ou une classe non\-sealed au lieu de la construction à l’origine de l’erreur.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0706.  
  
```  
// CS0706.cs // compile with: /target:library class A {} class C<T> where T : int[] {}  // CS0706 class D<T> where T : A {}  // OK  
```