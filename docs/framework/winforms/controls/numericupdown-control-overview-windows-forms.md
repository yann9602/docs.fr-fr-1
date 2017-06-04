---
title: "Vue d&#39;ensemble du contr&#244;le NumericUpDown (Windows Forms) | Microsoft Docs"
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
  - "NumericUpDown"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôle toupie numérique, Windows Forms"
  - "NumericUpDown (contrôle Windows Forms), à propos du contrôle NumericUpDown"
  - "contrôle toupie, Windows Forms"
ms.assetid: cff3cf30-4d46-4381-87df-37bfe83c71c5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Vue d&#39;ensemble du contr&#244;le NumericUpDown (Windows Forms)
Le contrôle Windows Forms <xref:System.Windows.Forms.NumericUpDown> se présente comme une zone de texte à laquelle sont associées deux flèches permettant le déplacement vers le haut et vers le bas dans une liste.  Il affiche et définit une valeur numérique provenant d'une liste d'options de valeurs numériques fixes.  L'utilisateur peut augmenter et diminuer cette valeur numérique en cliquant sur les flèches Haut et Bas, en appuyant sur les touches HAUT et BAS ou en tapant le nombre de son choix dans la zone de texte du contrôle.  La touche HAUT rapproche ce nombre de la valeur maximale ; à l'inverse, la touche BAS le rapproche de la valeur minimale.  
  
 À cause de ses fonctionnalités polyvalentes, ce contrôle est un choix évident, par exemple, si vous souhaitez créer un contrôle de volume pour une application du lecteur de la musique.  Le contrôle <xref:System.Windows.Forms.NumericUpDown> est utilisé dans beaucoup d'applications du Panneau de configuration Windows.  
  
## Propriétés et méthodes principales  
 Les nombres affichés dans la zone de texte du contrôle peuvent être dans divers formats, y compris hexadécimal.  Pour plus d'informations, consultez [Comment : définir le format du contrôle NumericUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md).  Les propriétés clés du contrôle sont <xref:System.Windows.Forms.NumericUpDown.Value%2A>, <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> \(valeur par défaut 100\), <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> \(valeur par défaut 0\) et <xref:System.Windows.Forms.NumericUpDown.Increment%2A> \(valeur par défaut 1\).  La propriété <xref:System.Windows.Forms.NumericUpDown.Value%2A> définit le nombre actuellement sélectionné dans le contrôle.  La propriété <xref:System.Windows.Forms.NumericUpDown.Increment%2A> définit l'écart duquel le nombre est augmenté ou diminué lorsque l'utilisateur clique sur la flèche Haut ou Bas.  Lorsque le focus quitte le contrôle, toute valeur entrée est validée par rapport aux valeurs numériques maximale et minimale.  Vous pouvez augmenter la vitesse des déplacements du contrôle à travers les nombres, lorsque l'utilisateur appuie continuellement sur la flèche haut ou flèche, avec la propriété <xref:System.Windows.Forms.NumericUpDown.Accelerations%2A>.  Les principales méthodes du contrôle sont <xref:System.Windows.Forms.NumericUpDown.UpButton%2A> et <xref:System.Windows.Forms.NumericUpDown.DownButton%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Forms.NumericUpDown>   
 [NumericUpDown, contrôle](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)   
 [Comment : définir le format du contrôle NumericUpDown Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-format-for-the-windows-forms-numericupdown-control.md)   
 [TextBox, contrôle](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)