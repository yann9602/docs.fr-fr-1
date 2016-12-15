---
title: "&#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type | Microsoft Docs"
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
  - "bc32128"
  - "vbc32128"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32128"
ms.assetid: 1155b23a-ad75-4bab-b9da-73f35c767a36
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;IsNot&#39; operand of type &#39;typename&#39; can only be compared to &#39;Nothing&#39;, because &#39;typename&#39; is a nullable type
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une variable déclarée nullable a été comparée à une expression autre que `Nothing` à l'aide de l'opérateur `IsNot`.  
  
 **ID d'erreur :** BC32128  
  
### Pour corriger cette erreur  
  
1.  Pour comparer un type nullable à une expression autre que `Nothing` à l'aide de l'opérateur `IsNot`, appelez la méthode `GetType` sur le type Nullable et comparez le résultat avec l'expression, comme illustré dans l'exemple suivant.  
  
    ```vb#  
    Dim number? As Integer = 5  
  
    If number IsNot Nothing Then  
      If number.GetType() IsNot Type.GetType("System.Int32") Then   
  
      End If  
    End If  
    ```  
  
## Voir aussi  
 [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)   
 [IsNot Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)