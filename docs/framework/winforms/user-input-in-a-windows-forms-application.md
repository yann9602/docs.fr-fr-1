---
title: "Entr&#233;e d&#39;utilisateur dans une application Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Forms, entrée d'utilisateur"
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Entr&#233;e d&#39;utilisateur dans une application Windows Forms
Dans Windows Forms, l'entrée d'utilisateur est envoyée aux applications sous la forme de messages Windows.  Une série de méthodes substituables traite ces messages au niveau de l'application, du formulaire et du contrôle.  Lorsque ces méthodes reçoivent les messages de clavier et de souris, ils déclenchent des événements qui peuvent être gérés pour obtenir des informations à propos des entrées de souris ou de clavier.  Dans beaucoup de cas, les applications Windows Forms seront en mesure de traiter simplement toutes les entrées d'utilisateur en gérant ces événements.  Dans d'autres cas, une application peut devoir se substituer à l'une des méthodes qui traitent les messages afin d'intercepter un message particulier avant qu'il ne soit reçu par l'application, le formulaire ou le contrôle.  
  
## Événements de souris et de clavier  
 Tous les contrôles Windows Forms héritent d'un jeu d'événements en rapport avec les entrées de souris et de clavier.  Par exemple, un contrôle peut gérer l'événement <xref:System.Windows.Forms.Control.KeyPress> afin de déterminer le code de caractère d'une touche qui a été enfoncée, ou un contrôle peut gérer l'événement <xref:System.Windows.Forms.Control.MouseClick> pour déterminer l'emplacement d'un clic de souris.  Pour plus d'informations sur les événements de clavier et de souris, consultez [Utilisation des événements du clavier](../../../docs/framework/winforms/using-keyboard-events.md) et [Événements liés à la souris dans les Windows Forms](../../../docs/framework/winforms/mouse-events-in-windows-forms.md).  
  
## Méthodes qui traitent les messages des entrées d'utilisateur  
 Les formulaires et les contrôles ont accès à l'interface <xref:System.Windows.Forms.IMessageFilter> et à un jeu de méthodes substituables qui traitent les messages Windows à différents points dans la file d'attente de messages.  Ces méthodes ont toutes un paramètre <xref:System.Windows.Forms.Message>, qui encapsule les détails de bas niveau des messages Windows.  Vous pouvez implémenter ou substituer ces méthodes pour examiner le message, puis consommer le message ou le transmettre au consommateur suivant dans la file d'attente de messages.  Le tableau suivant présente les méthodes qui traitent tous les messages Windows dans Windows Forms.  
  
|Méthode|Remarques|  
|-------------|---------------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|Cette méthode intercepte les messages Windows mis en file d'attente \(ou publiés\) au niveau de l'application.|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Cette méthode intercepte les messages Windows au niveau du formulaire et du contrôle avant qu'ils aient été traités.|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Cette méthode traite des messages Windows au niveau du formulaire et du contrôle.|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Cette méthode exécute le traitement par défaut des messages Windows au niveau du formulaire et du contrôle.  Cela assure le fonctionnement minimal d'une fenêtre.|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|Cette méthode intercepte les messages au niveau du formulaire et du contrôle une fois qu'ils ont été traités.  Le bit de style <xref:System.Windows.Forms.ControlStyles> doit être défini pour que cette méthode puisse être appelée.|  
  
 Les messages de la souris et du clavier sont également traités par un jeu supplémentaire de méthodes substituables qui sont spécifiques à ces types de messages.  Pour plus d'informations, consultez [Fonctionnement de l'entrée au clavier](../../../docs/framework/winforms/how-keyboard-input-works.md) et [Fonctionnement des entrées de la souris dans les Windows Forms](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md).  
  
## Voir aussi  
 [Entrées d'utilisateur dans les Windows Forms](../../../docs/framework/winforms/user-input-in-windows-forms.md)   
 [Entrée au clavier dans une application Windows Forms](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)