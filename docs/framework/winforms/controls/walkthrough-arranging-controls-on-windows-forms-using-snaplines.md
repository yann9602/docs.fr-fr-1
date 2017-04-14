---
title: "Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les dans les Windows Forms &#224; l&#39;aide des lignes d&#39;alignement (SnapLines) | Microsoft Docs"
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
  - "contrôles (Windows Forms), disposer avec les lignes d'alignement"
  - "SnapLine (classe), procédures pas à pas"
  - "lignes d'alignement, disposer les contrôles Windows Forms"
  - "contrôles Windows Forms, réorganiser"
ms.assetid: d5c9edc7-cf30-4a97-8ebe-201d569340f8
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Proc&#233;dure pas &#224; pas&#160;: organisation des contr&#244;les dans les Windows Forms &#224; l&#39;aide des lignes d&#39;alignement (SnapLines)
Le positionnement précis des contrôles sur votre formulaire est une haute priorité pour beaucoup d'applications.  Le Concepteur Windows Forms vous propose beaucoup d'outils de disposition pour accomplir cette opération.  L'un des plus importants est la fonctionnalité <xref:System.Windows.Forms.Design.Behavior.SnapLine>.  
  
 Les lignes d'alignement \(SnapLines\) vous indiquent précisément où aligner des contrôles avec d'autres contrôles.  Elles vous indiquent également les distances recommandées pour les marges entre les contrôles, comme spécifié par les indications de l'interface utilisateur de Windows.  Pour plus d'informations, consultez [Conception et développement d'une interface utilisateur \(page éventuellement en anglais\)](http://go.microsoft.com/FWLink/?LinkId=83878).  
  
 Avec les lignes d'alignement \(SnapLines\), il est plus facile d'aligner vos contrôles pour obtenir une apparence et un comportement impeccables et professionnels.  
  
 Cette procédure pas à pas illustre les tâches suivantes :  
  
-   Création d'un projet Windows Forms  
  
-   Espacement et alignement des contrôles à l'aide des lignes d'alignement \(SnapLines\)  
  
-   Alignement selon les marges du contrôle et du conteneur  
  
-   Alignement selon des contrôles regroupés  
  
-   Utilisation des lignes d'alignement \(SnapLines\) pour placer un contrôle en dessinant sa taille en mode plan  
  
-   Utilisation des lignes d'alignement \(SnapLines\) lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
-   Redimensionnement des contrôles à l'aide des lignes d'alignement \(SnapLines\)  
  
-   Alignement d'une étiquette sur le texte d'un contrôle  
  
-   Utilisation de lignes d'alignement \(SnapLines\) avec la navigation à l'aide du clavier  
  
-   Lignes d'alignement \(SnapLines\) et panneaux de disposition  
  
-   Désactivation des lignes d'alignement \(SnapLines\)  
  
 Lorsque vous aurez terminé, vous aurez assimilé le rôle de disposition joué par la fonctionnalité des lignes d'alignement \(SnapLines\).  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Création du projet  
 La première étape consiste à créer le projet et configurer le formulaire.  
  
#### Pour créer le projet  
  
1.  Créez un projet d'application Windows appelé « SnaplineExample ».  Pour plus d'informations, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  Sélectionnez le formulaire dans le Concepteur Forms.  
  
## Espacement et alignement des contrôles à l'aide des lignes d'alignement \(SnapLines\)  
 Les lignes d'alignement \(SnapLines\) vous offrent un moyen précis et intuitif d'aligner des contrôles sur votre formulaire.  Ils apparaissent lorsque vous déplacez un ou plusieurs contrôles sélectionnés près d'une position qui s'alignerait sur un autre contrôle ou jeu de contrôles.  Votre sélection s'alignera à la position suggérée comme si vous l'aviez déplacée devant les autres contrôles.  
  
#### Pour réorganiser des contrôles à l'aide de lignes d'alignement \(SnapLines\)  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
2.  Déplacez le contrôle <xref:System.Windows.Forms.Button> au coin inférieur droit du formulaire.  Notez les lignes d'alignement \(Snaplines\) qui apparaissent lorsque le contrôle <xref:System.Windows.Forms.Button> s'approche des bordures droite et inférieure du contrôle.  Ces lignes d'alignement \(SnapLines\) affichent la distance recommandée entre les bordures du contrôle et le formulaire.  
  
3.  Déplacez le contrôle <xref:System.Windows.Forms.Button> autour des bordures du formulaire et notez l'endroit où les lignes d'alignement \(SnapLines\) apparaissent.  Lorsque vous avez terminé, déplacez le contrôle <xref:System.Windows.Forms.Button> près du centre du formulaire.  
  
4.  Faites glisser un autre contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
5.  Déplacez le deuxième contrôle <xref:System.Windows.Forms.Button> jusqu'à ce qu'il soit presque au niveau du premier.  Notez la ligne d'alignement \(SnapLine\) qui apparaît à la ligne de base du texte des deux boutons, et remarquez que le contrôle que vous déplacez s'aligne à une position qui est exactement au niveau de l'autre contrôle.  
  
6.  Déplacez le deuxième contrôle <xref:System.Windows.Forms.Button> jusqu'à ce qu'il soit positionné directement au\-dessus du premier.  Notez les lignes d'alignement \(SnapLines\) qui apparaissent le long des bords gauche et droit des deux boutons, et remarquez que le contrôle que vous déplacez s'aligne à une position qui est alignée exactement avec l'autre contrôle.  
  
7.  Sélectionnez l'un des contrôles <xref:System.Windows.Forms.Button> et déplacez\-le à proximité de l'autre, jusqu'à ce qu'ils se touchent presque.  Notez la ligne d'alignement \(Snapline\) qui apparaît entre eux.  Cette distance est la distance recommandée entre les bordures des contrôles.  Notez également que le contrôle vous déplacez s'aligne à cette position.  
  
8.  Faites glisser deux contrôles <xref:System.Windows.Forms.Panel> de la **Boîte à outils** vers votre formulaire.  
  
9. Déplacez l'un des contrôles <xref:System.Windows.Forms.Panel> jusqu'à ce qu'il soit presque au niveau du premier.  Notez les lignes d'alignement \(SnapLines\) qui apparaissent le long des bords supérieur et inférieur des deux contrôles, et remarquez que le contrôle que vous déplacez s'aligne à une position qui est exactement au niveau de l'autre contrôle.  
  
## Alignement selon les marges du contrôle et du conteneur  
 Les lignes d'alignement \(SnapLines\) vous aident à aligner de façon cohérente vos contrôles sur les marges des formulaires et des conteneurs.  
  
#### Pour aligner des contrôles sur les marges de formulaires et de conteneurs  
  
1.  Sélectionnez l'un des contrôles <xref:System.Windows.Forms.Button> et déplacez\-le près de la bordure droite du formulaire jusqu'à ce qu'une ligne d'alignement \(SnapLine\) apparaisse.  La distance de la ligne d'alignement \(SnapLine\) par rapport à la bordure droite est la somme de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle et des valeurs de propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire.  
  
> [!NOTE]
>  Si la propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire a la valeur 0,0,0,0, le Concepteur Windows Forms affecte une valeur <xref:System.Windows.Forms.Control.Padding%2A> ombrée de 9,9,9,9 au formulaire.  Pour modifier ce comportement, assignez une valeur autre que 0,0,0,0.  
  
1.  Modifiez la valeur de la propriété <xref:System.Windows.Forms.Control.Margin%2A> du contrôle <xref:System.Windows.Forms.Button> en développant l'entrée <xref:System.Windows.Forms.Control.Margin%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 0.  Pour plus d'informations, consultez [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md).  
  
2.  Déplacez le contrôle <xref:System.Windows.Forms.Button> près de la bordure droite du formulaire jusqu'à ce qu'une ligne d'alignement \(SnapLine\) apparaisse.  Cette distance est maintenant indiquée par la valeur de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du formulaire.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **Boîte à outils** vers votre formulaire.  
  
4.  Modifiez la valeur de la propriété <xref:System.Windows.Forms.Control.Padding%2A> du contrôle <xref:System.Windows.Forms.GroupBox> en développant l'entrée <xref:System.Windows.Forms.Control.Padding%2A> dans la fenêtre **Propriétés** et en attribuant à la propriété <xref:System.Windows.Forms.Padding.All%2A> la valeur 10.  
  
5.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** jusqu'au contrôle <xref:System.Windows.Forms.GroupBox>.  
  
6.  Déplacez le contrôle <xref:System.Windows.Forms.Button> près de la bordure droite du contrôle <xref:System.Windows.Forms.GroupBox> jusqu'à ce qu'une ligne d'alignement \(SnapLine\) apparaisse.  Déplacez le contrôle <xref:System.Windows.Forms.Button> dans le contrôle <xref:System.Windows.Forms.GroupBox> et notez où les lignes d'alignement \(SnapLines\) apparaissent.  
  
## Alignement selon des contrôles regroupés  
 Vous pouvez utiliser des lignes d'alignement \(SnapLines\) pour aligner des contrôles regroupés aussi bien que des contrôles dans un contrôle <xref:System.Windows.Forms.GroupBox>.  
  
#### Pour aligner des contrôles regroupés  
  
1.  Sélectionnez deux des contrôles sur votre formulaire.  Déplacez la sélection autour et notez les lignes d'alignement \(SnapLines\) qui apparaissent entre votre sélection et les autres contrôles.  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.GroupBox> de la **Boîte à outils** vers votre formulaire.  
  
3.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** jusqu'au contrôle <xref:System.Windows.Forms.GroupBox>.  
  
4.  Sélectionnez l'un des contrôles <xref:System.Windows.Forms.Button> et déplacez\-le autour du contrôle <xref:System.Windows.Forms.GroupBox>.  Notez les lignes d'alignement \(SnapLines\) qui apparaissent aux bords du contrôle <xref:System.Windows.Forms.GroupBox>.  Notez également les lignes d'alignement \(SnapLines\) qui apparaissent aux bords du <xref:System.Windows.Forms.Button> contrôlent qui est contenu par le contrôle <xref:System.Windows.Forms.GroupBox>.  Les contrôles qui sont des enfants d'un contrôle conteneur prennent aussi en charge les lignes d'alignement \(SnapLines\).  
  
## Utilisation des lignes d'alignement \(SnapLines\) pour placer un contrôle en dessinant sa taille en mode plan  
 Les lignes d'alignement \(SnapLines\) vous aident à aligner des contrôles lorsque vous les placez la première fois sur un formulaire.  
  
#### Pour utiliser les lignes d'alignement \(SnapLines\) en vue de placer un contrôle en dessinant sa taille en mode plan  
  
1.  Dans la **Boîte à outils**, cliquez sur l'icône du contrôle <xref:System.Windows.Forms.Button>.  Ne le faites pas glisser sur le formulaire.  
  
2.  Déplacez le pointeur de la souris sur l'aire de conception du formulaire.  Notez que le pointeur se transforme en croix avec l'icône du contrôle <xref:System.Windows.Forms.Button> jointe.  Notez également les lignes d'alignement \(SnapLines\) qui apparaissent pour suggérer des positions alignées pour le contrôle <xref:System.Windows.Forms.Button>.  
  
3.  Cliquez et maintenez le bouton de la souris enfoncé.  
  
4.  Faites glisser le pointeur de la souris autour du formulaire.  Notez qu'un plan est dessiné, en indiquant la position et la taille du contrôle.  
  
5.  Faites glisser le pointeur jusqu'à ce qu'il s'aligne avec un autre contrôle sur le formulaire.  Notez qu'une ligne d'alignement \(SnapLine\) apparaît pour indiquer l'alignement.  
  
6.  Relâchez le bouton de la souris.  Le contrôle est créé selon la position et la taille indiquées par le plan.  
  
## Utilisation des lignes d'alignement \(SnapLines\) lorsque vous faites glisser un contrôle à partir de la boîte à outils  
 Les lignes d'alignement \(SnapLines\) vous aident à aligner des contrôles lorsque vous les faites glisser de la **Boîte à outils** sur votre formulaire.  
  
#### Pour utiliser des lignes d'alignement \(SnapLines\) lorsque vous faites glisser un contrôle à partir de la boîte à outils  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** sur votre formulaire, mais ne relâchez pas le bouton de souris.  
  
2.  Déplacez le pointeur de la souris sur l'aire de conception du formulaire.  Notez que le pointeur change pour indiquer la position à laquelle le nouveau contrôle <xref:System.Windows.Forms.Button> sera créé.  
  
3.  Faites glisser le pointeur de la souris autour du formulaire.  Notez les lignes d'alignement \(SnapLines\) qui apparaissent pour suggérer des positions alignées pour le contrôle <xref:System.Windows.Forms.Button>.  Recherchez une position qui est alignée avec d'autres contrôles.  
  
4.  Relâchez le bouton de la souris.  Le contrôle est créé à la position indiquée par les lignes d'alignement \(SnapLines\).  
  
## Redimensionnement des contrôles à l'aide des lignes d'alignement \(SnapLines\)  
 Les lignes d'alignement \(SnapLines\) vous aident à aligner des contrôles lorsque vous les redimensionnez.  
  
#### Pour redimensionner un contrôle à l'aide de lignes d'alignement \(SnapLines\)  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  
  
2.  Redimensionnez le contrôle <xref:System.Windows.Forms.Button> en saisissant l'une des poignées de redimensionnement et en la faisant glisser.  Pour plus d'informations, consultez [Comment : redimensionner des contrôles sur des Windows Forms](../../../../docs/framework/winforms/controls/how-to-resize-controls-on-windows-forms.md).  
  
3.  Faites glisser la poignée de redimensionnement jusqu'à ce que l'une des bordures du contrôle <xref:System.Windows.Forms.Button> soit alignée avec un autre contrôle.  Notez qu'une ligne d'alignement \(SnapLine\) apparaît.  Notez également que la poignée de redimensionnement s'aligne à la position indiquée par la ligne d'alignement \(SnapLine\).  
  
4.  Redimensionnez le contrôle <xref:System.Windows.Forms.Button> dans différentes directions et alignez la poignée de redimensionnement selon différents contrôles.  Notez comment les lignes d'alignement \(SnapLines\) apparaissent dans différentes orientations pour indiquer l'alignement.  
  
## Alignement d'une étiquette sur le texte d'un contrôle  
 Certains contrôles offrent une ligne d'alignement \(SnapLine\) pour aligner d'autres contrôles sur le texte affiché.  
  
#### Pour aligner une étiquette sur le texte d'un contrôle  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TextBox> de la **Boîte à outils** vers votre formulaire.  Lorsque vous déposez le contrôle <xref:System.Windows.Forms.TextBox> sur le formulaire, cliquez sur le glyphe de balise active et sélectionnez l'option **Définir textBox1 pour le texte**.  Pour plus d'informations, consultez [Procédure pas à pas : exécution de tâches courantes à l'aide de balises actives dans les contrôles Windows Forms](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md).  
  
2.  Faites glisser un contrôle <xref:System.Windows.Forms.Label> de la **Boîte à outils** vers votre formulaire.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Label> la valeur `true`.  Notez que les bordures du contrôle sont ajustées pour contenir le texte affiché.  
  
4.  Déplacez le contrôle <xref:System.Windows.Forms.Label> à gauche du contrôle <xref:System.Windows.Forms.TextBox> afin qu'il soit aligné avec le bord inférieur du contrôle <xref:System.Windows.Forms.TextBox>.  Notez la ligne d'alignement \(SnapLine\) qui apparaît le long des bords inférieurs des deux contrôles.  
  
5.  Déplacez le contrôle  <xref:System.Windows.Forms.Label>légèrement vers le haut, jusqu'à ce que le texte <xref:System.Windows.Forms.Label>et le texte <xref:System.Windows.Forms.TextBox> soient alignés.  Notez la ligne d'alignement \(SnapLine\) différemment mise en forme avec des styles qui apparaît, en indiquant quand les champs de texte des deux contrôles sont alignés.  
  
## Utilisation de lignes d'alignement \(SnapLines\) avec la navigation à l'aide du clavier  
 Les lignes d'alignement \(SnapLines\) vous aident à aligner des contrôles lorsque vous les réorganisez à l'aide des touches de direction du clavier.  
  
#### Pour utiliser des lignes d'alignement \(SnapLines\) avec la navigation par clavier  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers votre formulaire.  Placez\-le dans l'angle supérieur gauche du formulaire.  
  
2.  Appuyez sur CTRL\+BAS.  Notez que le contrôle se déplace vers le bas du formulaire jusqu'à la première position d'alignement horizontale disponible.  
  
3.  Appuyez sur CTRL\+BAS jusqu'à ce que le contrôle atteigne le bas du formulaire.  Notez les positions qu'il occupe à mesure qu'il descend dans le formulaire.  
  
4.  Appuyez sur CTRL\+DROITE.  Notez que le contrôle se déplace à travers le formulaire jusqu'à la première position d'alignement verticale disponible.  
  
5.  Appuyez sur CTRL\+DROITE jusqu'à ce que le contrôle atteigne le côté du formulaire.  Notez les positions qu'il occupe à mesure qu'il se déplace à travers le formulaire.  
  
6.  Déplacez le contrôle autour du formulaire avec une combinaison de touches de direction.  Notez les positions que le contrôle occupe et les lignes d'alignement \(SnapLines\) qui les accompagnent.  
  
7.  Appuyez sur MAJ\+une touche de direction pour redimensionner le contrôle <xref:System.Windows.Forms.Button> par des incréments d'un pixel.  
  
8.  Appuyez sur la combinaison CTRL\+MAJ\+une touche de direction pour redimensionner le contrôle <xref:System.Windows.Forms.Button> par incréments de lignes d'alignement \(SnapLines\).  
  
## Lignes d'alignement \(SnapLines\) et panneaux de disposition  
 Les lignes d'alignement \(SnapLines\) sont désactivés dans les panneaux de disposition.  
  
#### Pour désactiver sélectivement les lignes d'alignement \(SnapLines\)  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Double\-cliquez sur l'icône du contrôle <xref:System.Windows.Forms.Button> dans la **Boîte à outils**.  Notez qu'un nouveau contrôle de bouton apparaît dans la première cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  Double\-cliquez sur l'icône du contrôle <xref:System.Windows.Forms.Button> dans la **Boîte à outils** à deux reprises.  Cela laisse une cellule vide dans le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
4.  Faites glisser un contrôle <xref:System.Windows.Forms.Button> de la **Boîte à outils** vers la cellule vide du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Notez qu'aucune ligne d'alignement \(SnapLine\) n'apparaît.  
  
5.  Faites glisser le contrôle <xref:System.Windows.Forms.Button> hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> et déplacez\-le autour du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  Notez que les lignes d'alignement \(SnapLines\) apparaissent de nouveau.  
  
## Désactivation des lignes d'alignement \(SnapLines\)  
 Les lignes d'alignement \(SnapLines\) sont activées par défaut.  Vous pouvez désactiver sélectivement les lignes d'alignement \(SnapLines\), ou vous pouvez les désactiver dans l'environnement de design.  
  
#### Pour désactiver sélectivement les lignes d'alignement \(SnapLines\)  
  
-   Appuyez sur la touche ALT tout en déplaçant un contrôle autour du formulaire.  
  
     Notez qu'aucune ligne d'alignement \(SnapLine\) n'apparaît et le contrôle ne s'aligne pas sur toutes les positions d'alignement potentielles.  
  
#### Pour désactiver les lignes d'alignement \(SnapLines\) dans l'environnement de design  
  
1.  Dans le menu **Outils**, ouvrez la boîte de dialogue **Options**.  Ouvrez la boîte de dialogue Concepteur Windows Forms.  Pour plus d'informations, consultez [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/fr-fr/8dd170af-72f0-4212-b04b-034ceee92834).  
  
2.  Sélectionnez le nœud **Général**.  Dans la section **LayoutMode**, remplacez **SnapLines** par **SnapToGrid**.  
  
3.  Cliquez sur OK pour appliquer le paramètre.  
  
4.  Sélectionnez un contrôle sur votre formulaire et déplacez\-le autour des autres contrôles.  Notez que les lignes d'alignement \(SnapLines\) n'apparaissent pas.  
  
## Étapes suivantes  
 Les lignes d'alignement \(SnapLines\) offrent un moyen intuitif pour aligner des contrôles sur votre formulaire.  Voici quelques suggestions pour une exploration plus approfondie :  
  
-   Essayez d'imbriquer un contrôle <xref:System.Windows.Forms.GroupBox> dans un autre contrôle <xref:System.Windows.Forms.GroupBox>.  Placez un contrôle <xref:System.Windows.Forms.Button> dans le contrôle enfant <xref:System.Windows.Forms.GroupBox>, et un autre dans le contrôle parent <xref:System.Windows.Forms.GroupBox>.  Déplacez les contrôles <xref:System.Windows.Forms.Button> autour pour voir comment les lignes d'alignement \(SnapLines\) franchissent les limites des conteneurs.  
  
-   Créez une colonne de contrôles <xref:System.Windows.Forms.TextBox> et une colonne correspondante de contrôles <xref:System.Windows.Forms.Label>.  Affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Control.AutoSize%2A> du contrôle <xref:System.Windows.Forms.Label>.  Utilisez les lignes d'alignement \(SnapLines\) pour déplacer les contrôles <xref:System.Windows.Forms.Label>afin que leur texte affiché soit aligné avec le texte dans les contrôles <xref:System.Windows.Forms.TextBox>.  
  
 Pour plus d'informations sur la conception d'interfaces utilisateur Windows, consultez l'ouvrage *Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers* Redmond, WA: Microsoft Press, 1999  \(USBN : 0\-7356\-0566\-1\).  
  
## Voir aussi  
 <xref:System.Windows.Forms.Design.Behavior.SnapLine>   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)   
 [Procédure pas à pas : disposition des contrôles Windows Forms avec les propriétés Padding, Margins et AutoSize](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)   
 [Disposition des contrôles dans les Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)