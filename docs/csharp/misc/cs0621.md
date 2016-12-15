---
title: "Erreur du compilateur CS0621 | Microsoft Docs"
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
  - "CS0621"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0621"
ms.assetid: 7ff392c6-478c-4971-93dc-f837b1b8748c
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0621
'membre' : les membres virtual ou abstract ne peuvent pas être private  
  
 Les membres **virtual** et **abstract** private ne sont pas autorisés.  
  
 L’exemple suivant génère l’erreur CS0621 :  
  
```  
// CS0621.cs abstract class MyClass { private virtual void DoNothing1()   // CS0621 { } private abstract void DoNothing2();   // CS0621 public static void Main() { } }  
```