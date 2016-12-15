---
title: "Erreur du compilateur CS0836 | Microsoft Docs"
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
  - "CS0836"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0836"
ms.assetid: 74a12271-1612-45aa-a398-7964e0269892
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0836
Impossible d’utiliser un type anonyme dans une expression constante.  
  
 Les seuls éléments autorisés dans une expression constante sont les constantes nommées, les littéraux et les expressions mathématiques qui combinent des expressions constantes.  
  
### Pour corriger cette erreur  
  
1.  Faites du type anonyme un type nommé.  
  
## Exemple  
 L’exemple suivant illustre une façon de générer l’erreur CS0836 :  
  
```  
// cs0836.cs using System; [AttributeUsage(AttributeTargets.Class, AllowMultiple = true, Inherited = false)] public class A : Attribute { public A(object obj) { } } [A(new { })] // CS0836 public class B { } public class Test { public static int Main() { return 0; } }  
```