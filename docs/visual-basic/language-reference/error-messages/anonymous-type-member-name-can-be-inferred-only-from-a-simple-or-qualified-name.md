---
title: "Anonymous type member name can be inferred only from a simple or qualified name with no arguments | Microsoft Docs"
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
  - "vbc36556"
  - "bc36556"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36556"
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Anonymous type member name can be inferred only from a simple or qualified name with no arguments
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous ne pouvez pas déduire de nom de membre de type anonyme d'une expression complexe.  
  
```vb#  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Pour plus d'informations sur les sources à partir desquelles les types anonymes peuvent et ne peuvent pas déduire de noms de membre et de types, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **ID d'erreur :** BC36556  
  
### Pour corriger cette erreur  
  
-   Assignez l'expression à un nom de membre, comme illustré dans le code suivant :  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## Voir aussi  
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)