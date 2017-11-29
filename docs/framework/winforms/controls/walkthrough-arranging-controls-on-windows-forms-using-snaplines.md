---
title: "Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement (SnapLines)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with snaplines
- snaplines [Windows Forms], arranging Windows Forms controls
- SnapLine class [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: be514f435b787c770eca114d42bee5c1424a40c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-snaplines"></a>Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement (SnapLines)
Le positionnement précis des contrôles sur votre formulaire constitue une haute priorité pour de nombreuses applications. Le Concepteur Windows Forms offre de nombreux outils de disposition pour y parvenir. Un des plus importants est le <xref:System.Windows.Forms.Design.Behavior.SnapLine> fonctionnalité.  
  
 Les lignes d’alignement vous indiquent précisément où aligner des contrôles avec d’autres contrôles. Ils indiquent également les distances recommandées pour les marges entre les contrôles, comme spécifié par les indications d’Interface utilisateur Windows. Pour plus d’informations, consultez [développement et conception de l’Interface utilisateur](http://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Les lignes d’alignement permettent d’aligner vos contrôles pour crisp, Professionnel apparence et le comportement (apparence).  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Windows Forms  
  
-   L’espacement et l’alignement des contrôles à l’aide des lignes d’alignement  
  
-   Alignement de formulaire et des marges de conteneur  
  
-   Alignement des contrôles groupés  
  
-   À l’aide des lignes d’alignement pour placer un contrôle en dessinant sa taille en  
  
-   À l’aide des lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
-   Redimensionnement de contrôles à l’aide des lignes d’alignement  
  
-   Alignement d’une étiquette de texte d’un contrôle  
  
-   À l’aide des lignes d’alignement avec la Navigation au clavier  
  
-   Les lignes d’alignement et panneaux de disposition  
  
-   La désactivation des lignes d’alignement  
  
 Lorsque vous avez terminé, vous comprendrez le rôle de disposition joué par la fonctionnalité de lignes d’alignement.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’application Windows appelé « SnaplineExample ». Pour plus d’informations, consultez l’article [Comment : créer un projet d’application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le Concepteur de formulaires.  
  
## <a name="spacing-and-aligning-controls-using-snaplines"></a>L’espacement et l’alignement des contrôles à l’aide des lignes d’alignement  
 Les lignes d’alignement vous donnent un moyen précis et intuitif pour aligner des contrôles sur votre formulaire. Elles apparaissent lorsque vous déplacez un ou plusieurs contrôles sélectionnés près d’une position qui est aligné sur un autre contrôle ou un ensemble de contrôles. Votre sélection sera « aligné » à la position suggérée que vous dépassez les autres contrôles.  
  
#### <a name="to-arrange-controls-using-snaplines"></a>Pour organiser les contrôles à l’aide des lignes d’alignement  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Déplacer le <xref:System.Windows.Forms.Button> contrôle vers le coin inférieur droit du formulaire. Notez les lignes d’alignement apparaissent en tant que le <xref:System.Windows.Forms.Button> contrôle s’approche des bordures inférieure et droite de l’écran. Ces lignes d’alignement affichent la distance recommandée entre les bordures du contrôle et le formulaire.  
  
3.  Déplacer le <xref:System.Windows.Forms.Button> contrôle autour des bordures du formulaire et notez où les lignes d’alignement apparaissent. Lorsque vous avez terminé, déplacez le <xref:System.Windows.Forms.Button> contrôle près du centre de l’écran.  
  
4.  Faites glisser une autre <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
5.  Déplacez le second <xref:System.Windows.Forms.Button> contrôle jusqu'à ce qu’il soit presque au niveau du premier. Notez la ligne d’alignement apparaît au niveau de la ligne de base des deux boutons et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au niveau de l’autre contrôle.  
  
6.  Déplacez le second <xref:System.Windows.Forms.Button> contrôle jusqu'à ce qu’il est placé directement au-dessus du premier. Notez les lignes d’alignement qui apparaissent sur les bords gauche et droit des deux boutons et notez que le contrôle vous déplacez s’aligne à une position qui est alignée exactement avec l’autre contrôle.  
  
7.  Sélectionnez une de le <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de l’autre, jusqu'à ce qu’ils se touchent presque. Notez la ligne d’alignement qui apparaît entre eux. Cette distance est la distance recommandée entre les bordures des contrôles. Notez également que le contrôle que vous déplacez s’aligne à cette position.  
  
8.  Faites glisser deux <xref:System.Windows.Forms.Panel> des contrôles de la **boîte à outils** vers votre formulaire.  
  
9. Déplacez l’un de le <xref:System.Windows.Forms.Panel> contrôle jusqu'à ce qu’il soit presque au niveau du premier. Notez les lignes d’alignement qui s’affichent le long des bords supérieur et inférieur des deux contrôles et notez que le contrôle que vous déplacez s’aligne à une position qui est exactement au niveau de l’autre contrôle.  
  
## <a name="aligning-to-form-and-container-margins"></a>Alignement de formulaire et des marges de conteneur  
 Les lignes d’alignement vous aident à aligner des contrôles pour les marges de formulaires et de conteneurs de façon cohérente.  
  
#### <a name="to-align-controls-to-form-and-container-margins"></a>Pour aligner des contrôles pour les marges de formulaires et de conteneurs  
  
1.  Sélectionnez une de le <xref:System.Windows.Forms.Button> contrôle et déplacez-le proche de la bordure droite de l’écran jusqu'à ce qu’une ligne d’alignement apparaît. Distance de la ligne d’alignement de la bordure droite est la somme du contrôle <xref:System.Windows.Forms.Control.Margin%2A> propriété et du formulaire <xref:System.Windows.Forms.Control.Padding%2A> valeurs de propriété.  
  
> [!NOTE]
>  Si du formulaire <xref:System.Windows.Forms.Control.Padding%2A> propriété a la valeur 0,0,0,0, le Concepteur Windows Forms permet au formulaire d’un élément occulté <xref:System.Windows.Forms.Control.Padding%2A> valeur 9,9,9,9. Pour remplacer ce comportement, affectez une valeur autre que 0,0,0,0.  
  
1.  Modifiez la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Margin%2A> propriété en développant le <xref:System.Windows.Forms.Control.Margin%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> 0 à la propriété. Pour plus d’informations, consultez [procédure pas à pas : disposition des contrôles Windows Forms avec Padding, Margins et la propriété AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Déplacer le <xref:System.Windows.Forms.Button> contrôle proche de la bordure droite de l’écran jusqu'à ce qu’une ligne d’alignement apparaît. Cette distance est maintenant indiquée par la valeur du formulaire <xref:System.Windows.Forms.Control.Padding%2A> propriété.  
  
3.  Faites glisser un <xref:System.Windows.Forms.GroupBox> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
4.  Modifiez la valeur de la <xref:System.Windows.Forms.GroupBox> du contrôle <xref:System.Windows.Forms.Control.Padding%2A> propriété en développant le <xref:System.Windows.Forms.Control.Padding%2A> entrée dans le **propriétés** fenêtre et en attribuant le <xref:System.Windows.Forms.Padding.All%2A> propriété à 10.  
  
5.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.GroupBox> contrôle.  
  
6.  Déplacer le <xref:System.Windows.Forms.Button> contrôle proche de la bordure droite de la <xref:System.Windows.Forms.GroupBox> contrôle jusqu'à ce qu’une ligne d’alignement apparaît. Déplacer le <xref:System.Windows.Forms.Button> contrôler dans le <xref:System.Windows.Forms.GroupBox> contrôle et notez où les lignes d’alignement apparaissent.  
  
## <a name="aligning-to-grouped-controls"></a>Alignement des contrôles groupés  
 Vous pouvez utiliser des lignes d’alignement pour aligner des contrôles regroupés ainsi que des contrôles dans un <xref:System.Windows.Forms.GroupBox> contrôle.  
  
#### <a name="to-align-to-grouped-controls"></a>Pour aligner des contrôles regroupés  
  
1.  Sélectionnez deux contrôles sur votre formulaire. Déplacer la sélection et notez les lignes d’alignement qui apparaissent entre votre sélection et les autres contrôles.  
  
2.  Faites glisser un <xref:System.Windows.Forms.GroupBox> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
3.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.GroupBox> contrôle.  
  
4.  Sélectionnez une de la <xref:System.Windows.Forms.Button> contrôle et déplacer le <xref:System.Windows.Forms.GroupBox> contrôle. Notez les lignes d’alignement qui apparaissent sur les bords de la <xref:System.Windows.Forms.GroupBox> contrôle. Notez également les lignes d’alignement qui apparaissent sur les bords de la <xref:System.Windows.Forms.Button> contrôle contenu dans le <xref:System.Windows.Forms.GroupBox> contrôle. Les contrôles qui sont des enfants d’un contrôle conteneur prennent également en charge les lignes d’alignement.  
  
## <a name="using-snaplines-to-place-a-control-by-outlining-its-size"></a>À l’aide des lignes d’alignement pour placer un contrôle en dessinant sa taille en  
 Les lignes d’alignement vous aident à qu'aligner contrôle lorsque vous placez d’abord les sur un formulaire.  
  
#### <a name="to-use-snaplines-to-place-a-control-by-outlining-its-size"></a>Pour utiliser les lignes d’alignement pour placer un contrôle en dessinant sa taille en  
  
1.  Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.  
  
2.  Déplacez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> . Notez également les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le <xref:System.Windows.Forms.Button> contrôle.  
  
3.  Cliquez et maintenez le bouton de la souris enfoncé.  
  
4.  Faites glisser le pointeur de la souris autour du formulaire. Notez qu’un plan est dessiné, indiquant la position et la taille du contrôle.  
  
5.  Faites glisser le pointeur jusqu'à ce qu’il s’aligne sur un autre contrôle sur le formulaire. Notez qu’une ligne d’alignement apparaît pour indiquer l’alignement.  
  
6.  Relâchez le bouton de la souris. Le contrôle est créé à la position et la taille indiquée par le plan.  
  
## <a name="using-snaplines-when-dragging-a-control-from-the-toolbox"></a>À l’aide des lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
 Les lignes d’alignement vous aident à aligner contrôle lorsque vous les faites glisser à partir de la **boîte à outils** vers votre formulaire.  
  
#### <a name="to-use-snaplines-when-dragging-a-control-from-the-toolbox"></a>Pour utiliser les lignes d’alignement lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire, mais ne relâchez pas le bouton de la souris.  
  
2.  Déplacez le pointeur de la souris sur l’aire de conception du formulaire. Notez que le pointeur se transforme pour indiquer la position à laquelle la nouvelle <xref:System.Windows.Forms.Button> contrôle sera créé.  
  
3.  Faites glisser le pointeur de la souris autour du formulaire. Notez les lignes d’alignement qui apparaissent pour suggérer des positions alignées pour le <xref:System.Windows.Forms.Button> contrôle. Rechercher une position qui est alignée avec d’autres contrôles.  
  
4.  Relâchez le bouton de la souris. Le contrôle est créé à la position indiquée par les lignes d’alignement.  
  
## <a name="resizing-controls-using-snaplines"></a>Redimensionnement de contrôles à l’aide des lignes d’alignement  
 Les lignes d’alignement vous aident à aligner les contrôles les redimensionner.  
  
#### <a name="to-resize-a-control-using-snaplines"></a>Pour redimensionner un contrôle à l’aide des lignes d’alignement  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Redimensionner le <xref:System.Windows.Forms.Button> contrôle en saisissant l’une des poignées de redimensionnement et en faisant glisser. Pour plus d’informations, consultez [Comment : redimensionner des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Faites glisser la poignée de redimensionnement jusqu'à la <xref:System.Windows.Forms.Button> bordures du contrôle est aligné avec un autre contrôle. Notez qu’une ligne d’alignement apparaît. Notez également que la poignée de redimensionnement s’aligne à la position indiquée par la ligne d’alignement.  
  
4.  Redimensionner le <xref:System.Windows.Forms.Button> contrôler dans différentes directions et alignez la poignée de redimensionnement selon différents contrôles. Notez comment les lignes d’alignement apparaissent dans différentes orientations pour indiquer l’alignement.  
  
## <a name="aligning-a-label-to-a-controls-text"></a>Alignement d’une étiquette de texte d’un contrôle  
 Certains contrôles offrent une ligne d’alignement pour aligner les autres contrôles au texte affiché.  
  
#### <a name="to-align-a-label-to-a-controls-text"></a>Pour aligner une étiquette de texte d’un contrôle  
  
1.  Faites glisser un <xref:System.Windows.Forms.TextBox> contrôle depuis la **boîte à outils** vers votre formulaire. Lorsque vous déposez le <xref:System.Windows.Forms.TextBox> contrôle vers le formulaire, cliquez sur le glyphe de balise active et sélectionnez le **la valeur texte textBox1** option. Pour plus d’informations, consultez [procédure pas à pas : exécution courantes des tâches à l’aide de balises actives des contrôles Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Faites glisser un <xref:System.Windows.Forms.Label> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
3.  Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Label>. Notez que les bordures du contrôle sont ajustées pour s’adapter au texte d’affichage.  
  
4.  Déplacer le <xref:System.Windows.Forms.Label> contrôle vers la gauche de la <xref:System.Windows.Forms.TextBox> contrôler, afin qu’il est aligné sur le bord inférieur de la <xref:System.Windows.Forms.TextBox> contrôle. Notez la ligne d’alignement qui apparaît le long des bords en bas des deux contrôles.  
  
5.  Déplacer le <xref:System.Windows.Forms.Label> contrôle légèrement vers le haut, jusqu'à ce que le <xref:System.Windows.Forms.Label> texte et la <xref:System.Windows.Forms.TextBox> texte sont alignées. Notez la ligne d’alignement différemment de style qui s’affiche, indiquant que les champs de texte des deux contrôles sont alignées.  
  
## <a name="using-snaplines-with-keyboard-navigation"></a>À l’aide des lignes d’alignement avec la Navigation au clavier  
 Les lignes d’alignement vous aident à qu'aligner contrôle lorsque vous les réorganisez à l’aide des touches de direction du clavier.  
  
#### <a name="to-use-snaplines-with-keyboard-navigation"></a>Pour utiliser les lignes d’alignement avec la navigation au clavier  
  
1.  Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** vers votre formulaire. Placez-le dans le coin supérieur gauche du formulaire.  
  
2.  Appuyez sur CTRL + flèche bas. Notez que le contrôle se déplace vers le bas de l’écran à la première position d’alignement horizontal disponible.  
  
3.  Appuyez sur CTRL + flèche bas jusqu'à ce que le contrôle atteint le bas du formulaire. Notez les positions qu’il occupe lorsqu’il se déplace vers le bas du formulaire.  
  
4.  Appuyez sur CTRL + flèche droite. Notez que le contrôle se trouve sur le formulaire à la première position d’alignement verticale disponible.  
  
5.  Appuyez sur CTRL + flèche droite jusqu'à ce que le contrôle atteigne le côté du formulaire. Notez les positions qu’il occupe comme il se trouve sur le formulaire.  
  
6.  Déplacez le contrôle autour du formulaire avec une combinaison de touches de direction. Notez les positions occupées par le contrôle et les lignes d’alignement qui les accompagnent.  
  
7.  Appuyez sur MAJ + touches de direction pour redimensionner le <xref:System.Windows.Forms.Button> contrôle par incréments d’un pixel.  
  
8.  Appuyez sur CTRL + MAJ + touches de direction pour redimensionner le <xref:System.Windows.Forms.Button> contrôle par incréments de ligne d’alignement.  
  
## <a name="snaplines-and-layout-panels"></a>Les lignes d’alignement et panneaux de disposition  
 Les lignes d’alignement sont désactivés dans les panneaux de disposition.  
  
#### <a name="to-selectively-disable-snaplines"></a>Pour désactiver de manière sélective les lignes d’alignement  
  
1.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle de bouton apparaît dans le <xref:System.Windows.Forms.TableLayoutPanel> première cellule du contrôle.  
  
3.  Double-cliquez sur le <xref:System.Windows.Forms.Button> icône de contrôle dans le **boîte à outils** deux fois de plus. Cela laisse une cellule vide dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
4.  Faites glisser un <xref:System.Windows.Forms.Button> contrôler à partir de la **boîte à outils** dans la cellule vide de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez qu’aucune ligne d’alignement n’apparaître.  
  
5.  Faites glisser le <xref:System.Windows.Forms.Button> contrôler de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle et la déplacer le <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez que les lignes d’alignement s’affichent à nouveau.  
  
## <a name="disabling-snaplines"></a>La désactivation des lignes d’alignement  
 Les lignes d’alignement sont activés par défaut. Vous pouvez désactiver sélectivement les lignes d’alignement, ou vous pouvez les désactiver dans l’environnement de conception.  
  
#### <a name="to-selectively-disable-snaplines"></a>Pour désactiver de manière sélective les lignes d’alignement  
  
-   Appuyez sur la touche ALT et tout en déplaçant un contrôle autour du formulaire.  
  
     Notez qu’aucune ligne d’alignement n’apparaître et le contrôle ne s’aligne sur toutes les positions d’alignement potentielles.  
  
#### <a name="to-disable-snaplines-in-the-design-environment"></a>Pour désactiver les lignes d’alignement dans l’environnement de conception  
  
1.  À partir de la **outils** menu, ouvrir le **Options** boîte de dialogue. Ouvrez la boîte de dialogue du Concepteur Windows Forms. Pour plus d’informations, consultez [général, Concepteur Windows Forms, boîte de dialogue Options](http://msdn.microsoft.com/en-us/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Sélectionnez le **général** nœud. Dans le **Mode de disposition** section, modifiez la sélection à partir de **les lignes d’alignement** à **SnapToGrid**.  
  
3.  Cliquez sur OK pour appliquer le paramètre.  
  
4.  Sélectionnez un contrôle sur votre formulaire et déplacer les autres contrôles. Notez que les lignes d’alignement n’apparaissent pas.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Les lignes d’alignement offrent un moyen intuitif de l’alignement des contrôles sur votre formulaire. Voici quelques suggestions à explorer :  
  
-   Essayez d’imbriquer un <xref:System.Windows.Forms.GroupBox> contrôle dans une autre <xref:System.Windows.Forms.GroupBox> contrôle. Place un <xref:System.Windows.Forms.Button> contrôle au sein de l’enfant <xref:System.Windows.Forms.GroupBox> contrôle et l’autre au sein du parent <xref:System.Windows.Forms.GroupBox> contrôle. Déplacer le <xref:System.Windows.Forms.Button> contrôles autour pour voir comment les lignes d’alignement franchissent les limites du conteneur.  
  
-   Créer une colonne de <xref:System.Windows.Forms.TextBox> contrôles et une colonne correspondante de <xref:System.Windows.Forms.Label> contrôles. Définir la valeur de la <xref:System.Windows.Forms.Label> contrôles <xref:System.Windows.Forms.Control.AutoSize%2A> propriété `true`. Permet de déplacer les lignes d’alignement le <xref:System.Windows.Forms.Label> contrôle afin que leur texte affiché soit aligné avec le texte dans le <xref:System.Windows.Forms.TextBox> contrôles.  
  
 Pour plus d’informations sur la conception de l’interface utilisateur Windows, consultez le manuel *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA : Microsoft Press, 1999. (USBN : 0-7356-0566-1).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)  
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)
