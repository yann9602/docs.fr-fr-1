---
title: "Avertissement du compilateur (niveau&#160;1) CS0612 | Microsoft Docs"
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
  - "CS0612"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0612"
ms.assetid: 7695f3b7-ffef-43f7-83db-fc1a9e361f1a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;1) CS0612
'membre' est obsolète.  
  
 Le Concepteur de classes a marqué un membre avec l’attribut [Obsolete](http://msdn.microsoft.com/fr-fr/05e99cd0-bda6-4f79-a890-1ca093b4b488). Cela signifie que le membre ne sera peut\-être pas pris en charge dans une version ultérieure de la classe.  
  
 L’exemple suivant montre comment l’accès à un membre obsolète génère l’avertissement CS0612 :  
  
```  
// CS0612.cs // compile with: /W:1 using System; class MyClass { [Obsolete] public static void ObsoleteMethod() { } [Obsolete] public static int ObsoleteField; } class MainClass { static public void Main() { MyClass.ObsoleteMethod();    // CS0612 here: method is deprecated MyClass.ObsoleteField = 0;   // CS0612 here: field is deprecated } }  
```