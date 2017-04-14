---
title: "Vue d&#39;ensemble du contr&#244;le RadioButton (Windows Forms) | Microsoft Docs"
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
  - "RadioButton"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "cases d'option, à propos des cases d'option"
  - "cases d'option, déterminer l'état"
  - "RadioButton (contrôle Windows Forms), à propos du contrôle RadioButton"
  - "RadioButton (contrôle Windows Forms), déterminer l'état"
ms.assetid: cd11f0c2-d098-4022-adf9-1455bc166a13
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du contr&#244;le RadioButton (Windows Forms)
Le contrôle <xref:System.Windows.Forms.RadioButton> Windows Forms présente à l'utilisateur plusieurs choix mutuellement exclusifs.  Les cases d'option et les cases à cocher ont à première vue un fonctionnement similaire, mais il existe entre elles une différence importante ; en effet, lorsqu'un utilisateur sélectionne dans un groupe une case d'option, les autres ne peuvent plus être sélectionnées.  À l'inverse, l'utilisateur peut activer autant de cases à cocher qu'il le souhaite.  La présence d'un groupe de cases d'option indique à l'utilisateur qu'il ne peut faire qu'un seul choix parmi les différentes options qui lui sont proposées.  
  
## Utilisation du contrôle  
 Lorsqu'un utilisateur clique sur un contrôle <xref:System.Windows.Forms.RadioButton>, sa propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> prend la valeur `true` et le gestionnaire de l'événement <xref:System.Windows.Forms.Control.Click> est appelé.  L'événement <xref:System.Windows.Forms.RadioButton.CheckedChanged> est déclenché lorsque la valeur de la propriété <xref:System.Windows.Forms.RadioButton.Checked%2A> change.  Si la propriété <xref:System.Windows.Forms.RadioButton.AutoCheck%2A> a la valeur `true` \(valeur par défaut\), la sélection de la case d'option a pour effet de désactiver automatiquement toutes les autres cases du groupe.  En général, cette propriété ne prend la valeur `false` que lorsqu'un code de validation est utilisé pour garantir que la case d'option sélectionnée est une option autorisée.  Le texte affiché dans le contrôle est défini à l'aide de la propriété <xref:System.Windows.Forms.Control.Text%2A>, laquelle peut contenir des raccourcis de touches d'accès rapide.  Une touche d'accès rapide permet à l'utilisateur de « cliquer » sur l'autre contrôle en appuyant sur cette touche tout en maintenant la touche ALT enfoncée.  Pour plus d'informations, consultez [Comment : créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) et [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  
  
 Si la propriété <xref:System.Windows.Forms.RadioButton.Appearance%2A> est définie avec la valeur <xref:System.Windows.Forms.Appearance>, le contrôle <xref:System.Windows.Forms.RadioButton> prend l'aspect d'un bouton de commande enfoncé lorsqu'il est sélectionné.  Les cases d'option conservent également des images à l'aide des propriétés <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A>.  Pour plus d'informations, consultez [Comment : définir l'image affichée par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.RadioButton>   
 [Vue d'ensemble du contrôle Panel](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle GroupBox](../../../../docs/framework/winforms/controls/groupbox-control-overview-windows-forms.md)   
 [Vue d'ensemble du contrôle CheckBox](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)   
 [Comment : créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)   
 [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)   
 [Comment : grouper des contrôles RadioButton Windows Forms en un ensemble fonctionnant indépendamment](../../../../docs/framework/winforms/controls/how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md)   
 [RadioButton, contrôle](../../../../docs/framework/winforms/controls/radiobutton-control-windows-forms.md)