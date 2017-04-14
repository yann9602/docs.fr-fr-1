---
title: "Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les dans les Windows Forms &#224; l&#39;aide d&#39;un TableLayoutPanel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "contrôles (Windows Forms), disposer avec TableLayoutPanel"
  - "TableLayoutPanel (contrôle Windows Forms), procédures pas à pas"
  - "contrôles Windows Forms, réorganiser"
ms.assetid: d474885e-12cc-4ab7-b997-2a23a643049b
caps.latest.revision: 28
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 28
---
# Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les dans les Windows Forms &#224; l&#39;aide d&#39;un TableLayoutPanel
Certaines applications exigent un formulaire dont la disposition se réorganise de manière appropriée lorsque le formulaire est redimensionné ou lorsque la taille de son contenu change.  Lorsque vous avez besoin d'une disposition dynamique et que vous ne souhaitez pas gérer explicitement des événements <xref:System.Windows.Forms.Control.Layout> dans votre code, pensez à utiliser un panneau de disposition.  
  
 Le contrôle <xref:System.Windows.Forms.FlowLayoutPanel> et le contrôle <xref:System.Windows.Forms.TableLayoutPanel> offrent des moyens intuitifs de réorganisation des contrôles sur votre formulaire.  Les deux fournissent la capacité automatique et configurable de contrôler les positions relatives des contrôles enfants qu'ils contiennent, et les deux offrent des fonctions de disposition dynamique au moment de l'exécution ; ils peuvent donc redimensionner et repositionner les contrôles enfants lorsque les dimensions du formulaire parent changent.  Les panneaux de disposition peuvent être imbriqués dans des panneaux de disposition pour permettre la réalisation d'interfaces utilisateur sophistiquées.  
  
 Le <xref:System.Windows.Forms.FlowLayoutPanel> réorganise son contenu dans un sens spécifique du flux : horizontal ou vertical.  Son contenu peut être encapsulé d'une ligne à la suivante, ou d'une colonne à la suivante.  Alternativement, son contenu peut être découpé au lieu d'être encapsulé.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md).  
  
 Le <xref:System.Windows.Forms.TableLayoutPanel> réorganise son contenu dans une grille, en fournissant ainsi des fonctionnalités semblables à l'élément HTML \<table\>.  Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> vous permet de placer des contrôles dans une présentation grille sans requérir que vous spécifiiez précisément la position de chaque contrôle individuel.  Ses cellules sont disposées en lignes et colonnes, et ceux\-ci peuvent avoir des tailles différentes.  Les cellules peuvent être fusionnées à travers les lignes et colonnes.  Les cellules peuvent contenir tout ce qu'un formulaire peut contenir et se comportent dans la plupart des cas comme des conteneurs.  
  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> fournit également une fonction de redimensionnant proportionnel au moment de l'exécution ; votre disposition peut donc changer doucement lorsque votre formulaire est redimensionné.  Cela rend le contrôle <xref:System.Windows.Forms.TableLayoutPanel> parfaitement adapté aux objectifs tels que les formulaires de saisie de données et les applications localisées.  Pour plus d'informations, consultez [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/fr-fr/e193b4fc-912a-4917-b036-b76c7a6f58ab) et [Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/fr-fr/c5240b6e-aaca-4286-9bae-778a416edb9c).  
  
 En général, vous ne devez pas utiliser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> comme conteneur pour la disposition entière.  Utilisez des contrôles <xref:System.Windows.Forms.TableLayoutPanel> pour fournir des fonctions de redimensionnant proportionnel aux parties de la disposition.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms  
  
-   Réorganisation des contrôles dans les lignes et les colonnes  
  
-   Définition des propriétés des lignes et des colonnes  
  
-   Étendue de lignes et de colonnes avec un contrôle  
  
-   Gestion automatique des dépassements de capacité  
  
-   Insertion de contrôles par un double\-clic dans la boîte à outils  
  
-   Insertion d'un contrôle en dessinant son plan  
  
-   Réassignation de contrôles existants à un parent différent  
  
 Lorsque vous aurez terminé, vous aurez assimilé le fonctionnement du rôle joué par ces importantes fonctionnalités de disposition.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé « TableLayoutPanelExample ».  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le **Concepteur Windows** **Forms**.  
  
## Réorganisation des contrôles dans les lignes et les colonnes  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> vous permet de réorganiser facilement des contrôles dans les lignes et colonnes.  
  
#### Pour réorganiser des contrôles dans les lignes et les colonnes à l'aide d'un TableLayoutPanel  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  Notez que, par défaut, le contrôle <xref:System.Windows.Forms.TableLayoutPanel> a quatre cellules.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel> et déposez\-le dans l'une des cellules.  Notez que le contrôle <xref:System.Windows.Forms.Button> est créé dans la cellule que vous avez sélectionnée.  
  
3.  Faites glisser trois autres contrôles <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel>, afin que chaque cellule contienne un bouton.  
  
4.  Attrapez la poignée de redimensionnement verticale entre les deux colonnes et déplacez\-la à gauche.  Notez que les contrôles <xref:System.Windows.Forms.Button> dans la première colonne sont redimensionnés selon une plus petite largeur, alors que la taille des contrôles <xref:System.Windows.Forms.Button> dans la deuxième colonne est inchangée.  
  
5.  Attrapez la poignée de redimensionnement verticale entre les deux colonnes et déplacez\-la à droite.  Notez que les contrôles <xref:System.Windows.Forms.Button> dans la première colonne retournent à leur taille d'origine, alors que les contrôles <xref:System.Windows.Forms.Button> dans la deuxième colonne sont déplacés à droite.  
  
6.  Déplacez la poignée de redimensionnement horizontale vers le haut et le bas pour constater l'effet sur les contrôles dans le panneau.  
  
## Positionnement des contrôles dans les cellules à l'aide de l'amarrage et de l'ancrage  
 Le comportement d'ancrage des contrôles enfants dans un <xref:System.Windows.Forms.TableLayoutPanel> diffère du comportement dans d'autres contrôles conteneur.  Le comportement d'amarrage des contrôles enfants est le même que d'autres contrôles conteneur.  
  
#### Positionnement des contrôles dans les cellules  
  
1.  Sélectionnez le premier contrôle <xref:System.Windows.Forms.Button>.  Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  Notez que le contrôle <xref:System.Windows.Forms.Button> se développe pour remplir sa cellule.  
  
2.  Sélectionnez l'un des autres contrôles <xref:System.Windows.Forms.Button>.  Affectez à sa propriété <xref:System.Windows.Forms.Control.Anchor%2A> la valeur <xref:System.Windows.Forms.AnchorStyles>.  Notez qu'il est déplacé afin que sa bordure droite soit près de la bordure droite de la cellule.  La distance entre les bordures est la somme de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle <xref:System.Windows.Forms.Button> et de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du panneau.  
  
3.  Attribuez à la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle <xref:System.Windows.Forms.Button> les valeurs <xref:System.Windows.Forms.AnchorStyles> et <xref:System.Windows.Forms.AnchorStyles>.  Notez que le contrôle est dimensionné selon la largeur de la cellule, avec les valeurs <xref:System.Windows.Forms.Control.Margin%2A> et <xref:System.Windows.Forms.Control.Padding%2A> prises en considération.  
  
4.  Répétez les étapes 2 et 3 avec les styles <xref:System.Windows.Forms.AnchorStyles> et <xref:System.Windows.Forms.AnchorStyles>.  
  
## Définition des propriétés des lignes et des colonnes  
 Vous pouvez définir des propriétés individuelles de lignes et colonnes en utilisant les collections <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> et <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>.  
  
#### Pour définir des propriétés de lignes et de colonnes  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans le **Concepteur Windows Forms**.  
  
2.  Dans les fenêtres **Propriétés**, ouvrez la collection <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> en cliquant sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) à côté de l'entrée **Colonnes**.  
  
3.  Sélectionnez la première colonne et modifiez la valeur de sa propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> en <xref:System.Windows.Forms.SizeType>.  Cliquez sur **OK** pour accepter les modifications.  Notez que la largeur de la première colonne est réduite pour contenir le contrôle <xref:System.Windows.Forms.Button>.  Notez également que la largeur de la colonne n'est pas redimensionnable.  
  
4.  Dans la fenêtre **Propriétés**, ouvrez la collection <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> et sélectionnez la première colonne.  Affectez à sa propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> la valeur <xref:System.Windows.Forms.SizeType>.  Cliquez sur **OK** pour accepter les modifications.  Redimensionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> à une plus grande largeur et remarquez que la largeur de la première colonne se développe.  Redimensionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> à une plus petite largeur et remarquez que les boutons dans la première colonne sont dimensionnés de façon à tenir dans la cellule.  Notez également que la largeur de la colonne est redimensionnable.  
  
5.  Dans la fenêtre **Propriétés**, ouvrez la collection <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A> et sélectionnez toutes les colonnes répertoriées.  Affectez à chaque propriété <xref:System.Windows.Forms.TableLayoutStyle.SizeType%2A> la valeur <xref:System.Windows.Forms.SizeType>.  Cliquez sur **OK** pour accepter les modifications.  Répétez avec la collection <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A>.  
  
6.  Saisissez l'une des poignées de redimensionnement et redimensionnez à la fois la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Notez que les lignes et les colonnes sont redimensionnées lorsque la taille de contrôle <xref:System.Windows.Forms.TableLayoutPanel> change.  Notez également que les lignes et les colonnes sont redimensionnables avec les poignées de dimensionnement horizontale et verticale.  
  
## Étendue de lignes et de colonnes avec un contrôle  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ajoute plusieurs nouvelles propriétés aux contrôles au moment du design.  `RowSpan` et `ColumnSpan` sont deux de ces propriétés.  Vous pouvez utiliser ces propriétés pour étendre un contrôle sur plusieurs lignes ou colonnes.  
  
#### Pour couvrir plusieurs lignes et des colonnes avec un contrôle  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.Button> dans la première ligne et la première colonne.  
  
2.  Dans la fenêtre **Propriétés**, remplacez la valeur de la propriété `ColumnSpan` par 2.  Notez que le contrôle <xref:System.Windows.Forms.Button> remplit la première colonne et la deuxième colonne.  Notez également qu'une ligne supplémentaire a été ajoutée pour tenir compte de cette modification.  
  
3.  Répétez l'étape 2 pour la propriété `RowSpan`.  
  
## Insertion de contrôles par un double\-clic dans la boîte à outils  
 Vous pouvez remplir votre <xref:System.Windows.Forms.TableLayoutPanel> contrôle en double\-cliquant sur les contrôles de la **Boîte à outils**.  
  
#### Pour insérer des contrôles par un double\-clic dans la boîte à outils  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Double\-cliquez sur l'icône du contrôle <xref:System.Windows.Forms.Button> dans la **Boîte à outils**.  Notez qu'un nouveau contrôle de bouton apparaît dans la première cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  Double\-cliquez sur plusieurs autres contrôles dans la **Boîte à outils**.  Notez que les nouveaux contrôles apparaissent successivement dans les cellules inoccupées du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Notez également que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> se développe pour tenir compte des nouveaux contrôles si aucune cellule ouverte n'est disponible.  
  
## Gestion automatique des dépassements de capacité  
 Lorsque vous insérez des contrôles dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>, vous pouvez manquer de cellules vides pour vos nouveaux contrôles.  Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> gère cette situation automatiquement en augmentant le nombre de cellules.  
  
#### Pour observer la gestion automatique des dépassements de capacité  
  
1.  S'il y a encore des cellules vides dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>, continuez à insérer de nouveaux contrôles <xref:System.Windows.Forms.Button> jusqu'à ce que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> soit complet.  
  
2.  Une fois que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> est complet, double\-cliquez sur l'icône <xref:System.Windows.Forms.Button> dans la **Boîte à outils** pour insérer un autre contrôle <xref:System.Windows.Forms.Button>.  Notez que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> crée de nouvelles cellules pour tenir compte du nouveau contrôle.  Insérez d'autres contrôles et observez le comportement de redimensionnement.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A> du contrôle <xref:System.Windows.Forms.TableLayoutPanel> la valeur <xref:System.Windows.Forms.TableLayoutPanelGrowStyle>.  Double\-cliquez sur l'icône <xref:System.Windows.Forms.Button> dans la **Boîte à outils** pour insérer des contrôles <xref:System.Windows.Forms.Button> jusqu'à ce que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> soit complet.  Double\-cliquez de nouveau sur l'icône <xref:System.Windows.Forms.Button> dans la **Boîte à outils**.  Remarquez que vous obtenez un message d'erreur du **Concepteur Windows Forms** qui vous informe qu'il n'est pas possible de créer des lignes et des colonnes supplémentaires.  
  
## Insertion d'un contrôle en dessinant son plan  
 Vous pouvez insérer un contrôle dans un contrôle <xref:System.Windows.Forms.TableLayoutPanel> et spécifier sa taille en dessinant son plan dans une cellule.  
  
#### Pour insérer un contrôle en dessinant son plan  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Dans la **Boîte à outils**, cliquez sur l'icône du contrôle <xref:System.Windows.Forms.Button>.  Ne le faites pas glisser sur le formulaire.  
  
3.  Placez le pointeur de la souris sur le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Notez que le pointeur se transforme en croix avec l'icône du contrôle <xref:System.Windows.Forms.Button> jointe.  
  
4.  Cliquez et maintenez le bouton de la souris enfoncé.  
  
5.  Faites glisser le pointeur de la souris pour dessiner le plan du contrôle <xref:System.Windows.Forms.Button>.  Lorsque la taille vous convient, relâchez le bouton de souris.  Notez que le contrôle <xref:System.Windows.Forms.Button> est créé dans la cellule dans laquelle vous avez dessiné le plan du contrôle.  
  
## Les contrôles multiples dans les cellules ne sont pas autorisés  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ne peut contenir qu'un seul contrôle enfant par cellule.  
  
#### Pour montrer que les contrôles multiples dans les cellules ne sont pas autorisés  
  
-   Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel> et déposez\-le dans l'une des cellules occupées.  Notez que le contrôle <xref:System.Windows.Forms.TableLayoutPanel> ne vous permet pas de déposer le contrôle <xref:System.Windows.Forms.Button> dans la cellule occupée.  
  
## Échange de contrôles  
 Le contrôle <xref:System.Windows.Forms.TableLayoutPanel> vous permet d'échanger des contrôles qui occupent deux cellules différentes.  
  
#### Pour échanger des contrôles  
  
-   Faites glisser l'un des contrôles <xref:System.Windows.Forms.Button> d'une cellule occupée et déposez\-le sur une autre cellule occupée.  Notez que les deux contrôles sont déplacés d'une cellule dans l'autre.  
  
## Étapes suivantes  
 Vous pouvez obtenir une disposition complexe à l'aide d'une combinaison de panneaux de disposition et de contrôles.  Voici quelques suggestions pour une exploration plus approfondie :  
  
-   Essayez de redimensionner l'un des contrôles <xref:System.Windows.Forms.Button> à une plus grande taille et notez l'effet produit sur la disposition.  
  
-   Collez une sélection de plusieurs contrôles dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel> et notez comment les contrôles sont insérés.  
  
-   Les panneaux de disposition peuvent contenir d'autres panneaux de disposition.  Essayez de déposer un contrôle <xref:System.Windows.Forms.TableLayoutPanel> dans le contrôle existant.  
  
-   Ancrez le contrôle <xref:System.Windows.Forms.TableLayoutPanel> au formulaire parent.  Redimensionnez le formulaire et notez l'effet produit sur la disposition.  
  
## Voir aussi  
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 <xref:System.Windows.Forms.TableLayoutPanel>   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. \(USBN: 0\-7356\-0566\-1\)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)   
 [Walkthrough: Creating a Resizable Windows Form for Data Entry](http://msdn.microsoft.com/fr-fr/e193b4fc-912a-4917-b036-b76c7a6f58ab)   
 [Walkthrough: Creating a Localizable Windows Form](http://msdn.microsoft.com/fr-fr/c5240b6e-aaca-4286-9bae-778a416edb9c)   
 [Meilleures pratiques pour le contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)   
 [Vue d'ensemble de la propriété AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md)   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)   
 [Comment : ancrer des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)   
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)