---
title: "Range variable name can be inferred only from a simple or qualified name with no arguments | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36599"
  - "bc36599"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36599"
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Range variable name can be inferred only from a simple or qualified name with no arguments
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un élément de programmation qui prend un ou plusieurs arguments est inclus dans une requête LINQ.  Le compilateur ne peut pas déduire de variable de portée de cet élément de programmation.  
  
 **ID d'erreur :** BC36599  
  
### Pour corriger cette erreur  
  
1.  Fournissez un nom de variable explicite pour l'élément de programmation, comme indiqué dans le code suivant :  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias = SampleFunction(var1), var1  
```  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)