---
title: "Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30941"
  - "vbc30941"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30941"
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une définition de structure n'inclut pas de variables non partagées ou d'événements non personnalisés non partagés.  
  
 Chaque structure doit avoir une variable ou un événement qui s'applique à chaque instance spécifique \(non partagée\) et non à toutes les instances collectivement \([Shared](../../../visual-basic/language-reference/modifiers/shared.md)\).  Les constantes, propriétés et procédures non partagées ne répondent pas à cette condition.  Par ailleurs, s'il n'y a aucune variable non partagée et qu'un seul événement non partagé, cet événement ne peut pas être un événement `Custom`.  
  
 **ID d'erreur :** BC30941  
  
### Pour corriger cette erreur  
  
-   Définissez au moins une variable ou un événement qui n'est pas `Shared`.  Si vous ne définissez qu'un événement, il doit être non personnalisé et non partagé.  
  
## Voir aussi  
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)