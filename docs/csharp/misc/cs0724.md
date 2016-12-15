---
title: "Erreur du compilateur CS0724 | Microsoft Docs"
ms.custom: ""
ms.date: "10/01/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0724"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0724"
ms.assetid: bcdb2017-7a43-4242-b4e2-a1ae03d6d73f
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0724
n’a pas besoin d’attribut CLSCompliant, car l’assembly n’en a pas  
  
 L’exemple suivant génère l’erreur CS0724 en raison de l’instruction `throw` dans le bloc de la clause `finally`.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0724.  
  
```  
// CS0724.cs using System; class X { static void Test() { try { throw new Exception(); } catch { try { } finally { throw; // CS0724 } } } static void Main() { } }  
```