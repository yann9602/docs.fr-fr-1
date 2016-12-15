---
title: "&#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible | Microsoft Docs"
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
  - "vbc31102"
  - "bc31102"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31102"
ms.assetid: 6f7b31b7-3656-4ae1-8851-90f5f4c6950a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Set&#39; accessor of property &#39;&lt;propertyname&gt;&#39; is not accessible
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une instruction essaie d'enregistrer la valeur d'une propriété alors qu'elle n'a pas accès à la procédure `Set` de la propriété.  
  
 Si l'[Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) est marquée avec un niveau d'accès plus restrictif que son [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md), la définition de la valeur de la propriété peut échouer dans les cas suivants :  
  
-   L'instruction `Set` est marquée [Private](../../../visual-basic/language-reference/modifiers/private.md) et le code appelant est situé à l'extérieur de la classe ou la structure dans laquelle la propriété est définie.  
  
-   L'instruction `Set` est marquée [Protected](../../../visual-basic/language-reference/modifiers/protected.md) et le code appelant ne figure pas dans la classe ou la structure dans laquelle la propriété est définie, ni dans une classe dérivée.  
  
-   L'instruction `Set` est marquée [Friend](../../../visual-basic/language-reference/modifiers/friend.md) et le code appelant ne figure pas dans l'assembly dans lequel la propriété est définie.  
  
 **ID d'erreur :** BC31102  
  
### Pour corriger cette erreur  
  
-   Si vous avez le contrôle du code source qui définit la propriété, vous devez déclarer la procédure `Set` avec le même niveau d'accès que la propriété proprement dite.  
  
-   Si vous n'avez pas le contrôle du code source qui définit la propriété, ou si vous devez limiter davantage le niveau d'accès de la procédure `Set` que celui de la propriété proprement dite, essayez de déplacer l'instruction qui définit la valeur de la propriété vers une zone de code qui offre un meilleur accès à la propriété.  
  
## Voir aussi  
 [Procédures de propriété](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [How to: Declare a Property with Mixed Access Levels](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)