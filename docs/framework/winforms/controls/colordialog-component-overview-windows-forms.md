---
title: Vue d'ensemble du composant ColorDialog (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ColorDialog
helpviewer_keywords:
- color dialog box [Windows Forms], about color dialog box
- ColorDialog component [Windows Forms], about ColorDialog
ms.assetid: 6dbdd8f0-f697-4728-bb09-7ea156f6d800
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5df0d7ddd16de5bd8bb052c09731df6583ca4903
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="colordialog-component-overview-windows-forms"></a>Vue d'ensemble du composant ColorDialog (Windows Forms)
Windows Forms <xref:System.Windows.Forms.ColorDialog> composant est une boîte de dialogue préconfigurée qui permet à l’utilisateur de sélectionner une couleur dans une palette et d’ajouter des couleurs personnalisées à cette palette. Il s’agit de la même boîte de dialogue que celle que vous voyez dans d’autres applications Windows pour sélectionner des couleurs. Vous pouvez l'utiliser dans votre application Windows comme alternative à la configuration de votre propre boîte de dialogue.  
  
 La couleur sélectionnée dans la boîte de dialogue est retournée dans le <xref:System.Windows.Forms.ColorDialog.Color%2A> propriété. Si le <xref:System.Windows.Forms.ColorDialog.AllowFullOpen%2A> est définie sur `false`, le bouton « Définir des couleurs personnalisées » est désactivé et que l’utilisateur est limité aux couleurs prédéfinies dans la palette. Si le <xref:System.Windows.Forms.ColorDialog.SolidColorOnly%2A> est définie sur `true`, l’utilisateur ne peut pas sélectionner de couleurs tramées. Pour afficher la boîte de dialogue, vous devez appeler sa <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ColorDialog>  
 [ColorDialog, composant](../../../../docs/framework/winforms/controls/colordialog-component-windows-forms.md)  
 [Contrôles et composants de boîte de dialogue](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 [Guide pratique pour modifier l’apparence du composant ColorDialog Windows Forms](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-colordialog-component.md)
