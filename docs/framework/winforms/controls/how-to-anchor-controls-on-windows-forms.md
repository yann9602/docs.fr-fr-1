---
title: "Comment : ancrer des contrôles aux Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c6f7cc527c7409ffecab2ac67386d0f819cce3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a>Comment : ancrer des contrôles aux Windows Forms
Si vous concevez un formulaire de l’utilisateur peut redimensionner au moment de l’exécution, les contrôles sur votre formulaire doivent redimensionner et repositionner correctement. Pour redimensionner dynamiquement les contrôles dans le formulaire, vous pouvez utiliser le <xref:System.Windows.Forms.Control.Anchor%2A> propriété des contrôles Windows Forms. Le <xref:System.Windows.Forms.Control.Anchor%2A> propriété définit la position d’ancrage d’un pour le contrôle. Lorsqu’un contrôle est ancré à un formulaire et le formulaire est redimensionné, le contrôle gère la distance entre le contrôle et les positions d’ancrage. Par exemple, si vous avez un <xref:System.Windows.Forms.TextBox> contrôle est ancré à la gauche, droite et inférieure du formulaire, comme le formulaire est redimensionné, le <xref:System.Windows.Forms.TextBox> contrôle est redimensionné horizontalement pour qu’il conserve la même distance des bords droit et gauche de l’écran. En outre, le contrôle se positionne verticalement afin que son emplacement est toujours la même distance entre le bord inférieur de l’écran. Si un contrôle n’est pas ancré et le formulaire est redimensionné, la position du contrôle par rapport aux bords du formulaire est modifiée.  
  
 Le <xref:System.Windows.Forms.Control.Anchor%2A> propriété interagit avec le <xref:System.Windows.Forms.Control.AutoSize%2A> propriété. Pour plus d’informations, consultez [vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-anchor-a-control-on-a-form"></a>Pour ancrer un contrôle sur un formulaire  
  
1.  Sélectionnez le contrôle que vous souhaitez ancrer.  
  
    > [!NOTE]
    >  Vous pouvez ancrer plusieurs contrôles simultanément en appuyant sur la touche CTRL ENFONCÉE, en cliquant sur chaque contrôle pour le sélectionner, puis en suivant le reste de cette procédure.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur la flèche située à droite de la <xref:System.Windows.Forms.Control.Anchor%2A> propriété.  
  
     Un éditeur s’affiche qui indique une croix.  
  
3.  Pour définir un point d’ancrage, cliquez sur le coin supérieur gauche, droite ou section inférieure de la croix.  
  
     Les contrôles sont ancrés vers le haut et gauche par défaut.  
  
4.  Pour effacer un côté du contrôle qui a été ancré, cliquez sur cette branche de la croix.  
  
5.  Pour fermer la <xref:System.Windows.Forms.Control.Anchor%2A> éditeur de propriétés, cliquez sur le <xref:System.Windows.Forms.Control.Anchor%2A> nom de la propriété à nouveau.  
  
 Lorsque votre formulaire est affiché au moment de l’exécution, le contrôle est redimensionné pour rester à la même distance entre le bord de l’écran. La distance entre le bord ancré reste toujours la même que la distance définie lorsque le contrôle se trouve dans le Concepteur Windows Forms.  
  
> [!NOTE]
>  Certains contrôles, tels que le <xref:System.Windows.Forms.ComboBox> , possèdent une limite de hauteur. Ancrer le contrôle vers le bas de sa forme ou un conteneur ne peut pas forcer le contrôle dépasse sa limite de hauteur.  
  
 Les contrôles hérités doivent être `Protected` pour pouvoir être ancrés. Pour modifier le niveau d’accès d’un contrôle, définissez son `Modifiers` propriété dans le **propriétés** fenêtre.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Guide pratique pour fixer des contrôles sur des Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
