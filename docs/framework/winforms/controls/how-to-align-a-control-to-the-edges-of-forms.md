---
title: "Comment&#160;: aligner un contr&#244;le sur les bords des formulaires | Microsoft Docs"
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
  - "contrôles (Windows Forms), aligner sur des formulaires"
  - "contrôles personnalisés (Windows Forms), ancrer à l'aide du code"
  - "Dock (propriété), aligner les contrôles à l'aide du code"
  - "formulaires, aligner des contrôles"
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: aligner un contr&#244;le sur les bords des formulaires
Vous pouvez aligner un contrôle sur le bord de vos formulaires en définissant la propriété <xref:System.Windows.Forms.Control.Dock%2A>.  Cette propriété désigne l’emplacement de votre contrôle dans le formulaire.  La propriété <xref:System.Windows.Forms.Control.Dock%2A> peut avoir les valeurs suivantes :  
  
|Paramètre|Effet sur le contrôle|  
|---------------|---------------------------|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre en bas du formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|Remplit tout l'espace restant dans le formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre sur le côté gauche du formulaire.|  
|<xref:System.Windows.Forms.DockStyle>|Ne s'ancre nulle part et apparaît à l'emplacement spécifié par sa propriété <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre sur le côté droit du formulaire..|  
|<xref:System.Windows.Forms.DockStyle>|S'ancre en haut du formulaire.|  
  
 Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.  
  
### Pour définir la propriété Dock de votre contrôle au moment de l'exécution  
  
1.  Affectez la valeur appropriée à la propriété <xref:System.Windows.Forms.Control.Dock%2A> dans le code.  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## Voir aussi  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=fullName>   
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)   
 [Comment : ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)   
 [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)