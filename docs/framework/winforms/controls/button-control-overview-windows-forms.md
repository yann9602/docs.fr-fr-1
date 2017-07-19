---
title: "Vue d&#39;ensemble du contr&#244;le Button (Windows&#160;Forms) | Microsoft Docs"
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
  - "Button"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "bouton (contrôle Windows Forms), à propos du contrôle Button"
  - "boutons, à propos des boutons"
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Vue d&#39;ensemble du contr&#244;le Button (Windows&#160;Forms)
Le contrôle <xref:System.Windows.Forms.Button> Windows Forms permet à l'utilisateur d'effectuer une action en cliquant dessus.  Lorsque l'utilisateur clique sur le bouton, ce dernier réagit comme s'il était enfoncé puis relâché.  Chaque fois qu'un utilisateur clique sur un bouton, le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> est appelé.  Vous devez donc placer du code dans ce gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> afin d'exécuter l'action de votre choix.  
  
 Le texte qui s'affiche sur le bouton est contenu dans la propriété <xref:System.Windows.Forms.Control.Text%2A>.  Si ce texte excède la largeur du bouton, il passe sur la ligne suivante.  Toutefois, il est tronqué si sa hauteur totale dépasse la capacité du contrôle.  Pour plus d'informations, consultez [Comment : définir le texte affiché par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).  La propriété <xref:System.Windows.Forms.Control.Text%2A> peut contenir une touche d'accès rapide, laquelle permet à l'utilisateur de « cliquer » sur le contrôle en appuyant sur cette touche tout en maintenant la touche ALT enfoncée.  Pour plus d'informations, consultez [Comment : créer des touches d'accès rapide pour des contrôles Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  L'apparence du texte est déterminée par les propriétés <xref:System.Windows.Forms.Control.Font%2A> et <xref:System.Windows.Forms.ButtonBase.TextAlign%2A>.  
  
 Le contrôle <xref:System.Windows.Forms.Button> peut également afficher des images à l'aide des propriétés <xref:System.Windows.Forms.ButtonBase.Image%2A> et <xref:System.Windows.Forms.ButtonBase.ImageList%2A>.  Pour plus d'informations, consultez [Comment : définir l'image affichée par un contrôle Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## Voir aussi  
 <xref:System.Windows.Forms.Button>   
 [Comment : répondre à un clic du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)   
 [Méthodes de sélection du contrôle Button Windows Forms](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)   
 [Comment : désigner un bouton Windows Forms comme bouton Accepter à l'aide du concepteur](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)   
 [Comment : désigner un bouton Windows Forms comme bouton Annuler à l'aide du concepteur](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)   
 [Button, contrôle](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)