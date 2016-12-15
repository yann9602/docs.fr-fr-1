---
title: "Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39; | Microsoft Docs"
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
  - "vbc36532"
  - "bc36532"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36532"
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une expression lambda a été assignée à un délégué qui a une signature incompatible.  Par exemple, dans le code suivant, le délégué `Del` a deux paramètres entiers.  
  
```vb#  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 L'erreur est déclenchée si une expression lambda avec un argument est déclarée comme type `Del` :  
  
```vb#  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID d'erreur :** BC36532  
  
### Pour corriger cette erreur  
  
-   Ajustez la définition de délégué ou l'expression lambda assignée afin que les signatures soient compatibles.  
  
## Voir aussi  
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)