---
title: "Comment&#160;: aligner un contr&#244;le sur les bords des formulaires au moment du design | Microsoft Docs"
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
  - "contrôles personnalisés (Windows Forms), ancrer (à l'aide du concepteur)"
  - "Dock (propriété), aligner les contrôles (à l'aide du concepteur)"
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: aligner un contr&#244;le sur les bords des formulaires au moment du design
Vous pouvez faire en sorte que votre contrôle s'aligne sur le bord de vos formulaires en définissant la <xref:System.Windows.Forms.Control.Dock%2A>.  Cette propriété désigne l'emplacement de votre contrôle dans le formulaire.  La propriété <xref:System.Windows.Forms.Control.Dock%2A> peut avoir les valeurs suivantes :  
  
|Paramètre|Effet sur votre contrôle|  
|---------------|------------------------------|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre en bas du formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|Remplit tout l'espace restant dans le formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre au côté gauche du formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|Ne s'ancre nulle part et apparaît à l'emplacement spécifié par son emplacement \(<xref:System.Windows.Forms.Control.Location%2A>\).|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre au côté droit du formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre en haut du formulaire.|  
  
 Ces valeurs peuvent également être définies dans le code.  Pour plus d'informations, consultez [Comment : aligner un contrôle sur les bords des formulaires](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir la propriété Dock de votre contrôle au moment du design  
  
1.  Dans le Concepteur Windows Forms, sélectionnez votre contrôle.  
  
2.  Dans la fenêtre **Propriétés**, cliquez sur la zone déroulante en regard de la propriété <xref:System.Windows.Forms.Control.Dock%2A>.  
  
     Une interface graphique représentant les six paramètres <xref:System.Windows.Forms.Control.Dock%2A> possibles s'affiche.  
  
3.  Choisissez le paramètre approprié.  
  
4.  Votre contrôle s'ancrera désormais de la manière spécifiée par ce paramètre.  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [Comment : aligner un contrôle sur les bords des formulaires](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [Comment : ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Développement de contrôles Windows Forms au moment du design](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)