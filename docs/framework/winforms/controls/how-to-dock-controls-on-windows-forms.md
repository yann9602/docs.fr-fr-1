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
  - "contrôles (Windows Forms), fixer"
  - "Dock (propriété)"
  - "applications de style Explorateur, créer"
  - "contrôles Windows Forms, remplir une zone cliente"
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: ancrer des contr&#244;les aux Windows Forms
Vous pouvez ancrer des contrôles aux bords de votre formulaire ou demander qu'ils remplissent leur conteneur \(qui peut être un formulaire ou un contrôle conteneur\).  Par exemple, l'Explorateur Windows ancre son contrôle <xref:System.Windows.Forms.TreeView> au côté gauche de la fenêtre et son contrôle <xref:System.Windows.Forms.ListView> au côté droit.  La propriété <xref:System.Windows.Forms.Control.Dock%2A> permet de définir le mode d'ancrage de tous les contrôles Windows Forms visibles.  
  
> [!NOTE]
>  Les contrôles sont ancrés dans l'ordre de plan inverse.  
  
 La propriété <xref:System.Windows.Forms.Control.Dock%2A> interagit avec la propriété <xref:System.Windows.Forms.Control.AutoSize%2A>.  Pour plus d'informations, consultez [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
### Pour ancrer un contrôle  
  
1.  Sélectionnez le contrôle à ancrer.  
  
2.  Dans la fenêtre Propriétés, cliquez sur la flèche à droite de la propriété <xref:System.Windows.Forms.Control.Dock%2A>.  
  
     Un éditeur dans lequel est affichée une série de zones représentant les bords et la partie centrale du formulaire apparaît.  
  
3.  Cliquez sur le bouton représentant le bord du formulaire auquel vous voulez ancrer le contrôle.  Pour remplir le formulaire du contrôle ou le contrôle conteneur, cliquez sur la zone centrale.  Cliquez sur **\(Aucun\)** pour désactiver l'ancrage.  
  
     Le contrôle est automatiquement redimensionné par rapport aux limites du bord d'ancrage.  
  
    > [!NOTE]
    >  Les contrôles hérités doivent présenter l'accès `Protected` pour pouvoir être ancrés.  Pour modifier le niveau d'accès d'un contrôle, définissez sa propriété **Modifier** dans la fenêtre Propriétés.  
  
## Voir aussi  
 [contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)   
 [Création d'étiquettes et de raccourcis pour les contrôles Windows Forms](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [Contrôles à utiliser dans les Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [Classement par fonction des contrôles Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)   
 [Comment : ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)