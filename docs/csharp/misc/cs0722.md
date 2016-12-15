---
title: "Erreur du compilateur CS0722 | Microsoft Docs"
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
  - "CS0722"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0722"
ms.assetid: 85f6854c-581d-482b-b4b0-1e665d9e3e6f
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0722
'type' : les types static ne peuvent pas être utilisés en tant que types de retour  
  
 Un type static n’est pas pertinent en tant que type de retour, car il est impossible de créer des instances de types static.  
  
 L’exemple suivant génère l’erreur CS0722 :  
  
```  
// CS0722.cs public static class SC { } public class CMain { public SC F()  // CS0722 { return null; } public static void Main() { } }  
```