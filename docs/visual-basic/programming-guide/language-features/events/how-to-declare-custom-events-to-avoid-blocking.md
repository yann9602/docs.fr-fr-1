---
title: "How to: Declare Custom Events To Avoid Blocking (Visual Basic) | Microsoft Docs"
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
  - "declaring events, custom"
  - "events [Visual Basic], custom"
  - "custom events"
ms.assetid: 998b6a90-67c5-4d2c-8b11-366d3e355505
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 12
---
# How to: Declare Custom Events To Avoid Blocking (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Il existe plusieurs cas où il est important qu'un gestionnaire d'événements ne bloque pas les gestionnaires d'événements suivants.  Les événements personnalisés permettent à l'événement d'appeler ses gestionnaires d'événements de façon asynchrone.  
  
 Par défaut, le champ du magasin de stockage pour une déclaration de l'événement est un délégué multicast qui associe en série tous les gestionnaires d'événements.  Cela signifie que si un gestionnaire met un certain temps à s'exécuter, les autres gestionnaires sont bloqués tant qu'il n'a pas terminé.  \(Les gestionnaires d'événements valides ne doivent jamais exécuter des opérations longues ou susceptibles de créer un blocage\).  
  
 Au lieu d'utiliser l'implémentation d'événements par défaut fournie par Visual Basic, vous pouvez utiliser un événement personnalisé pour exécuter les gestionnaires d'événements de façon asynchrone.  
  
## Exemple  
 Dans cet exemple, l'accesseur `AddHandler` ajoute le délégué pour chaque gestionnaire de l'événement `Click` dans un <xref:System.Collections.ArrayList> stocké dans le champ `EventHandlerList`.  
  
 Lorsque le code déclenche l'événement `Click`, l'accesseur `RaiseEvent` appelle tous les délégués de gestionnaire d'événements de façon asynchrone à l'aide de la méthode <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>.  Étant donné que cette méthode appelle chaque gestionnaire sur un thread de travail et retourne immédiatement, les gestionnaires ne peuvent pas se bloquer mutuellement.  
  
 [!code-vb[VbVbalrEvents#27](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#27)]  
  
## Voir aussi  
 <xref:System.Collections.ArrayList>   
 <xref:System.Web.Services.Protocols.LogicalMethodInfo.BeginInvoke%2A>   
 [Events](../../../../visual-basic/programming-guide/language-features/events/events.md)   
 [How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)