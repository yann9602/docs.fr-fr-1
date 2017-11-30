---
title: "Comment : créer une interface de style Explorateur Windows sur un Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Explorer [Windows Forms], creating with Windows Forms
- SplitContainer control [Windows Forms], Explorer-style interface
- forms [Windows Forms], Windows Explorer type
ms.assetid: 9a3d5f4f-5dda-4350-9ad5-57ce5976dc47
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96f2ca8189d6840bc68f063ef9b97539c24b0e6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-explorerstyle-interface-on-a-windows-form"></a>Comment : créer une interface de style Explorateur Windows sur un Windows Form
L’Explorateur Windows est un choix d’interface utilisateur commune pour les applications en raison de son caractère familier.  
  
 Est de l’Explorateur Windows, essentiellement, un <xref:System.Windows.Forms.TreeView> contrôle et un <xref:System.Windows.Forms.ListView> contrôle sur des panneaux séparés. Les panneaux sont rendus redimensionnables par un séparateur. Cette disposition des contrôles est très efficace pour afficher et parcourir des informations.  
  
 Les étapes suivantes montrent comment organiser les contrôles dans un formulaire de type Explorateur Windows. Elles ne présentent pas de procédure Ajouter les fonctionnalités d’exploration des fichiers de l’application de l’Explorateur Windows.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-windows-explorer-style-windows-form"></a>Pour créer un formulaire Windows de style Explorateur Windows  
  
1.  Créer un nouveau projet d’Application Windows. Pour plus d’informations, consultez l’article [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  À partir de la **boîte à outils**:  
  
    1.  Faites glisser un <xref:System.Windows.Forms.SplitContainer> contrôle vers votre formulaire.  
  
    2.  Faites glisser un <xref:System.Windows.Forms.TreeView> contrôler en **SplitterPanel1** (le panneau de configuration de la <xref:System.Windows.Forms.SplitContainer> contrôle marqué comme **Panel1**).  
  
    3.  Faites glisser un <xref:System.Windows.Forms.ListView> contrôler en **SplitterPanel2** (le panneau de configuration de la <xref:System.Windows.Forms.SplitContainer> contrôle marqué comme **Panel2**).  
  
3.  Sélectionnez les trois contrôles en appuyant sur la touche CTRL ENFONCÉE et en cliquant dessus à son tour. Lorsque vous sélectionnez le <xref:System.Windows.Forms.SplitContainer> contrôler, cliquez sur la barre de fractionnement, plutôt que les panneaux.  
  
    > [!NOTE]
    >  N’utilisez pas le **sélectionner tout** commande sur le **modifier** menu. Si vous procédez ainsi, la propriété nécessaire à l’étape suivante n’apparaîtra pas dans le **propriétés** fenêtre.  
  
4.  Dans le **propriétés** , configurez la <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Appuyez sur F5 pour exécuter l'application.  
  
     Le formulaire affiche une interface utilisateur en deux parties, semblable à celle de l’Explorateur Windows.  
  
    > [!NOTE]
    >  Lorsque vous faites glisser le séparateur, les panneaux se redimensionnent.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.SplitContainer>  
 [Guide pratique pour créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)  
 [Guide pratique pour définir le redimensionnement et le positionnement du comportement dans une fenêtre fractionnée](../../../../docs/framework/winforms/controls/how-to-define-resize-and-positioning-behavior-in-a-split-window.md)  
 [Guide pratique pour fractionner une fenêtre horizontalement](../../../../docs/framework/winforms/controls/how-to-split-a-window-horizontally.md)  
 [SplitContainer, contrôle](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
