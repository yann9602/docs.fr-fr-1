---
title: "Derived Math Functions (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "arithmetic operations, derived math functions"
  - "cosecant function"
  - "arcsecant function"
  - "arccotangent function"
  - "functions [Visual Basic], derived math functions"
  - "inverse functions"
  - "math functions, derived"
  - "derived math functions"
  - "cotangent function"
  - "angles"
  - "secant function"
  - "trigonometric functions"
  - "logarithms"
  - "arccosecant function"
  - "hyperbolic functions"
  - "arcsine function"
  - "degrees"
  - "arccosine function"
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Derived Math Functions (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le tableau suivant répertorie les fonctions mathématiques non intrinsèques qui peuvent être dérivées des fonctions mathématiques intrinsèques de l'objet <xref:System.Math?displayProperty=fullName>.  Vous pouvez accéder aux fonctions mathématiques intrinsèques en ajoutant `Imports System.Math` à votre fichier ou projet.  
  
|Fonction|Équivalents|  
|--------------|-----------------|  
|Sécante \(Sec\(x\)\)|1 \/ Cos\(x\)|  
|Cosécante \(Csc\(x\)\)|1 \/ Sin\(x\)|  
|Cotangente \(Ctan\(x\)\)|1 \/ Tan\(x\)|  
|Arcsinus \(Asin\(x\)\)|Atan\(x \/ Sqrt\(\-x \* x \+ 1\)\)|  
|Arccosinus \(Acos\(x\)\)|Atan\(\-x \/ Sqrt\(\-x \* x \+ 1\)\) \+ 2 \* Atan\(1\)|  
|Arcsécante \(Asec\(x\)\)|2 \* Atan\(1\) – Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Arccosécante \(Acsc\(x\)\)|Atan\(Sign\(x\) \/ Sqrt\(x \* x – 1\)\)|  
|Arccotangente \(Acot\(x\)\)|2 \* Atan\(1\) \- Atan\(x\)|  
|Arcsinus hyperbolique \(Sinh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ 2|  
|Cosinus hyperbolique \(Cosh\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ 2|  
|Tangente hyperbolique \(Tanh\(x\)\)|\(Exp\(x\) – Exp\(\-x\)\) \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Sécante hyperbolique \(Sech\(x\)\)|2 \/ \(Exp\(x\) \+ Exp\(\-x\)\)|  
|Cosécante hyperbolique \(Csch\(x\)\)|2 \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Cotangente hyperbolique \(Coth\(x\)\)|\(Exp\(x\) \+ Exp\(\-x\)\) \/ \(Exp\(x\) – Exp\(\-x\)\)|  
|Arcsinus hyperbolique \(Asinh\(x\)\)|Log\(x \+ Sqrt\(x \* x \+ 1\)\)|  
|Arccosinus hyperbolique \(Acosh\(x\)\)|Log\(x \+ Sqrt\(x \* x – 1\)\)|  
|Arctangente hyperbolique \(Atanh\(x\)\)|Log\(\(1 \+ x\) \/ \(1 – x\)\) \/ 2|  
|Arcsécante hyperbolique \(AsecH\(x\)\)|Log\(\(Sqrt\(\-x \* x \+ 1\) \+ 1\) \/ x\)|  
|Arccosécante hyperbolique \(Acsch\(x\)\)|Log\(\(Sign\(x\) \* Sqrt\(x \* x \+ 1\) \+ 1\) \/ x\)|  
|Arccotangente hyperbolique \(Acoth\(x\)\)|Log\(\(x \+ 1\) \/ \(x – 1\)\) \/ 2|  
  
## Voir aussi  
 [Fonctions mathématiques](../../../visual-basic/language-reference/functions/math-functions.md)