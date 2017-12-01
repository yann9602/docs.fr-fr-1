---
title: "Comment : aligner un contrôle sur les bords des formulaires"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a55212ac4d770848355ace1b0ef3fff3cc50f871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>Comment : aligner un contrôle sur les bords des formulaires
Vous pouvez aligner un contrôle sur le bord de vos formulaires en définissant la propriété <xref:System.Windows.Forms.Control.Dock%2A>. Cette propriété désigne l’emplacement de votre contrôle dans le formulaire. La propriété <xref:System.Windows.Forms.Control.Dock%2A> peut avoir les valeurs suivantes :  
  
|Paramètre|Effet sur le contrôle|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|S'ancre en bas du formulaire.|  
|<xref:System.Windows.Forms.DockStyle.Fill>|Remplit tout l'espace restant dans le formulaire.|  
|<xref:System.Windows.Forms.DockStyle.Left>|S'ancre sur le côté gauche du formulaire.|  
|<xref:System.Windows.Forms.DockStyle.None>|Ne s'ancre nulle part et apparaît à l'emplacement spécifié par sa propriété <xref:System.Windows.Forms.Control.Location%2A>.|  
|<xref:System.Windows.Forms.DockStyle.Right>|S'ancre sur le côté droit du formulaire.|  
|<xref:System.Windows.Forms.DockStyle.Top>|S'ancre en haut du formulaire.|  
  
 Cette fonctionnalité est prise en charge au moment du design dans Visual Studio.  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>Pour définir la propriété Dock de votre contrôle au moment de l'exécution  
  
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
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [Développement de contrôles Windows Forms personnalisés avec le .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Guide pratique pour ancrer des contrôles enfants dans un contrôle FlowLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
