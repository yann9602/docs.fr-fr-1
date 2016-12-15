---
title: "Avertissement du compilateur (niveau&#160;2) CS0472 | Microsoft Docs"
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
  - "cs0472"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0472"
ms.assetid: dc80e0a3-dbd3-4a81-b8bb-a59b510cd3e1
caps.latest.revision: 4
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0472
Le résultat de l’expression est toujours 'valeur1', car une valeur de type 'valeur2' n’est jamais égale à 'null' du type 'valeur3'  
  
 Le compilateur doit émettre un avertissement si vous utilisez un opérateur ayant une valeur de constante Null.  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0472 :  
  
```  
public class Test { public static int Main() { int i = 5; int counter = 0; // Comparison: if (i == null)  // CS0472 // To resolve, use a valid value for i. counter++; return counter; } }  
```