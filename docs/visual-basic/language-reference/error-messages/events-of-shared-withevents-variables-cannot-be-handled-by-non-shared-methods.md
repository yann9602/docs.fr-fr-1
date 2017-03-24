---
title: "Events of shared WithEvents variables cannot be handled by non-shared methods | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30594"
  - "vbc30594"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30594"
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Events of shared WithEvents variables cannot be handled by non-shared methods
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une variable déclarée avec le modificateur `Shared` est une variable partagée.  Une variable partagée identifie exactement un seul emplacement de stockage.  Une variable déclarée avec le modificateur `WithEvents` garantit que le type auquel appartient la variable gère l'ensemble d'événements déclenchés par la variable.  Quand une valeur est assignée à la variable, la propriété créée par la déclaration `WithEvents` déconnecte tout gestionnaire d'événements existant et raccorde le nouveau gestionnaire d'événements via la méthode `Add`.  
  
 **ID d'erreur :** BC30594  
  
### Pour corriger cette erreur  
  
-   Déclarez votre gestionnaire d'événements comme `Shared`.  
  
## Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)