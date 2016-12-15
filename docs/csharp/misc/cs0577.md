---
title: "Erreur du compilateur CS0577 | Microsoft Docs"
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
  - "CS0577"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0577"
ms.assetid: 34f8f453-f016-4f2c-981a-0d61449cd74b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0577
L’attribut Conditional n’est pas valide sur 'function', car il s’agit d’un constructeur, d’un destructeur, d’un opérateur ou d’une implémentation d’interface explicite  
  
 `Conditional` ne peut pas être appliqué aux méthodes spécifiées.  
  
 Par exemple, vous ne pouvez pas utiliser certains attributs sur une définition d’interface explicite. L’exemple suivant génère l’erreur CS0577 :  
  
```  
// CS0577.cs // compile with: /target:library interface I { void m(); } public class MyClass : I { [System.Diagnostics.Conditional("a")]   // CS0577 void I.m() {} }  
```