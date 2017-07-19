---
title: "Proc&#233;dure pas &#224; pas&#160;: r&#233;organisation du contenu WPF sur les Windows Forms au moment du design | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "interopérabilité (WPF)"
  - "Windows Forms, ancrer un contenu WPF"
  - "Windows Forms, organiser un contenu WPF au moment du design"
  - "contenu WPF (Windows Forms), organiser au moment du design"
  - "contenu WPF, héberger dans les Windows Forms"
  - "contrôles utilisateur WPF (Windows Forms), héberger dans un panneau de disposition"
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Proc&#233;dure pas &#224; pas&#160;: r&#233;organisation du contenu WPF sur les Windows Forms au moment du design
Cette procédure pas à pas montre comment utiliser les fonctionnalités de disposition Windows Forms, telles que l'ancrage et les lignes d'alignement, pour disposer les contrôles WPF \(Windows Presentation Foundation\).  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer le contrôle WPF ;  
  
-   héberger des contrôles WPF dans un panneau de disposition ;  
  
-   utiliser des lignes d'alignement pour aligner des contrôles WPF ;  
  
-   ancrer des contrôles WPF.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Composants requis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C\# sont pris en charge.  
  
#### Pour créer le projet  
  
-   Créez un projet d'application Windows Forms dans Visual Basic ou Visual C\# nommé `ArrangeElementHost`.  
  
## Création du contrôle WPF  
 Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.  
  
#### Pour créer des contrôles WPF  
  
1.  Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet.  Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`.  Pour plus d'informations, consultez [Procédure pas à pas : création de contenu WPF sur les Windows Forms au moment du design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  En mode Design, assurez\-vous que `UserControl1` est sélectionné.  Pour plus d'informations, consultez [Comment : sélectionner et déplacer des éléments sur l'aire de conception](http://msdn.microsoft.com/fr-fr/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans la fenêtre **Propriétés**, affectez la valeur `200` aux propriétés <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A>.  
  
4.  Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Blue`.  
  
5.  Générez le projet.  
  
## Hébergement de contrôles WPF dans un panneau de disposition  
 Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.  
  
#### Pour héberger des contrôles WPF dans un panneau de disposition  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans la **Boîte à outils**, faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> vers le formulaire.  
  
3.  Dans le panneau des Smart Tags du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, sélectionnez **Supprimer la dernière ligne**.  
  
4.  Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
5.  Dans la **Boîte à outils**, double\-cliquez sur `UserControl1` pour créer une instance de `UserControl1` dans la première cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
6.  Dans la **Boîte à outils**, double\-cliquez sur `UserControl1` pour créer une autre instance dans la seconde cellule du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
7.  Dans la fenêtre **Structure du document**, sélectionnez `tableLayoutPanel1`.  Pour plus d'informations, consultez [Document Outline Window](http://msdn.microsoft.com/fr-fr/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.Control.Padding%2A> la valeur `10, 10, 10, 10`.  
  
     Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.  
  
## Utilisation de lignes d'alignement pour aligner des contrôles WPF  
 Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire.  Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### Pour utiliser des lignes d'alignement pour aligner des contrôles WPF  
  
1.  Dans la **Boîte à outils**, faites glisser une instance de `UserControl1` sur le formulaire et placez\-la dans l'espace sous le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.  
  
2.  À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
4.  Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.  
  
5.  Dans la fenêtre **Propriétés**, affectez la valeur `20, 20, 20, 20` à la propriété Marge.  
  
6.  Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse.  La ligne d'alignement centrale indique maintenant une marge de 20.  
  
7.  Déplacez `elementHost3` vers la droite jusqu'à ce que son bord gauche soit aligné avec le bord gauche de `elementHost1`.  
  
8.  Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.  
  
## Ancrage de contrôles WPF  
 Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.  
  
#### Pour ancrer des contrôles WPF  
  
1.  Sélectionnez `elementHost1`.  
  
2.  Dans la fenêtre **Propriétés**, affectez la valeur **Haut, Bas, Gauche, Droite** à la propriété <xref:System.Windows.Forms.Control.Anchor%2A>.  
  
3.  Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
     Le contrôle `elementHost1` est redimensionné pour remplir la cellule.  
  
4.  Sélectionnez `elementHost2`.  
  
5.  Dans la fenêtre **Propriétés**, affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
     Le contrôle `elementHost2` est redimensionné pour remplir la cellule.  
  
6.  Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
7.  Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
8.  Sélectionnez `elementHost3`.  
  
9. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
     Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.  
  
10. Redimensionnez le formulaire.  
  
     Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.  
  
     Pour plus d'informations, consultez [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
  
## Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>   
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>   
 [Comment : ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)   
 [Comment : aligner un contrôle sur les bords des formulaires au moment du design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)   
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide des lignes d'alignement \(SnapLines\)](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)   
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)   
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)   
 [Concepteur WPF](http://msdn.microsoft.com/fr-fr/c6c65214-8411-4e16-b254-163ed4099c26)