---
title: "Troubleshooting Inherited Event Handlers in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "troubleshooting events"
  - "inherited events"
  - "troubleshooting Visual Basic, event handlers"
  - "event handling, troubleshooting"
  - "event handlers, troubleshooting"
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Troubleshooting Inherited Event Handlers in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cette rubrique décrit les problèmes courants relatifs aux gestionnaires d'événements dans les composants hérités.  
  
## Procédures  
  
#### Le code d'un gestionnaire d'événements s'exécute deux fois pour chaque appel  
  
-   Un gestionnaire d'événements hérité ne doit pas inclure de clause [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md).  La méthode de la classe de base est déjà associée à l'événement et se déclenche en conséquence.  Supprimez la clause `Handles` de la méthode héritée.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#32)]  
  
-   Si la méthode héritée ne comporte aucun mot clé `Handles`, vérifiez que votre code ne contient aucune [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) supplémentaire, ni aucune méthode susceptible de gérer le même événement.  
  
## Voir aussi  
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)