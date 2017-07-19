---
title: "Comment&#160;: ancrer des contr&#244;les aux Windows Forms | Microsoft Docs"
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
  - "Anchor (propriété), activer les formulaires redimensionnables"
  - "contrôles (Windows Forms), ancrer"
  - "contrôles (Windows Forms), positionner"
  - "formulaires, redimensionner"
  - "redimensionner les formulaires"
  - "résolution d'écran et affichage de contrôles"
  - "contrôles Windows Forms, résolutions d'écran"
  - "contrôles Windows Forms, taille"
  - "Windows Forms, redimensionner"
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# Comment&#160;: ancrer des contr&#244;les aux Windows Forms
Si vous créez un formulaire que l'utilisateur peut redimensionner au moment de l'exécution, les contrôles qu'il contient doivent adopter la taille et la position adéquates.  Pour redimensionner dynamiquement les contrôles dans le formulaire, vous pouvez utiliser la propriété <xref:System.Windows.Forms.Control.Anchor%2A> des contrôles Windows Forms.  La propriété <xref:System.Windows.Forms.Control.Anchor%2A> détermine la position d'ancrage d'un contrôle.  Lorsqu'un contrôle est ancré à un formulaire et que celui\-ci est redimensionné, la distance entre le contrôle et les positions d'ancrage est préservée.  Par exemple, si un contrôle <xref:System.Windows.Forms.TextBox> est ancré dynamiquement aux bords gauche, droit et inférieur du formulaire, il est redimensionné horizontalement lorsque le formulaire change de taille, de<xref:System.Windows.Forms.TextBox> sorte qu'il reste toujours à la même distance des bords droit et gauche du formulaire.  En outre, le contrôle se positionne verticalement de façon à être toujours placé à la même distance du bord inférieur du formulaire.  Si un contrôle n'est pas ancré dynamiquement, lorsque le formulaire est redimensionné, sa position par rapport aux bords du formulaire se trouve modifiée.  
  
 La propriété <xref:System.Windows.Forms.Control.Anchor%2A> interagit avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.  Pour plus d'informations, consultez [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ancrer dynamiquement un contrôle à un formulaire  
  
1.  Sélectionnez le contrôle à ancrer dynamiquement.  
  
    > [!NOTE]
    >  Il est possible d'ancrer dynamiquement plusieurs contrôles simultanément en appuyant sur la touche CTRL, en cliquant sur chaque contrôle requis pour le sélectionner, puis en suivant la suite de la procédure.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur la flèche située à droite de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  
  
     Un éditeur qui a la forme d'une croix s'affiche.  
  
3.  Pour définir une ancre dynamique, cliquez sur la branche droite, gauche, haute ou basse de la croix.  
  
     Les contrôles sont ancrés par défaut aux bords supérieur et gauche.  
  
4.  Pour annuler l'ancrage dynamique d'un contrôle, cliquez sur la branche de la croix correspondant à l'ancrage que vous voulez supprimer.  
  
5.  Pour fermer l'éditeur de propriétés <xref:System.Windows.Forms.Control.Anchor%2A>, cliquez de nouveau sur le nom de la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  
  
 Lorsque votre formulaire est affiché au moment de l'exécution, le contrôle est redimensionné de façon à rester à la même distance du bord du formulaire.  La distance par rapport au bord d'ancrage reste identique à celle qui a été fixée lors du positionnement du contrôle dans le Concepteur Windows Forms.  
  
> [!NOTE]
>  La hauteur de certains contrôles, par exemple <xref:System.Windows.Forms.ComboBox>, est limitée.  L'ancrage dynamique d'un contrôle au bord inférieur de son formulaire ou conteneur ne peut forcer un dépassement de sa limite en hauteur.  
  
 Les contrôles hérités doivent présenter l'accès `Protected` pour pouvoir être ancrés.  Pour modifier le niveau d'accès d'un contrôle, définissez sa propriété `Modifiers` dans la fenêtre **Propriétés**.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)