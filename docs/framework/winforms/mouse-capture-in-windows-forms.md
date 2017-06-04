---
title: "Capture de la souris dans les Windows Forms | Microsoft Docs"
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
  - "souris, capturer"
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Capture de la souris dans les Windows Forms
La *capture de la souris* signifie qu'un contrôle prend le contrôle de toutes les entrées de la souris.  Lorsqu'un contrôle a capturé la souris, il reçoit les entrées de la souris, que le pointeur se trouve à l'intérieur de ses bordures ou pas.  
  
## Définition de la capture de la souris  
 Dans les Windows Forms, la souris est capturée par le contrôle lorsque l'utilisateur appuie sur un bouton de souris sur un contrôle, et la souris est relâchée par le contrôle lorsque l'utilisateur relâche le bouton de souris.  
  
 La propriété <xref:System.Windows.Forms.Control.Capture%2A> de la classe <xref:System.Windows.Forms.Control> spécifie si un contrôle a capturé la souris.  Pour déterminer le moment où un contrôle perd la capture de la souris, gérez l'événement <xref:System.Windows.Forms.Control.MouseCaptureChanged>.  
  
 Seule la fenêtre de premier plan peut capturer la souris.  Lorsqu'une fenêtre d'arrière\-plan tente de capturer la souris, la fenêtre reçoit uniquement des messages pour les événements de souris qui se produisent lorsque le pointeur de la souris se trouve dans la partie visible de la fenêtre.  De la même façon, même si la fenêtre de premier plan a capturé la souris, l'utilisateur peut toujours cliquer dans une autre fenêtre, la faisant ainsi passer au premier plan.  Lorsque la souris est capturée, les touches de raccourci ne fonctionnent pas.  
  
## Voir aussi  
 [Entrée de la souris dans une application Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)