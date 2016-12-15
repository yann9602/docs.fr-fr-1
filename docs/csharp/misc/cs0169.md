---
title: "Avertissement du compilateur (niveau&#160;3) CS0169 | Microsoft Docs"
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
  - "CS0169"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0169"
ms.assetid: 04b0015f-658d-440a-b9ba-831178f1a180
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;3) CS0169
Le champ privé 'class member' n’est jamais utilisé  
  
 Une variable privée a été déclarée mais n’a jamais été référencée Cet avertissement est généralement généré lorsque vous déclarez un membre privé d’une classe et que vous ne l’utilisez pas.  
  
 L’exemple suivant génère l’avertissement CS0169 :  
  
```  
// compile with: /W:3 using System; public class ClassX { int i;   // CS0169, i is not used anywhere public static void Main() { } }  
```