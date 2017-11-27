---
title: "Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], arranging with TableLayoutPanel
- TableLayoutPanel control [Windows Forms], walkthroughs
- Windows Forms controls, arranging
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b2d5c07be4ddebc3bfaa8c1979b39e3ef172a428
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel"></a>Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel
Certaines applications exigent un formulaire dont la disposition s’organise de manière appropriée à mesure que le formulaire est redimensionné ou que le contenu change de taille. Si vous avez besoin d’une disposition dynamique et que vous ne souhaitez pas gérer les événements <xref:System.Windows.Forms.Control.Layout> explicitement dans votre code, envisagez d’utiliser un panneau de disposition.  
  
 Les contrôles <xref:System.Windows.Forms.FlowLayoutPanel> et <xref:System.Windows.Forms.TableLayoutPanel> vous permettent d’organiser de manière intuitive les contrôles sur votre formulaire. Tous deux vous permettent de contrôler automatiquement et de configurer la position relative des contrôles enfants qu’ils contiennent, et l’un et l’autre proposent des fonctionnalités de disposition dynamique au moment de l’exécution qui leur permettent de redimensionner et repositionner les contrôles enfants à mesure que les dimensions du formulaire parent changent. Les panneaux de disposition peuvent être imbriqués dans d’autres panneaux de disposition, ce qui permet de créer des interfaces utilisateur sophistiquées.  
  
 <xref:System.Windows.Forms.FlowLayoutPanel> organise son contenu dans un sens de flux spécifique : horizontal ou vertical. Vous pouvez encapsuler son contenu d'une ligne à la suivante ou d'une colonne à la suivante. Vous pouvez également découper son contenu au lieu de l'encapsuler. Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 Le <xref:System.Windows.Forms.TableLayoutPanel> réorganise son contenu dans une grille, en fournissant des fonctionnalités similaires à l’élément HTML \<table > élément. Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet de placer des contrôles dans une disposition en grille sans avoir à spécifier précisément la position de chaque contrôle. Ses cellules sont organisées dans des lignes et des colonnes dont la taille peut varier. Les cellules peuvent être fusionnés dans les lignes et colonnes. Cellules peuvent contenir tout élément à un formulaire peut contenir et se comportent dans la plupart des autres égards comme des conteneurs.  
  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle fournit également une fonction de redimensionnement proportionnel au moment de l’exécution pour permettre à votre disposition de modifier facilement lorsque votre formulaire est redimensionné. Cela rend la <xref:System.Windows.Forms.TableLayoutPanel> contrôle convient particulièrement pour des opérations telles que les formulaires de saisie de données et les applications localisées. Pour plus d’informations, consultez [procédure pas à pas : création d’un Windows Form redimensionnable pour l’entrée de données](http://msdn.microsoft.com/en-us/e193b4fc-912a-4917-b036-b76c7a6f58ab) et [procédure pas à pas : création d’un formulaire Windows localisable](http://msdn.microsoft.com/en-us/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 En règle générale, vous ne devez pas utiliser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle comme conteneur pour la disposition entière. Utilisez <xref:System.Windows.Forms.TableLayoutPanel> pour fournir des fonctions de redimensionnement proportionnel aux parties de la disposition des contrôles.  
  
 Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
-   Création d’un projet Windows Forms  
  
-   Organisation des contrôles dans des lignes et colonnes  
  
-   Ligne de paramètre et les propriétés de colonne  
  
-   Étendue de lignes et colonnes avec un contrôle  
  
-   Gestion automatique des dépassements de capacité  
  
-   Insertion de contrôles en double-cliquant dessus dans la boîte à outils  
  
-   Insertion d’un contrôle en dessinant son contour  
  
-   Réassignation de contrôles existants à un parent différent  
  
 À l’issue de cette procédure, vous comprendrez le rôle joué par ces fonctionnalités de disposition importantes.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet et à configurer le formulaire.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
1.  Créez un projet d’Application Windows appelé « TableLayoutPanelExample ». Pour plus d’informations, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) .  
  
2.  Sélectionnez le formulaire dans le **Windows** **Concepteur Forms**.  
  
## <a name="arranging-controls-in-rows-and-columns"></a>Organisation des contrôles dans des lignes et colonnes  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet de réorganiser facilement des contrôles en lignes et colonnes.  
  
#### <a name="to-arrange-controls-in-rows-and-columns-using-a-tablelayoutpanel"></a>Pour disposer les contrôles dans des lignes et colonnes à l’aide d’un TableLayoutPanel  
  
1.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire. Notez que, par défaut, le <xref:System.Windows.Forms.TableLayoutPanel> contrôle comporte quatre cellules.  
  
2.  Faites glisser un <xref:System.Windows.Forms.Button> contrôler à partir de la **boîte à outils** dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôler et déposez-le dans une des cellules. Notez que le <xref:System.Windows.Forms.Button> contrôle est créé dans la cellule sélectionnée.  
  
3.  Faites glisser trois autres <xref:System.Windows.Forms.Button> des contrôles de la **boîte à outils** dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôler, afin que chaque cellule contienne un bouton.  
  
4.  Saisissez la poignée de redimensionnement verticale entre les deux colonnes et déplacez-le vers la gauche. Notez que la <xref:System.Windows.Forms.Button> contrôles dans la première colonne sont redimensionnés à une plus petite largeur, lors de la taille de la <xref:System.Windows.Forms.Button> des contrôles dans la deuxième colonne est inchangée.  
  
5.  Saisissez la poignée de redimensionnement verticale entre les deux colonnes et déplacez-le vers la droite. Notez que la <xref:System.Windows.Forms.Button> contrôles dans la première colonne retournent à leur taille d’origine, tandis que le <xref:System.Windows.Forms.Button> contrôles dans la deuxième colonne sont déplacés vers la droite.  
  
6.  Déplacer la poignée de redimensionnement horizontal pour voir les effets sur les contrôles dans le panneau de configuration.  
  
## <a name="positioning-controls-within-cells-using-docking-and-anchoring"></a>Positionnement des contrôles dans les cellules à l’aide d’ancrage  
 Le comportement d’ancrage des contrôles enfants dans un <xref:System.Windows.Forms.TableLayoutPanel> diffère du comportement des autres contrôles conteneurs. Le comportement d’ancrage des contrôles enfants est le même que d’autres contrôles conteneur.  
  
#### <a name="positioning-controls-within-cells"></a>Positionnement des contrôles dans les cellules  
  
1.  Sélectionnez le premier <xref:System.Windows.Forms.Button> contrôle. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Dock%2A> par <xref:System.Windows.Forms.DockStyle.Fill>. Notez que le <xref:System.Windows.Forms.Button> contrôle se développe pour remplir sa cellule.  
  
2.  Sélectionnez une des autres <xref:System.Windows.Forms.Button> contrôles. Remplacez la valeur de sa propriété <xref:System.Windows.Forms.Control.Anchor%2A> par <xref:System.Windows.Forms.AnchorStyles.Right>. Notez qu’il est déplacé afin que sa bordure droite soit près de la bordure droite de la cellule. La distance entre les bordures est la somme de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Margin%2A> propriété et du panneau <xref:System.Windows.Forms.Control.Padding%2A> propriété.  
  
3.  Modifiez la valeur de la <xref:System.Windows.Forms.Button> du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété <xref:System.Windows.Forms.AnchorStyles.Right> et <xref:System.Windows.Forms.AnchorStyles.Left>. Notez que le contrôle est dimensionné à la largeur de la cellule, avec les <xref:System.Windows.Forms.Control.Margin%2A> et <xref:System.Windows.Forms.Control.Padding%2A> valeurs prises en compte.  
  
4.  Répétez les étapes 2 et 3 avec le <xref:System.Windows.Forms.AnchorStyles.Top> et <xref:System.Windows.Forms.AnchorStyles.Bottom> styles.  
  
## <a name="setting-row-and-column-properties"></a>Ligne de paramètre et les propriétés de colonne  
 Vous pouvez définir des propriétés individuelles de lignes et colonnes à l’aide de la <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> et <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collections.  
  
#### <a name="to-set-row-and-column-properties"></a>Pour définir les propriétés de ligne et de colonne  
  
1.  Sélectionnez le <xref:System.Windows.Forms.TableLayoutPanel> contrôler dans le **Concepteur Windows Forms**.  
  
2.  Dans le **propriétés** windows, ouvrez le <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection en cliquant sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) bouton à côté du **colonnes** entrée.  
  
3.  Sélectionnez la première colonne et modifiez la valeur de sa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété <xref:System.Windows.Forms.SizeType.AutoSize>. Cliquez sur **OK** pour accepter la modification. Notez que la largeur de la première colonne est réduite pour s’ajuster à la <xref:System.Windows.Forms.Button> contrôle. Notez également que la largeur de la colonne n’est pas redimensionnable.  
  
4.  Dans le **propriétés** fenêtre, ouvrez le <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection et sélectionnez la première colonne. Modifiez la valeur de sa <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété <xref:System.Windows.Forms.SizeType.Percent>. Cliquez sur **OK** pour accepter la modification. Redimensionner le <xref:System.Windows.Forms.TableLayoutPanel> le contrôle à une plus grande largeur et remarquez que la largeur de la première colonne se développe. Redimensionner le <xref:System.Windows.Forms.TableLayoutPanel> le contrôle à une plus petite largeur et remarquez que les boutons de la première colonne sont dimensionnés pour s’ajuster à la cellule. Notez également que la largeur de la colonne est redimensionnable.  
  
5.  Dans le **propriétés** fenêtre, ouvrez le <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> collection et sélectionnez toutes les colonnes répertoriées. Définir la valeur de chaque <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> propriété <xref:System.Windows.Forms.SizeType.Percent>. Cliquez sur **OK** pour accepter la modification. Répétez l’opération avec le <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> collection.  
  
6.  Saisissez une des poignées de redimensionnement et de redimensionner la largeur et la hauteur de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez que les lignes et colonnes sont redimensionnés en tant que le <xref:System.Windows.Forms.TableLayoutPanel> modifications de la taille du contrôle. Notez également que les lignes et colonnes sont redimensionnables avec horizontal et vertical de poignées de redimensionnement.  
  
## <a name="spanning-rows-and-columns-with-a-control"></a>Étendue de lignes et colonnes avec un contrôle  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle ajoute plusieurs nouvelles propriétés aux contrôles au moment du design. Deux de ces propriétés sont `RowSpan` et `ColumnSpan`. Vous pouvez utiliser ces propriétés pour définir un intervalle de contrôle plus d’une ligne ou une colonne.  
  
#### <a name="to-span-rows-and-columns-with-a-control"></a>Pour étendre des lignes et colonnes avec un contrôle  
  
1.  Sélectionnez le <xref:System.Windows.Forms.Button> contrôle dans la première ligne et la première colonne.  
  
2.  Dans le **propriétés** windows, remplacez la valeur de la `ColumnSpan` propriété **2**. Notez que le <xref:System.Windows.Forms.Button> contrôle remplit la première colonne et la deuxième colonne. Notez également qu’une ligne supplémentaire a été ajoutée pour prendre en charge cette modification.  
  
3.  Répétez l’étape 2 pour le `RowSpan` propriété.  
  
## <a name="inserting-controls-by-double-clicking-them-in-the-toolbox"></a>Insertion de contrôles en double-cliquant dessus dans la boîte à outils  
 Vous pouvez remplir votre <xref:System.Windows.Forms.TableLayoutPanel> contrôle en double-cliquant sur les contrôles dans le **boîte à outils**.  
  
#### <a name="to-insert-controls-by-double-clicking-in-the-toolbox"></a>Pour insérer des contrôles en double-cliquant dessus dans la boîte à outils  
  
1.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Double-cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> dans la **boîte à outils**. Notez qu’un nouveau contrôle de bouton apparaît dans le <xref:System.Windows.Forms.TableLayoutPanel> première cellule du contrôle.  
  
3.  Double-cliquez sur plusieurs autres contrôles dans la **boîte à outils**. Notez que les nouveaux contrôles apparaissent successivement dans le <xref:System.Windows.Forms.TableLayoutPanel> cellules inoccupé du contrôle. Notez également que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle s’étend pour prendre en charge les nouveaux contrôles si aucune cellule ouverte n’est disponible.  
  
## <a name="automatic-handling-of-overflows"></a>Gestion automatique des dépassements de capacité  
 Lorsque vous insérez des contrôles dans le <xref:System.Windows.Forms.TableLayoutPanel> (contrôle), vous pouvez exécuter en dehors des cellules vides pour vos nouveaux contrôles. Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle gère cette situation automatiquement en augmentant le nombre de cellules.  
  
#### <a name="to-observe-automatic-handling-of-overflows"></a>Pour observer la gestion automatique des dépassements de capacité  
  
1.  S’il existe encore des cellules vides dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôler, continuez à insérer de nouveaux <xref:System.Windows.Forms.Button> contrôle jusqu'à ce que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle est plein.  
  
2.  Une fois la <xref:System.Windows.Forms.TableLayoutPanel> contrôle est plein, double-cliquez sur le <xref:System.Windows.Forms.Button> icône dans le **boîte à outils** pour insérer un autre <xref:System.Windows.Forms.Button> contrôle. Notez que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle crée de nouvelles cellules pour tenir compte du nouveau contrôle. Insérer d’autres contrôles et observez le comportement de redimensionnement.  
  
3.  Affectez la valeur <xref:System.Windows.Forms.TableLayoutPanelGrowStyle.FixedSize> à la propriété <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanel>. Double-cliquez sur le <xref:System.Windows.Forms.Button> icône dans le **boîte à outils** à insérer <xref:System.Windows.Forms.Button> contrôle jusqu'à ce que le <xref:System.Windows.Forms.TableLayoutPanel> contrôle est plein. Double-cliquez sur le <xref:System.Windows.Forms.Button> icône dans le **boîte à outils** à nouveau. Notez que vous recevez un message d’erreur à partir de la **Concepteur Windows Forms** vous informant que les lignes et colonnes supplémentaires ne peut pas être créés.  
  
## <a name="inserting-a-control-by-drawing-its-outline"></a>Insertion d’un contrôle en dessinant son contour  
 Vous pouvez insérer un contrôle dans un <xref:System.Windows.Forms.TableLayoutPanel> contrôler et spécifier sa taille en dessinant son contour dans une cellule.  
  
#### <a name="to-insert-a-control-by-drawing-its-outline"></a>Pour insérer un contrôle en dessinant son contour  
  
1.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Dans la **boîte à outils**, cliquez sur l’icône de contrôle <xref:System.Windows.Forms.Button> . Ne la faites pas glisser sur le formulaire.  
  
3.  Déplacez le pointeur de la souris sur le <xref:System.Windows.Forms.TableLayoutPanel> contrôle. Notez que le pointeur devient une croix à laquelle est attachée l’icône de contrôle <xref:System.Windows.Forms.Button> .  
  
4.  Cliquez et maintenez le bouton de la souris enfoncé.  
  
5.  Faites glisser le pointeur de la souris pour tracer le contour du contrôle <xref:System.Windows.Forms.Button> . Quand la taille vous convient, relâchez le bouton de la souris. Notez que le <xref:System.Windows.Forms.Button> contrôle est créé dans la cellule dans laquelle vous avez dessiné le plan du contrôle.  
  
## <a name="multiple-controls-within-cells-are-not-permitted"></a>Plusieurs contrôles dans les cellules ne sont pas autorisées.  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle peut contenir uniquement un seul contrôle enfant par cellule.  
  
#### <a name="to-demonstrate-that-multiple-controls-within-cells-are-not-permitted"></a>Pour illustrer que plusieurs contrôles dans les cellules ne sont pas autorisées  
  
-   Faites glisser un <xref:System.Windows.Forms.Button> contrôle depuis la **boîte à outils** dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôler et déposez-le dans une des cellules occupées. Notez que la <xref:System.Windows.Forms.TableLayoutPanel> contrôle ne vous permet pas de supprimer le <xref:System.Windows.Forms.Button> contrôle dans la cellule occupée.  
  
## <a name="swapping-controls"></a>Échange de contrôles  
 Le <xref:System.Windows.Forms.TableLayoutPanel> contrôle vous permet d’échanger des contrôles occupée par les deux cellules différentes.  
  
#### <a name="to-swap-controls"></a>Permutation des contrôles  
  
-   Faites glisser un de le <xref:System.Windows.Forms.Button> contrôles cellule occupée et déposez-le sur une autre cellule occupée. Notez que les deux contrôles sont déplacés à partir d’une cellule dans l’autre.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous pouvez obtenir une disposition complexe en combinant plusieurs contrôles et panneaux de disposition. Voici quelques suggestions à explorer :  
  
-   Essayez de redimensionner l’un de le <xref:System.Windows.Forms.Button> à une taille plus grande et notez l’effet sur la disposition des contrôles.  
  
-   Collez une sélection de plusieurs contrôles dans le <xref:System.Windows.Forms.TableLayoutPanel> contrôler et notez la façon dont les contrôles sont insérés.  
  
-   Les panneaux de disposition peuvent contenir d’autres panneaux de disposition. Faites l’expérience de déposer un contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle existant.  
  
-   Ancrer le <xref:System.Windows.Forms.TableLayoutPanel> contrôle au formulaire parent. Redimensionnez le formulaire et observez-en l’effet sur la disposition.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide d’un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Expérience utilisateur Microsoft Windows, Recommandations officielles à destination des développeurs et des concepteurs d’interfaces utilisateur. Redmond, WA: Microsoft Press, 1999. (USBN : 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)  
 [Procédure pas à pas : création d’un Windows Form redimensionnable pour l’entrée de données](http://msdn.microsoft.com/en-us/e193b4fc-912a-4917-b036-b76c7a6f58ab)  
 [Procédure pas à pas : Création d’un formulaire Windows localisable](http://msdn.microsoft.com/en-us/c5240b6e-aaca-4286-9bae-778a416edb9c)  
 [Meilleures pratiques pour le contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)  
 [Vue d’ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [Guide pratique pour fixer des contrôles sur des Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [Guide pratique pour ancrer des contrôles sur des Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)
