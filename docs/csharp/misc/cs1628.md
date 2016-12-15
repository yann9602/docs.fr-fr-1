---
title: "Erreur du compilateur CS1628 | Microsoft Docs"
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
  - "CS1628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1628"
ms.assetid: 520f864c-afe3-4db2-b44e-cfaac28ff49d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1628
Impossible d’utiliser le paramètre ref ou out 'paramètre' dans une méthode anonyme, une expression lambda ou une expression de requête  
  
 Cette erreur se produit si vous utilisez un paramètre ref ou out à l’intérieur d’un bloc de méthode anonyme. Pour éviter cette erreur, utilisez une variable locale ou une autre construction.  
  
 L’exemple suivant génère l’erreur CS1628 :  
  
```  
// CS1628.cs delegate int MyDelegate(); class C { public static void F(ref int i) { MyDelegate d = delegate { return i; };  // CS1628 // Try this instead: // int tmp = i; // MyDelegate d = delegate { return tmp; }; } public static void Main() { } }  
```