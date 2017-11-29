---
title: "Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire"
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
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1eccb033dd07f634f3629fd6f314eaa3df56b422
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Procédure pas à pas : mise à disposition d'éléments de menu standard pour un formulaire
Vous pouvez fournir un menu standard pour vos formulaires avec le contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
 Cette procédure pas à pas montre comment utiliser un <xref:System.Windows.Forms.MenuStrip> contrôle pour créer un menu standard. Le formulaire répond également lorsqu’un utilisateur sélectionne un élément de menu. Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d’un projet Windows Forms.  
  
-   Création d’un menu standard.  
  
-   Création d’un <xref:System.Windows.Forms.StatusStrip> contrôle.  
  
-   Gérer la sélection d’éléments de menu.  
  
 Lorsque vous avez terminé, vous disposerez d’un formulaire avec un menu standard affichant les sélections d’élément de menu dans un <xref:System.Windows.Forms.StatusStrip> contrôle.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : fournir d’éléments de Menu Standard à un formulaire](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Des autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’application Windows appelé **StandardMenuForm**.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans le Concepteur Windows Forms, sélectionnez le formulaire.  
  
## <a name="creating-a-standard-menu"></a>Création d’un Menu Standard  
 Le Concepteur Windows Forms peut remplir automatiquement un <xref:System.Windows.Forms.MenuStrip> contrôle avec des éléments de menu standard.  
  
#### <a name="to-create-a-standard-menu"></a>Pour créer un menu standard  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle vers votre formulaire.  
  
2.  Cliquez sur le <xref:System.Windows.Forms.MenuStrip> glyphe de balise active du contrôle (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) et sélectionnez **insérer des éléments Standard**.  
  
     Le <xref:System.Windows.Forms.MenuStrip> contrôle soit rempli avec les éléments de menu standard.  
  
3.  Cliquez sur le **fichier** élément de menu pour afficher ses éléments de menu par défaut et les icônes correspondantes.  
  
## <a name="creating-a-statusstrip-control"></a>Création d’un contrôle StatusStrip  
 Utilisez la <xref:System.Windows.Forms.StatusStrip> contrôle pour afficher l’état de vos applications Windows Forms. Dans l’exemple actuel, les éléments de menu sélectionnés par l’utilisateur sont affichés dans un <xref:System.Windows.Forms.StatusStrip> contrôle.  
  
#### <a name="to-create-a-statusstrip-control"></a>Pour créer un contrôle StatusStrip  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.StatusStrip> contrôle vers votre formulaire.  
  
     Le <xref:System.Windows.Forms.StatusStrip> contrôle s’ancre automatiquement vers le bas du formulaire.  
  
2.  Cliquez sur le <xref:System.Windows.Forms.StatusStrip> du contrôle bouton de liste déroulante, puis sélectionnez **StatusLabel** pour ajouter un <xref:System.Windows.Forms.ToolStripStatusLabel> le contrôle à la <xref:System.Windows.Forms.StatusStrip> contrôle.  
  
## <a name="handling-item-selection"></a>Sélection d’éléments de gestion  
 Gérer les <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> événement répondre quand l’utilisateur sélectionne un élément de menu.  
  
#### <a name="to-handle-item-selection"></a>Pour gérer la sélection d’éléments  
  
1.  Cliquez sur le **fichier** élément de menu que vous avez créé dans la création une section de Menu Standard.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur **événements**.  
  
3.  Double-cliquez sur le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> événement.  
  
     Le Concepteur Windows Forms génère un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> événement.  
  
4.  Insérez le code suivant dans le Gestionnaire d’événements.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Insérer le `UpdateStatus` définition de méthode utilitaire dans le formulaire.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Point de contrôle  
  
#### <a name="to-test-your-form"></a>Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur le **fichier** élément de menu pour ouvrir le menu.  
  
3.  Sur le **fichier** menu, cliquez sur un des éléments pour le sélectionner.  
  
     Le <xref:System.Windows.Forms.StatusStrip> contrôle affiche l’élément sélectionné.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un formulaire avec un menu standard. Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStrip> famille de contrôles de nombreuses autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créer un formulaire d’interface (multidocument MDI) document avec l’ancrage <xref:System.Windows.Forms.ToolStrip> contrôles. Pour plus d’informations, consultez [procédure pas à pas : création d’un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Donnez à votre <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel. Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [MenuStrip, contrôle](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
