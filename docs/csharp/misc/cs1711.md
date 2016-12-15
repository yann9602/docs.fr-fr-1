---
title: "Avertissement du compilateur (niveau&#160;2)&#160;CS1711 | Microsoft Docs"
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
  - "CS1711"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1711"
ms.assetid: 0021275a-43eb-4295-929e-bb3283577a11
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2)&#160;CS1711
Le commentaire XML sur 'type' a une balise typeparam pour 'parameter', mais il n’existe pas de paramètre de type associé à ce nom  
  
 La documentation d’un type générique inclut une balise pour le paramètre de type dont le nom est incorrect.  
  
## Exemple  
 Le code suivant génère l’avertissement CS1711.  
  
```  
// cs1711.cs // compile with: /doc:cs1711.xml // CS1711 expected using System; ///<typeparam name="WrongName">can be an int</typeparam> class CMain { public static void Main() { } }  
```