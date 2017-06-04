---
title: "Restrictions relatives &#224; la propri&#233;t&#233; Interval du composant Timer Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Interval (propriété), limitations"
  - "Timer (composant Windows Forms), limitations de la propriété Interval"
  - "minuteries, intervalles entre les événements"
  - "minuteries, reposant sur Windows"
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Restrictions relatives &#224; la propri&#233;t&#233; Interval du composant Timer Windows Forms
Le composant <xref:System.Windows.Forms.Timer> Windows Forms possède une propriété <xref:System.Windows.Forms.Timer.Interval%2A> qui spécifie le nombre de millisecondes qui doivent s'écouler entre deux événements de minuterie \(Timer\).  Sauf si le composant est désactivé, une minuterie \(Timer\) continue de recevoir l'événement <xref:System.Windows.Forms.Timer.Tick> à intervalles à peu près constants.  
  
 Ce composant est conçu pour un environnement Windows Forms.  Si vous avez besoin d'une minuterie \(Timer\) adaptée à un environnement serveur, consultez [Introduction to Server\-Based Timers](http://msdn.microsoft.com/fr-fr/adc0bc0a-a519-4812-bafc-fb9d1a5801fc).  
  
## Propriété Interval  
 La propriété <xref:System.Windows.Forms.Timer.Interval%2A> impose quelques restrictions dont vous devez tenir compte lorsque vous programmez un composant <xref:System.Windows.Forms.Timer> :  
  
-   Si votre application ou une autre impose une demande importante au système \(boucles longues, calculs complexes, accès intensifs à un périphérique, un réseau ou un port, par exemple\), elle peut ne pas obtenir des événements de minuterie \(Timer\) aussi souvent que spécifié par la propriété <xref:System.Windows.Forms.Timer.Interval%2A>.  
  
-   Il n'est pas garanti que l'intervalle s'écoule dans le temps exact.  Pour que sa précision soit garantie, la minuterie \(Timer\) doit pouvoir au besoin consulter l'horloge système plutôt que de suivre en interne le temps écoulé.  
  
-   La précision de la propriété <xref:System.Windows.Forms.Timer.Interval%2A> est exprimée en millisecondes.  Certains ordinateurs fournissent un compteur haute résolution qui a une résolution supérieure aux millisecondes.  La disponibilité d'un tel compteur dépend du processeur de votre ordinateur.  Pour plus d'informations, consultez l'article 172338, "How To Use QueryPerformanceCounter to Time Code" \(Comment Utiliser QueryPerformanceCounter sur le code temporel\) dans la Base de connaissances Microsoft à l'adresse http:\/\/www.microsoft.com\/france\/support.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Timer>   
 [Timer, composant](../../../../docs/framework/winforms/controls/timer-component-windows-forms.md)   
 [Vue d'ensemble du composant Timer](../../../../docs/framework/winforms/controls/timer-component-overview-windows-forms.md)