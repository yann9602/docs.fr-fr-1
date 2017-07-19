---
title: "Vue d&#39;ensemble du contr&#244;le Panel (Windows Forms) | Microsoft Docs"
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
  - "Panel"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "regrouper les contrôles, Panel (contrôle)"
  - "Panel (contrôle Windows Forms), à propos du contrôle Panel"
ms.assetid: b6b83636-2c39-4dad-89d6-f0fa41049a74
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Vue d&#39;ensemble du contr&#244;le Panel (Windows Forms)
Les contrôles <xref:System.Windows.Forms.Panel> Windows Forms permettent de fournir un mode de groupement identifiable pour les autres contrôles.  Les zones sont principalement utilisées pour diviser un formulaire par fonctions.  Prenons l'exemple d'un formulaire de commande spécifiant des options de courrier, telles que le nom du service de messagerie rapide à utiliser.  Pour l'utilisateur, le fait que toutes ces options soient regroupées dans un panneau est un indice visuel logique.  Au moment du design, tous les contrôles peuvent être déplacés facilement ; si vous déplacez le contrôle <xref:System.Windows.Forms.Panel>, tous les contrôles qu'il contient sont également déplacés.  Les contrôles regroupés dans un panneau sont accessibles au moyen de sa propriété <xref:System.Windows.Forms.Control.Controls%2A>.  Cette propriété retourne une collection d'instances <xref:System.Windows.Forms.Control> ; ainsi, vous devrez généralement effectuer un cast d'un contrôle récupéré de cette façon en son type spécifique.  
  
## Panel et GroupBox  
 Le contrôle <xref:System.Windows.Forms.Panel> est similaire au contrôle <xref:System.Windows.Forms.GroupBox> ; toutefois, seul le contrôle <xref:System.Windows.Forms.Panel> peut disposer de barres de défilement et seul le contrôle <xref:System.Windows.Forms.GroupBox> peut afficher une légende.  
  
## Propriétés de clé  
 Pour afficher des barres de défilement, affectez à la propriété <xref:System.Windows.Forms.ScrollableControl.AutoScroll%2A> la valeur `true`.  Vous pouvez également personnaliser l'apparence de la zone en définissant les propriétés <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A> et <xref:System.Windows.Forms.Panel.BorderStyle%2A>.  Pour plus d'informations sur les propriétés <xref:System.Windows.Forms.Control.BackColor%2A> et <xref:System.Windows.Forms.Control.BackgroundImage%2A>, consultez [Comment : définir l'arrière\-plan d'un contrôle Panel](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel.md).  La propriété <xref:System.Windows.Forms.Panel.BorderStyle%2A> détermine si la zone est entourée d'une bordure invisible \(<xref:System.Windows.Forms.BorderStyle>\), d'une simple ligne \(<xref:System.Windows.Forms.BorderStyle>\) ou d'une ligne ombrée \(<xref:System.Windows.Forms.BorderStyle>\).  
  
## Voir aussi  
 <xref:System.Windows.Forms.Panel>   
 [GroupBox, contrôle](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)   
 [Comment : grouper les contrôles avec le contrôle Panel Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)   
 [Comment : définir l'arrière\-plan d'un contrôle Panel Windows Forms à l'aide du concepteur](../../../../docs/framework/winforms/controls/how-to-set-the-background-of-a-windows-forms-panel-using-the-designer.md)