---
title: "Vue d&#39;ensemble du contr&#244;le LinkLabel (Windows Forms) | Microsoft Docs"
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
  - "LinkLabel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Label (contrôle Windows Forms), à propos du contrôle Label"
  - "LinkLabel (contrôle Windows Forms), à propos du contrôle LinkLabel"
  - "liens, LinkLabel (contrôle)"
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du contr&#244;le LinkLabel (Windows Forms)
Le contrôle <xref:System.Windows.Forms.LinkLabel> Windows Forms vous permet de créer des liens Web dans les applications Windows Forms.  Vous pouvez utiliser le contrôle <xref:System.Windows.Forms.LinkLabel> pour effectuer toutes les tâches que vous exécutez à l'aide du contrôle <xref:System.Windows.Forms.Label> ; vous pouvez également définir une partie du texte en tant que lien vers un fichier, un dossier ou une page Web.  
  
## Opérations possibles avec le contrôle LinkLabe  
 En plus de toutes les propriétés, méthodes et événements du contrôle <xref:System.Windows.Forms.Label>, le contrôle <xref:System.Windows.Forms.LinkLabel> possède des propriétés applicables aux liens hypertexte et aux couleurs de lien.  La propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> définit la zone de texte qui active le lien.  Les propriétés <xref:System.Windows.Forms.LinkLabel.LinkColor%2A> <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A> et  <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> définissent les couleurs du lien.  L'événement <xref:System.Windows.Forms.LinkLabel.LinkClicked> détermine l'action qui se produit lorsque le texte du lien est sélectionné.  
  
 L'utilisation la plus simple d'un contrôle <xref:System.Windows.Forms.LinkLabel> consiste à afficher un lien unique à l'aide de la propriété <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>, mais vous pouvez également afficher plusieurs liens hypertexte à l'aide de la propriété <xref:System.Windows.Forms.LinkLabel.Links%2A>.  La propriété <xref:System.Windows.Forms.LinkLabel.Links%2A> vous permet d'accéder à une collection de liens.  Vous pouvez également spécifier des données dans la propriété <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> de chaque objet <xref:System.Windows.Forms.LinkLabel.Link> individuel.  La valeur de la propriété <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> peut être utilisée pour stocker l'emplacement d'un fichier à afficher ou l'adresse d'un site Web.  
  
## Voir aussi  
 <xref:System.Windows.Forms.LinkLabel>   
 [Vue d'ensemble du contrôle Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)   
 [Comment : créer un lien vers un objet ou une page Web à l'aide du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)   
 [Comment : modifier l'apparence du contrôle LinkLabel Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)