---
title: "Procédure pas à pas : création d'un contrôle ToolStrip de style professionnel"
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
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0fbc03ad16bcc0d63a75df5478f7da8abbf19193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Procédure pas à pas : création d'un contrôle ToolStrip de style professionnel
Vous pouvez donner à votre application <xref:System.Windows.Forms.ToolStrip> contrôle un aspect professionnel et le comportement en écrivant votre propre classe dérivée de la <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.  
  
 Cette procédure pas à pas montre comment utiliser <xref:System.Windows.Forms.ToolStrip> des contrôles pour créer un contrôle composite qui ressemble à la **volet de Navigation** fourni par Microsoft® Outlook®. Les tâches suivantes sont illustrées dans cette procédure pas à pas :  
  
-   Création d’un projet de bibliothèque de contrôles Windows.  
  
-   Conception du contrôle StackView.  
  
-   Implémentation d’un convertisseur personnalisé.  
  
 Lorsque vous avez terminé, vous devez un contrôle client personnalisé réutilisable avec l’apparence professionnelle d’un contrôle Microsoft Office® XP.  
  
 Pour copier le code dans cette rubrique sous forme de liste unique, consultez [Comment : créer un professionnel contrôle ToolStrip de style](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
-   Des autorisations suffisantes pour pouvoir créer et exécuter des projets d’application Windows Forms sur l’ordinateur où [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] est installé.  
  
## <a name="creating-a-windows-control-library-project"></a>Création d’un projet de bibliothèque de contrôles Windows  
 La première étape consiste à créer le projet de bibliothèque de contrôles.  
  
#### <a name="to-create-the-control-library-project"></a>Pour créer le projet de bibliothèque de contrôle  
  
1.  Créer un nouveau projet de bibliothèque de contrôles Windows nommé `StackViewLibrary`.  
  
2.  Dans **l’Explorateur de solutions**, supprimer le contrôle du projet par défaut en supprimant le fichier source nommé « UserControl1.cs » ou « UserControl1.vb », en fonction de la langue de votre choix.  
  
     Pour plus d’informations, consultez [NIB : Comment : exclure des éléments, de suppression et de suppression](http://msdn.microsoft.com/en-us/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Ajouter un nouveau <xref:System.Windows.Forms.UserControl> d’élément à la **StackViewLibrary** projet. Nommez le nouveau fichier source base de `StackView`.  
  
## <a name="designing-the-stackview-control"></a>Conception du contrôle StackView  
 Le `StackView` contrôle est un contrôle composite avec un seul enfant <xref:System.Windows.Forms.ToolStrip> contrôle. Pour plus d’informations sur les contrôles composites, consultez [variétés de contrôles personnalisés de](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Pour concevoir le contrôle StackView  
  
1.  À partir de la **boîte à outils**, faites glisser un <xref:System.Windows.Forms.ToolStrip> contrôle à l’aire de conception.  
  
2.  Dans le **propriétés** , configurez le <xref:System.Windows.Forms.ToolStrip> les propriétés du contrôle conformément au tableau suivant.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |Nom|`stackStrip`|  
    |CanOverflow|`false`|  
    |Station d' accueil|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Police|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle a été|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Padding|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  Dans le Concepteur Windows Forms, cliquez sur le <xref:System.Windows.Forms.ToolStrip> du contrôle **ajouter** bouton et ajoutez un <xref:System.Windows.Forms.ToolStripButton> à la `stackStrip` contrôle.  
  
4.  Dans le **propriétés** , configurez le <xref:System.Windows.Forms.ToolStripButton> les propriétés du contrôle conformément au tableau suivant.  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |Nom|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Marge|`0, 0, 0, 0`|  
    |Padding|`3, 3, 3, 3`|  
    |Texte|**Messagerie**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Répétez l’étape 7 pour les trois autres <xref:System.Windows.Forms.ToolStripButton> contrôles.  
  
     Nommez les contrôles `calendarStackButton`, `contactsStackButton`, et `tasksStackButton`. Définir la valeur de la <xref:System.Windows.Forms.Control.Text%2A> propriété **calendrier**, **Contacts**, et **tâches**, respectivement.  
  
## <a name="handling-events"></a>Gestion des événements  
 Deux événements sont importantes pour rendre le `StackView` contrôle se comporte correctement. Gérer les <xref:System.Windows.Forms.UserControl.Load> événement pour positionner le contrôle correctement. Gérer les <xref:System.Windows.Forms.ToolStripItem.Click> événement pour chaque <xref:System.Windows.Forms.ToolStripButton> pour donner le `StackView` contrôlent le comportement d’état semblable à la <xref:System.Windows.Forms.RadioButton> contrôle.  
  
#### <a name="to-handle-events"></a>Pour gérer des événements  
  
1.  Dans le Concepteur Windows Forms, sélectionnez le `StackView` contrôle.  
  
2.  Dans le **propriétés** fenêtre, cliquez sur **événements**.  
  
3.  Double-cliquez sur l’événement Load pour générer le `StackView_Load` Gestionnaire d’événements.  
  
4.  Dans la méthode de gestionnaire d'événements `StackView_Load`, copiez et collez le code suivant.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  Dans le Concepteur Windows Forms, sélectionnez le `mailStackButton` contrôle.  
  
6.  Dans le **propriétés** fenêtre, cliquez sur **événements**.  
  
7.  Double-cliquez sur l’événement Click.  
  
     Le Concepteur Windows Forms génère le `mailStackButton_Click` Gestionnaire d’événements.  
  
8.  Renommer le `mailStackButton_Click` Gestionnaire d’événements à `stackButton_Click`.  
  
     Pour plus d’informations, consultez [Comment : renommer un identificateur (Visual Basic)](http://msdn.microsoft.com/en-us/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Insérez le code suivant dans le `stackButton_Click` Gestionnaire d’événements.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. Dans le Concepteur Windows Forms, sélectionnez le `calendarStackButton` contrôle.  
  
11. Dans le **propriétés** , configurez l’événement Click pour le `stackButton_Click` Gestionnaire d’événements.  
  
12. Répétez les étapes 10 et 11 pour le `contactsStackButton` et `tasksStackButton` contrôles.  
  
## <a name="defining-icons"></a>Définition d’icônes  
 Chaque `StackView` bouton a une icône associée. Pour plus de commodité, chaque icône est représentée sous forme de chaîne codée en Base64 qui est désérialisée avant un <xref:System.Drawing.Bitmap> est créé à partir de celui-ci. Dans un environnement de production, vous stockez des données bitmap en tant que ressource et vos icônes s’affichent dans le Concepteur Windows Forms. Pour plus d’informations, consultez [Comment : ajouter des Images d’arrière-plan à des Windows Forms](http://msdn.microsoft.com/en-us/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>Pour définir des icônes  
  
1.  Dans l’éditeur de Code, insérez le code suivant dans le `StackView` définition de classe. Ce code initialise les bitmaps pour les <xref:System.Windows.Forms.ToolStripButton> icônes.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Ajoutez un appel à la `InitializeImages` méthode dans le `StackView` constructeur de classe.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Implémentation d’un convertisseur personnalisé  
 Vous pouvez personnaliser la plupart des éléments de la `StackView` contrôler en implémentant une classe qui dérive de la <xref:System.Windows.Forms.ToolStripRenderer> classe. Dans cette procédure, vous allez implémenter un <xref:System.Windows.Forms.ToolStripProfessionalRenderer> classe qui personnalise la poignée et dessine des arrière-plans dégradés pour le <xref:System.Windows.Forms.ToolStripButton> contrôles.  
  
#### <a name="to-implement-a-custom-renderer"></a>Pour implémenter un convertisseur personnalisé  
  
1.  Insérez le code suivant dans le `StackView` définition du contrôle.  
  
     La définition de la `StackRenderer` classe, qui remplace le <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, et <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> méthodes pour produire une apparence personnalisée.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  Dans le `StackView` constructeur du contrôle, créer une nouvelle instance de la `StackRenderer` classe et assignez-la à la `stackStrip` du contrôle <xref:System.Windows.Forms.ToolStrip.Renderer%2A> propriété.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>Test du contrôle StackView  
 Le `StackView` contrôle dérive la <xref:System.Windows.Forms.UserControl> classe. Par conséquent, vous pouvez tester le contrôle avec la **conteneur de Test UserControl**. Pour plus d’informations, consultez l’article [Comment : tester le comportement d’un UserControl au moment de l’exécution](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-the-stackview-control"></a>Pour tester le contrôle StackView  
  
1.  Appuyez sur F5 pour générer le projet et démarrer le **conteneur de Test UserControl**.  
  
2.  Déplacez le pointeur sur les boutons de la `StackView` contrôler, puis cliquez sur un bouton pour visualiser l’apparence de son état sélectionné.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Dans cette procédure pas à pas, vous avez créé un contrôle client personnalisé réutilisable avec l’apparence professionnelle d’un contrôle Microsoft Office XP. Vous pouvez utiliser la <xref:System.Windows.Forms.ToolStrip> famille de contrôles de nombreuses autres fins :  
  
-   Créer des menus contextuels pour vos contrôles avec <xref:System.Windows.Forms.ContextMenuStrip>. Pour plus d’informations, consultez [vue d’ensemble du composant ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Créer un formulaire avec un menu standard automatiquement rempli. Pour plus d’informations, consultez [procédure pas à pas : éléments de Menu Standard à un formulaire](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Créer un formulaire d’interface (multidocument MDI) document avec l’ancrage <xref:System.Windows.Forms.ToolStrip> contrôles. Pour plus d’informations, consultez [Comment : créer un formulaire MDI avec la fusion de menus et des contrôles ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [Contrôle ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Comment : fournir des éléments de menu standard à un formulaire](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
