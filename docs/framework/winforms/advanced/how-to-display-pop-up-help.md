---
title: "Comment : afficher l'aide contextuelle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e5f57e0a7981e8cae93960c8ffc3ed2168594cf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-pop-up-help"></a>Comment : afficher l'aide contextuelle
Permet d’afficher l’aide dans les Windows Forms s’effectue via le **aide** bouton situé sur le côté droit de la barre de titre, accessible via la <xref:System.Windows.Forms.Form.HelpButton%2A> propriété. Ce type d’affichage de l’aide convient parfaitement aux boîtes de dialogue. Les boîtes de dialogue modales (affichées avec la méthode <xref:System.Windows.Forms.Form.ShowDialog%2A>) ont des difficultés à afficher les systèmes d'aide externes, car elles doivent être fermées pour que le focus puisse basculer vers une autre fenêtre. En outre, à l’aide de la **aide** bouton nécessite qu’il y a aucune **réduire** bouton ou **agrandir** affiché dans la barre de titre. Il s’agit une convention de la boîte de dialogue standard, tandis que les formulaires possèdent généralement **réduire** et **agrandir** boutons.  
  
 Sachez que vous pouvez également utiliser le composant <xref:System.Windows.Forms.HelpProvider> pour lier des contrôles à des fichiers d'un système d'aide, même si vous avez implémenté l'aide contextuelle. Pour plus d’informations, consultez [fourniture d’aide dans une Application Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-pop-up-help"></a>Pour afficher une aide contextuelle  
  
1.  Faites glisser un [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) composant à partir de la boîte à outils vers votre formulaire.  
  
     Il sera placé dans la barre d'état en bas du Concepteur Windows Forms.  
  
2.  Dans la fenêtre Propriétés, affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Form.HelpButton%2A>. Ceci affichera un bouton avec un point d'interrogation sur le côté droit de la barre de titre du formulaire.  
  
3.  Pour que le <xref:System.Windows.Forms.Form.HelpButton%2A> soit affiché, il faut que les propriétés <xref:System.Windows.Forms.Form.MinimizeBox%2A> et <xref:System.Windows.Forms.Form.MaximizeBox%2A>  du formulaire aient la valeur `false`, que la propriété <xref:System.Windows.Forms.Form.ControlBox%2A> ait la valeur `true` et que la propriété <xref:System.Windows.Forms.Form.FormBorderStyle%2A> ait l'une des valeurs suivantes : <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> ou <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Sélectionnez le contrôle pour lequel vous souhaitez afficher l'aide sur votre formulaire et définissez la chaîne d'aide dans la fenêtre Propriétés. C’est la chaîne de texte qui s’affichera dans une fenêtre similaire à un [info-bulle](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).  
  
5.  Appuyez sur **F5**.  
  
6.  Appuyez sur la **aide** sur la barre de titre, puis cliquez sur le contrôle sur lequel vous définissez la chaîne d’aide.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage sous forme d’info-bulles de l’aide relative aux contrôles](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [Intégration de l’aide d’utilisateur dans les Windows Forms](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
