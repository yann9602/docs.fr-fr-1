---
title: "How to: Declare Custom Events To Conserve Memory (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring events, custom"
  - "events [Visual Basic], custom"
  - "custom events"
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Declare Custom Events To Conserve Memory (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Il existe plusieurs situations où il est important pour une application d'économiser l'utilisation de sa mémoire.  Les événements personnalisés permettent à l'application d'utiliser la mémoire uniquement pour les événements qu'elle gère.  
  
 Par défaut, lorsqu'une classe déclare un événement, le compilateur alloue de la mémoire à un champ pour stocker les informations sur l'événement.  Si une classe contient plusieurs événements inutilisés, ceux\-ci utilisent de la mémoire inutilement.  
  
 Au lieu d'utiliser l'implémentation d'événements par défaut fournie par Visual Basic, vous pouvez utiliser des événements personnalisés pour gérer plus consciencieusement l'utilisation de la mémoire.  
  
## Exemple  
 Dans cet exemple, la classe utilise une instance de la classe <xref:System.ComponentModel.EventHandlerList>, qui est contenue dans le champ `Events`, pour stocker les informations sur les événements utilisés.  La classe <xref:System.ComponentModel.EventHandlerList> est une classe de liste optimisée conçue pour contenir des délégués.  
  
 Tous les événements de la classe utilisent le champ `Events` pour assurer le suivi des méthodes qui gèrent chaque événement.  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## Voir aussi  
 <xref:System.ComponentModel.EventHandlerList>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)