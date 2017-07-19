---
title: "Vue d&#39;ensemble du contr&#244;le TrackBar (Windows Forms) | Microsoft Docs"
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
  - "TrackBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles Slider, à propos des contrôles Slider"
  - "contrôles Slider, à propos des contrôles Slider"
  - "TrackBar (contrôle Windows Forms), à propos du contrôle TrackBar"
ms.assetid: 95910ecb-8a4c-4776-89fa-206c89ed6973
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Vue d&#39;ensemble du contr&#244;le TrackBar (Windows Forms)
Le contrôle <xref:System.Windows.Forms.TrackBar> Windows Forms \(parfois appelé « contrôle Slider »\) permet de naviguer dans un gros volume d'informations ou d'ajuster visuellement un paramètre numérique.  Le contrôle <xref:System.Windows.Forms.TrackBar> est également constitué de deux parties : le curseur \(de défilement\) et les graduations.  Le curseur de défilement peut être ajusté.  Sa position correspond à la propriété <xref:System.Windows.Forms.TrackBar.Value%2A>.  Les graduations sont des indicateurs visuels. Elles sont placées à intervalles réguliers.  La barre de suivi se déplace selon les incréments que vous avez spécifiés. Elle peut être alignée horizontalement ou verticalement.  Vous pouvez par exemple recourir à la barre de suivi pour contrôler la fréquence de clignotement du curseur ou la vitesse de la souris dans le système.  
  
## Propriétés de clé  
 Les propriétés de clé du contrôle <xref:System.Windows.Forms.TrackBar> sont <xref:System.Windows.Forms.TrackBar.Value%2A>, <xref:System.Windows.Forms.TrackBar.TickFrequency%2A>, <xref:System.Windows.Forms.TrackBar.Minimum%2A> et <xref:System.Windows.Forms.TrackBar.Maximum%2A>.  <xref:System.Windows.Forms.TrackBar.TickFrequency%2A> est l'espacement des battements.  <xref:System.Windows.Forms.TrackBar.Minimum%2A> et <xref:System.Windows.Forms.TrackBar.Maximum%2A> sont les valeurs minimale et maximale pouvant être représentées sur la barre de suivi.  
  
 <xref:System.Windows.Forms.TrackBar.SmallChange%2A> et <xref:System.Windows.Forms.TrackBar.LargeChange%2A> sont deux autres propriétés importantes.  La valeur de la propriété <xref:System.Windows.Forms.TrackBar.SmallChange%2A> détermine le nombre de positions dont le curseur se déplace lorsque l'utilisateur appuie sur la touche GAUCHE ou DROITE.  La valeur de la propriété <xref:System.Windows.Forms.TrackBar.LargeChange%2A> détermine le nombre de positions dont le curseur se déplace lorsque l'utilisateur appuie sur la touche HAUT ou BAS ou clique sur la barre de suivi d'un côté ou de l'autre du curseur.  
  
## Voir aussi  
 <xref:System.Windows.Forms.TrackBar>   
 [TrackBar, contrôle](../../../../docs/framework/winforms/controls/trackbar-control-windows-forms.md)