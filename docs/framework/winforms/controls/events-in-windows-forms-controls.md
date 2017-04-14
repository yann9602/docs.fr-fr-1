---
title: "&#201;v&#233;nements dans les contr&#244;les Windows Forms | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), vue d'ensemble des événements à l'aide du code"
  - "événements (Windows Forms), contrôles personnalisés (à l'aide de code)"
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# &#201;v&#233;nements dans les contr&#244;les Windows Forms
Un contrôle Windows Forms hérite plus de soixante événements de <xref:System.Windows.Forms.Control?displayProperty=fullName>.  Ceux\-ci incluent l'événement <xref:System.Windows.Forms.Control.Paint>, qui fait qu'un contrôle est dessiné, les événements en rapport avec l'affichage d'une fenêtre, comme les événements <xref:System.Windows.Forms.Control.Resize> et <xref:System.Windows.Forms.Control.Layout>, et les événements de souris et de clavier de bas niveau.  Certains événements de niveau inférieur sont synthétisés par <xref:System.Windows.Forms.Control> en événements de sémantique, tels que <xref:System.Windows.Forms.Control.Click> et <xref:System.Windows.Forms.Control.DoubleClick>.  Pour plus d'informations sur les événements hérités, consultez <xref:System.Windows.Forms.Control>.  
  
 Si votre contrôle personnalisé doit substituer des fonctionnalités d'événements hérités, substituez la méthode `On`*NomÉvénement* au lieu d'attacher un délégué.  Si vous n'êtes pas familiarisé avec le modèle d'événement dans le .NET Framework, consultez [Raising Events from a Component](../Topic/Raising%20Events%20from%20a%20Component.md).  
  
## Voir aussi  
 [Substitution de la méthode OnPaint](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)   
 [Gestion des entrées utilisateur](../../../../docs/framework/winforms/controls/handling-user-input.md)   
 [Définition d'un événement](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [Événements](../../../../docs/standard/events/index.md)