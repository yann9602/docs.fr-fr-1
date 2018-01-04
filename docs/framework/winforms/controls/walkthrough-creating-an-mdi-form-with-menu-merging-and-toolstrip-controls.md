---
title: "Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip"
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b170c3e3311dbbfb070a66107bd4f22407647bae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Procédure pas à pas : création d'un formulaire MDI avec la fusion de menus et des contrôles ToolStrip
L'espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType> prend en charge plusieurs applications MDI (Multiple Document Interface) et le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge la fusion de menus. Les formulaires MDI peuvent également contenir des contrôles <xref:System.Windows.Forms.ToolStrip>.  
  
 Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStripPanel> les contrôles dans un formulaire MDI. Le formulaire prend également en charge la fusion de menus avec les menus enfants. Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d’un projet Windows Forms.  
  
-   Création du menu principal de votre formulaire. Le nom réel du menu varient.  
  
-   Ajout de la <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils**.  
  
-   Création d’un formulaire enfant.  
  
-   Réorganiser les <xref:System.Windows.Forms.ToolStripPanel> par ordre de plan des contrôles.  
  
 Lorsque vous avez terminé, vous aurez un formulaire MDI qui prend en charge la fusion de menus et d’être déplacés <xref:System.Windows.Forms.ToolStrip> contrôles.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Des autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’Application Windows appelé **feuille MDI**.  
  
     Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Dans le Concepteur Windows Forms, sélectionnez le formulaire.  
  
3.  Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.Form.IsMdiContainer%2A> à `true`.  
  
## <a name="creating-the-main-menu"></a>Création du Menu principal  
 Le formulaire MDI parent contient le menu principal. Le menu principal possède un élément de menu nommé **fenêtre**. Avec la **fenêtre** l’élément de menu, vous pouvez créer des formulaires enfants. Éléments de menu à partir de formulaires enfants sont fusionnés dans le menu principal.  
  
#### <a name="to-create-the-main-menu"></a>Pour créer le menu principal  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle vers le formulaire.  
  
2.  Ajouter un <xref:System.Windows.Forms.ToolStripMenuItem> à la <xref:System.Windows.Forms.MenuStrip> contrôler et nommez-le **fenêtre**.  
  
3.  Sélectionnez le contrôle <xref:System.Windows.Forms.MenuStrip>.  
  
4.  Dans la fenêtre Propriétés, définissez la valeur de la <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> propriété `ToolStripMenuItem1`.  
  
5.  Ajouter un sous-élément à la **fenêtre** élément de menu, puis nommez le sous-élément **nouveau**.  
  
6.  Dans la fenêtre Propriétés, cliquez sur **événements**.  
  
7.  Double-cliquez sur le <xref:System.Windows.Forms.ToolStripItem.Click> événement.  
  
     Le Concepteur Windows Forms génère un gestionnaire d’événements pour le <xref:System.Windows.Forms.ToolStripItem.Click> événement.  
  
8.  Insérez le code suivant dans le Gestionnaire d’événements.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]  
  
## <a name="adding-the-toolstrippanel-control-to-the-toolbox"></a>Ajout du contrôle ToolStripPanel à la boîte à outils  
 Lorsque vous utilisez <xref:System.Windows.Forms.MenuStrip> contrôles avec un formulaire MDI doit avoir le <xref:System.Windows.Forms.ToolStripPanel> contrôle. Vous devez ajouter le <xref:System.Windows.Forms.ToolStripPanel> le contrôle à la **boîte à outils** pour générer votre formulaire MDI dans le Concepteur Windows Forms.  
  
#### <a name="to-add-the-toolstrippanel-control-to-the-toolbox"></a>Pour ajouter le contrôle ToolStripPanel à la boîte à outils  
  
1.  Ouvrez le **boîte à outils**, puis cliquez sur le **tous les Windows Forms** onglet pour afficher les contrôles Windows Forms disponibles.  
  
2.  Avec le bouton droit pour ouvrir le menu contextuel, puis sélectionnez **choisir des éléments de**.  
  
3.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, faites défiler vers le bas la **nom** colonne jusqu'à ce que vous trouviez **ToolStripPanel**.  
  
4.  Activez la case à cocher en **ToolStripPanel**, puis cliquez sur **OK**.  
  
     Le <xref:System.Windows.Forms.ToolStripPanel> contrôle s’affiche dans le **boîte à outils**.  
  
## <a name="creating-a-child-form"></a>Création d’un formulaire enfant  
 Dans cette procédure, vous allez définir une classe de formulaire enfant séparée qui a son propre <xref:System.Windows.Forms.MenuStrip> contrôle. Les éléments de menu pour ce formulaire sont fusionnées avec celles du formulaire parent.  
  
#### <a name="to-define-a-child-form"></a>Pour définir un formulaire enfant  
  
1.  Ajoutez un nouveau formulaire nommé `ChildForm` au projet.  
  
     Pour plus d’informations, consultez [Comment : ajouter des Windows Forms à un projet](http://msdn.microsoft.com/en-us/3d7bb25f-fd90-47cf-9378-fa0d764686c1).  
  
2.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.MenuStrip> contrôle dans le formulaire enfant.  
  
3.  Cliquez sur le <xref:System.Windows.Forms.MenuStrip> glyphe de balise active du contrôle (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")), puis sélectionnez **modifier les éléments**.  
  
4.  Dans le **éditeur de collections Items** boîte de dialogue zone, ajoutez une nouvelle <xref:System.Windows.Forms.ToolStripMenuItem> nommé **ChildMenuItem** au menu enfant.  
  
     Pour plus d’informations, consultez [éditeur de collections d’éléments ToolStrip](http://msdn.microsoft.com/en-us/e681f3ab-94ba-4b2b-ac64-1dfad46caa25).  
  
## <a name="testing-the-form"></a>Test du formulaire  
  
#### <a name="to-test-your-form"></a>Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur le **fenêtre** élément de menu pour ouvrir le menu, puis cliquez sur **nouveau**.  
  
     Un nouveau formulaire enfant est créé dans la zone du formulaire MDI client. Les menus du formulaire enfant sont fusionné avec le menu principal.  
  
3.  Fermez le formulaire enfant.  
  
     Les menus du formulaire enfant sont supprimé dans le menu principal.  
  
4.  Cliquez sur **nouveau** plusieurs fois.  
  
     Les formulaires enfants sont automatiquement répertoriés sous la W**fenêtre** élément de menu, car le <xref:System.Windows.Forms.MenuStrip> du contrôle <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> est affectée.  
  
## <a name="adding-toolstrip-support"></a>Ajout d’un Support ToolStrip  
 Dans cette procédure, vous allez ajouter quatre <xref:System.Windows.Forms.ToolStrip> contrôles au formulaire parent MDI. Chaque <xref:System.Windows.Forms.ToolStrip> contrôle est ajouté à l’intérieur d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle, qui est ancré sur le bord de l’écran.  
  
#### <a name="to-add-toolstrip-controls-to-the-mdi-parent-form"></a>Pour ajouter des contrôles ToolStrip au formulaire parent MDI  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStripPanel> contrôle vers le formulaire.  
  
2.  Avec la <xref:System.Windows.Forms.ToolStripPanel> contrôle sélectionné, double-cliquez sur le <xref:System.Windows.Forms.ToolStrip> contrôler dans le **boîte à outils**.  
  
     A <xref:System.Windows.Forms.ToolStrip> contrôle est créé dans le <xref:System.Windows.Forms.ToolStripPanel> contrôle.  
  
3.  Sélectionnez le contrôle <xref:System.Windows.Forms.ToolStripPanel>.  
  
4.  Dans la fenêtre Propriétés, modifiez la valeur du contrôle <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Left>.  
  
     Le <xref:System.Windows.Forms.ToolStripPanel> contrôler s’ancre sur le côté gauche de l’écran, sous le menu principal. La zone cliente MDI est redimensionné pour s’ajuster à la <xref:System.Windows.Forms.ToolStripPanel> contrôle.  
  
5.  Répétez les étapes 1 à 4.  
  
     Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôle en haut du formulaire.  
  
     Le <xref:System.Windows.Forms.ToolStripPanel> contrôle est ancré sous le menu principal, mais à droite de la première <xref:System.Windows.Forms.ToolStripPanel> contrôle. Cette étape illustre l’importance de l’ordre de plan positionner correctement <xref:System.Windows.Forms.ToolStripPanel> contrôles.  
  
6.  Répétez les étapes 1 à 4 pour deux autres <xref:System.Windows.Forms.ToolStripPanel> contrôles.  
  
     Ancrer la nouvelle <xref:System.Windows.Forms.ToolStripPanel> contrôles à droite et en bas du formulaire.  
  
## <a name="arranging-toolstrippanel-controls-by-z-order"></a>Organisation des contrôles ToolStripPanel par ordre de plan  
 La position d’une fenêtre fixe <xref:System.Windows.Forms.ToolStripPanel> contrôle sur votre formulaire MDI est déterminée par la position du contrôle dans l’ordre de plan. Vous pouvez facilement réorganiser l’ordre de plan de vos contrôles dans la fenêtre Structure du Document.  
  
#### <a name="to-arrange-toolstrippanel-controls-by-z-order"></a>Pour organiser les contrôles ToolStripPanel suivant l’ordre de plan  
  
1.  Dans le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **structure du Document**.  
  
     La disposition de votre <xref:System.Windows.Forms.ToolStripPanel> contrôles à partir de la procédure précédente n’est pas standard. Il s’agit, car l’ordre de plan n’est pas correct. Utilisez la fenêtre Structure du Document pour modifier l’ordre de plan des contrôles.  
  
2.  Dans la fenêtre Structure du Document, sélectionnez **ToolStripPanel4**.  
  
3.  Cliquez sur le bouton de flèche vers le bas à plusieurs reprises, jusqu'à ce que **ToolStripPanel4** figure au bas de la liste.  
  
     Le **ToolStripPanel4** contrôle est ancré en bas de l’écran, sous les autres contrôles.  
  
4.  Sélectionnez **ToolStripPanel2**.  
  
5.  Cliquez une fois sur le bouton de flèche vers le bas pour positionner le troisième contrôle dans la liste.  
  
     Le **ToolStripPanel2** contrôle est ancrée en haut de l’écran, sous le menu principal et au-dessus des autres contrôles.  
  
6.  Sélectionnez différents contrôles dans le **structure du Document** fenêtre et les déplacer à différents endroits dans l’ordre de plan. Notez l’effet de l’ordre de plan sur la position des contrôles ancrés. Utilisez CTRL + Z ou **Annuler** sur la **modifier** menu pour annuler vos modifications.  
  
## <a name="checkpoint"></a>Point de contrôle  
  
#### <a name="to-test-your-form"></a>Pour tester votre formulaire  
  
1.  Appuyez sur F5 pour compiler et exécuter votre formulaire.  
  
2.  Cliquez sur la poignée d’un <xref:System.Windows.Forms.ToolStrip> contrôler et faites glisser le contrôle à différents endroits dans le formulaire.  
  
     Vous pouvez faire glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à partir d’un <xref:System.Windows.Forms.ToolStripPanel> contrôle à un autre.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un formulaire MDI parent avec <xref:System.Windows.Forms.ToolStrip> de contrôles et de la fusion de menus. Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStrip> famille de contrôles de nombreuses autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créer un formulaire avec un menu standard automatiquement rempli. Pour plus d’informations, consultez [procédure pas à pas : éléments de Menu Standard à un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Donnez à votre <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel. Pour plus d’informations, consultez [Comment : définir le convertisseur ToolStrip pour une Application](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Guide pratique pour créer des formulaires MDI parents](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)  
 [Guide pratique pour créer des formulaires MDI enfants](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)  
 [Guide pratique pour insérer un MenuStrip dans un menu déroulant MDI](../../../../docs/framework/winforms/controls/how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)  
 [Contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
