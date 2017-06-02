---
title: "Vue d&#39;ensemble du composant Timer (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Timer"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Timer (composant Windows Forms), à propos des composants Timer"
  - "minuteries, à propos des minuteries"
ms.assetid: e672c05b-a8b6-4b26-9e4d-9223aa9e3873
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du composant Timer (Windows Forms)
Le composant <xref:System.Windows.Forms.Timer> Windows Forms déclenche un événement à intervalles réguliers.  Ce composant est conçu pour un environnement Windows Forms.  Si vous avez besoin d'une minuterie \(Timer\) adaptée à un environnement serveur, consultez [Introduction to Server\-Based Timers](http://msdn.microsoft.com/fr-fr/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## Méthodes, événements et propriétés clés  
 La durée des intervalles est définie par la propriété <xref:System.Windows.Forms.Timer.Interval%2A> dont la valeur est exprimée en millisecondes.  Lorsque le composant est activé, l'événement <xref:System.Windows.Forms.Timer.Tick> est déclenché à chaque intervalle.  C'est ici que vous ajoutez le code à exécuter.  Pour plus d'informations, consultez [Comment : exécuter des procédures à intervalles définis à l'aide du composant Timer Windows Forms](../../../../docs/framework/winforms/controls/run-procedures-at-set-intervals-with-wf-timer-component.md).  Les méthodes clés du composant <xref:System.Windows.Forms.Timer> sont <xref:System.Windows.Forms.Timer.Start%2A> et <xref:System.Windows.Forms.Timer.Stop%2A>, qui activent et désactivent la minuterie.  Lorsque la minuterie est désactivée, elle est réinitialisée ; il est en effet impossible de suspendre un composant <xref:System.Windows.Forms.Timer>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Timer>   
 [Timer, composant](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Restrictions relatives à la propriété Interval du composant Timer Windows Forms](../../../../docs/framework/winforms/controls/limitations-of-the-timer-component-interval-property.md)