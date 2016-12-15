---
title: "Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement | Microsoft Docs"
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
  - "bc36635"
  - "vbc36635"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36635"
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Lambda expressions are not valid in the first expression of a &#39;Select Case&#39; statement
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous ne pouvez pas utiliser d'expression lambda pour l'expression de test dans une instruction `Select Case`.  Les définitions d'expression lambda retournent des fonctions et l'expression de test d'une instruction `Select Case` doit être un type de données élémentaire.  
  
 Le code suivant provoque cette erreur :  
  
```vb#  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID d'erreur :** BC36635  
  
### Pour corriger cette erreur  
  
-   Examinez votre code pour déterminer si une construction conditionnelle différente, telle qu'une instruction `If...Then...Else`, pourrait fonctionner.  
  
-   Vous avez pu prévoir d'appeler la fonction, comme indiqué dans le code suivant :  
  
    ```vb#  
    Dim num? As Integer  
    Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
        ' List of the cases  
    End Select  
    ```  
  
## Voir aussi  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md)   
 [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md)