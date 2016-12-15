---
title: "Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3015 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3015"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3015"
ms.assetid: 58182215-0c2f-4497-8baf-ffb29f18d6c7
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur&#160;(niveau&#160;1)&#160;CS3015
'method signature' ne possède aucun constructeur accessible qui utilise uniquement des types conformes CLS  
  
 Pour être conforme CLS, la liste d’arguments d’une classe d’attributs ne peut pas contenir de tableau. Pour plus d’informations sur la conformité CLS, consultez [Écriture d’un code conforme CLS](http://msdn.microsoft.com/fr-fr/4c705105-69a2-4e5e-b24e-0633bc32c7f3) et [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS3015.  
  
```  
// CS3015.cs // compile with: /target:library using System; [assembly:CLSCompliant(true)] public class MyAttribute : Attribute { public MyAttribute(int[] ai) {}   // CS3015 // try the following line instead // public MyAttribute(int ai) {} }  
```