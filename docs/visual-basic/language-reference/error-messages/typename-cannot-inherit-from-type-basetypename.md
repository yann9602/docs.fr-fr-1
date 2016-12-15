---
title: "&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly | Microsoft Docs"
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
  - "vbc30910"
  - "bc30910"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30910"
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une classe ou une interface hérite d'une classe ou d'une interface de base qui présente un niveau d'accès moins restrictif.  
  
 Par exemple, une interface `Public` hérite d'une interface `Friend`, ou une classe `Protected` hérite d'une classe `Private`.  Cela expose la classe ou l'interface de base à un accès au\-delà du niveau prévu.  
  
 **ID d'erreur :** BC30910  
  
### Pour corriger cette erreur  
  
-   Modifiez le niveau d'accès de la classe ou de l'interface dérivée pour qu'il soit au moins aussi restrictif que celui de la classe ou de l'interface de base.  
  
     ou  
  
-   Si un niveau d'accès moins restrictif doit être utilisé, supprimez l'instruction `Inherits`.  Vous ne pouvez pas hériter d'une classe ou d'une interface de base plus restreinte.  
  
## Voir aussi  
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)