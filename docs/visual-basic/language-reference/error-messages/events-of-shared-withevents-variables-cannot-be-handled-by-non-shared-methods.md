---
title: "Events of shared WithEvents variables cannot be handled by non-shared methods | Microsoft Docs"
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
  - "bc30594"
  - "vbc30594"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30594"
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Events of shared WithEvents variables cannot be handled by non-shared methods
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Une variable déclarée avec le modificateur `Shared` est une variable partagée.  Une variable partagée identifie exactement un seul emplacement de stockage.  Une variable déclarée avec le modificateur `WithEvents` garantit que le type auquel appartient la variable gère l'ensemble d'événements déclenchés par la variable.  Quand une valeur est assignée à la variable, la propriété créée par la déclaration `WithEvents` déconnecte tout gestionnaire d'événements existant et raccorde le nouveau gestionnaire d'événements via la méthode `Add`.  
  
 **ID d'erreur :** BC30594  
  
### Pour corriger cette erreur  
  
-   Déclarez votre gestionnaire d'événements comme `Shared`.  
  
## Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)