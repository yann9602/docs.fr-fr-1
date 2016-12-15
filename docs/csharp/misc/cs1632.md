---
title: "Erreur du compilateur CS1632 | Microsoft Docs"
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
  - "CS1632"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1632"
ms.assetid: fa18061a-8c6c-4788-b74e-62bacb16aed8
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1632
Le contrôle ne peut pas quitter le corps d'une méthode anonyme ou d'une expression lambda  
  
 Cette erreur se produit si une instruction de saut \(**break**, `goto`, **continue**, etc.\) tente de déplacer le contrôle hors d’un bloc de méthode anonyme. Un bloc de méthode anonyme est un corps de fonction. Pour l’arrêter, une instruction return doit être émise ou la fin du bloc doit être atteinte.  
  
 L’exemple suivant génère l’erreur CS1632 :  
  
```  
// CS1632.cs // compile with: /target:library delegate void MyDelegate(); class MyClass { public void Test() { for (int i = 0 ; i < 5 ; i++) { MyDelegate d = delegate { break;   // CS1632 }; } } }  
```