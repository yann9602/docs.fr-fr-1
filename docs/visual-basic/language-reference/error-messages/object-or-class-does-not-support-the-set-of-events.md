---
title: "Object or class does not support the set of events | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID459"
dev_langs: 
  - "VB"
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Object or class does not support the set of events
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous avez essayé d'utiliser une variable `WithEvents` avec un composant qui ne peut pas fonctionner comme une source d'événement pour le jeu d'événements spécifié.  Par exemple, vous souhaitiez recevoir les événements d'un objet, puis créer un autre objet qui `Implements` le premier objet.  Même si vous pensez pouvoir recevoir les événements de l'objet implémenté, ce n'est pas toujours le cas.  `Implements` implémente seulement une interface pour les méthodes et les propriétés.  `WithEvents` n'est pas pris en charge pour les `UserControls` privés, parce que l'information de type nécessaires pour déclencher l'`ObjectEvent` n'est pas disponible au moment de l'exécution.  
  
### Pour corriger cette erreur  
  
1.  Vous ne pouvez pas recevoir d'événements pour un composant qui ne fournit pas d'événements.  
  
## Voir aussi  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)   
 [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md)