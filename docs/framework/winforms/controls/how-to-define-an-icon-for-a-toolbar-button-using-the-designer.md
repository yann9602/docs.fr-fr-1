---
title: "Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e72b2516efab3bc5b5d8cc7cacb66f149f3a66
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>Comment : définir une icône pour un bouton ToolBar à l'aide du concepteur
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 <xref:System.Windows.Forms.ToolBar>boutons sont en mesure d’afficher des icônes pour faciliter l’identification par les utilisateurs. Pour cela ajouter des images à le <xref:System.Windows.Forms.ImageList> composant et en l’associant la <xref:System.Windows.Forms.ToolBar> contrôle.  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ToolBar> contrôle et une <xref:System.Windows.Forms.ImageList> composant. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>Pour définir une icône pour un bouton de barre d’outils au moment du design  
  
1.  Ajouter des images à le <xref:System.Windows.Forms.ImageList> composant. Pour plus d’informations, consultez [Comment : ajouter ou supprimer des Images ImageList avec le concepteur](../../../../docs/framework/winforms/controls/how-to-add-or-remove-imagelist-images-with-the-designer.md).  
  
2.  Sélectionnez le <xref:System.Windows.Forms.ToolBar> contrôle de votre formulaire.  
  
3.  Dans le **propriétés** , configurez la <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.ImageList%2A> propriété le <xref:System.Windows.Forms.ImageList> composant.  
  
4.  Cliquez sur le <xref:System.Windows.Forms.ToolBar> du contrôle <xref:System.Windows.Forms.ToolBar.Buttons%2A> propriété à sélectionner, puis cliquez sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) pour ouvrir la **Éditeur de collections ToolBarButton**.  
  
5.  Utilisez le **ajouter** bouton pour ajouter des boutons à la <xref:System.Windows.Forms.ToolBar> contrôle.  
  
6.  Dans le **propriétés** fenêtre qui s’affiche dans le volet situé à droite de la **éditeur de collections ToolBarButton**, définissez le <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> propriété de chaque bouton de barre d’outils à une des valeurs dans la liste, qui est dessiné à partir des images que vous avez ajouté à la <xref:System.Windows.Forms.ImageList> composant.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ToolBar>  
 [Guide pratique pour déclencher des événements de menu pour les boutons de barre d’outils](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [ToolBar, contrôle](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)  
 [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md)
