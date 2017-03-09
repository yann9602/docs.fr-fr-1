---
title: "&#201;v&#233;nements (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes (C#), événements"
  - "langage C#, événements"
  - "événements (C#)"
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# &#201;v&#233;nements (Guide de programmation C#)
Les événements permettent à une [classe](../../../csharp/language-reference/keywords/class.md) ou à un objet de notifier d’autres classes ou objets quand quelque chose de significatif se produit. La classe qui envoie \(ou *déclenche*\) l’événement est appelée *publieur* et les classes qui reçoivent \(ou *gèrent*\) l’événement sont appelées *abonnés*.  
  
 Dans une application C\# Windows Forms ou web classique, vous vous abonnez à des événements déclenchés par des contrôles, comme des boutons et des zones de liste. Vous pouvez utiliser l’IDE [!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] pour parcourir les événements publiés par un contrôle et sélectionner ceux que vous voulez gérer. L’IDE ajoute automatiquement une méthode de gestionnaire d’événements vide et le code pour vous abonner à l’événement. Pour plus d'informations, consultez [Comment : s'abonner et annuler l'abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## Vue d'ensemble des événements  
 Les événements ont les propriétés suivantes :  
  
-   Le publieur détermine quand un événement est déclenché ; les abonnés déterminent l’action entreprise en réponse à l’événement.  
  
-   Un événement peut avoir plusieurs abonnés. Un abonné peut gérer plusieurs événements provenant de plusieurs publieurs.  
  
-   Les événements qui n’ont aucun abonné ne sont jamais déclenchés.  
  
-   Les événements sont généralement utilisés pour signaler des actions de l’utilisateur, comme les clics de bouton ou les sélections de menu dans les interfaces utilisateur graphiques.  
  
-   Quand un événement a plusieurs abonnés, les gestionnaires d’événements sont appelées de façon synchrone quand un événement est déclenché. Pour appeler des événements de façon asynchrone, consultez [Calling Synchronous Methods Asynchronously](../Topic/Calling%20Synchronous%20Methods%20Asynchronously.md).  
  
-   Dans la bibliothèque de classes [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] , les événements sont basés sur le délégué <xref:System.EventHandler> et la classe de base <xref:System.EventArgs>.  
  
## Rubriques connexes  
 Pour plus d'informations, voir :  
  
-   [Comment : s'abonner et annuler l'abonnement à des événements](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [Comment : publier des événements conformes aux indications du .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [Comment : déclencher les événements de la classe de base dans les classes dérivées](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [Comment : implémenter des événements d'interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [Synchronisation des threads](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [Comment : utiliser un dictionnaire pour stocker des instances d'événements](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [Comment : implémenter des accesseurs d'événement personnalisés](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Chapitres proposés  
 [Delegates, Events, and Lambda Expressions](http://go.microsoft.com/fwlink/?LinkId=195395) \(Délégués, événements et expressions lambda\) dans [C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers](http://go.microsoft.com/fwlink/?LinkId=195369)  
  
 [Delegates and Events](http://go.microsoft.com/fwlink/?LinkId=195418) dans [Learning C\# 3.0: Master the fundamentals of C\# 3.0](http://go.microsoft.com/fwlink/?LinkId=195412)  
  
## Voir aussi  
 <xref:System.EventHandler>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Création de gestionnaires d'événements dans les Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../Topic/Multithreaded%20Programming%20with%20the%20Event-based%20Asynchronous%20Pattern.md)