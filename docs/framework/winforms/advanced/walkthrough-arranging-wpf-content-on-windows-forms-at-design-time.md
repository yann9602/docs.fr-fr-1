---
title: "Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF user control [Windows Forms], hosting in a layout panel
- WPF content [Windows Forms], arranging at design time
- Windows Forms, arranging WPF content at design time
- WPF content [Windows Forms], hosting in Windows Forms
- Windows Forms, anchoring and docking WPF content
- interoperability [WPF]
ms.assetid: 5efb1c53-1484-43d6-aa8a-f4861b99bb8a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: afde62d07c009de4612aa44ebbd81b5a71ef36e5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-arranging-wpf-content-on-windows-forms-at-design-time"></a>Procédure pas à pas : réorganisation du contenu WPF sur les Windows Forms au moment du design
Cette procédure pas à pas montre comment utiliser les fonctionnalités de disposition Windows Forms, telles que l’ancrage et les lignes d’alignement, pour disposer les contrôles WPF (Windows Presentation Foundation).  
  
 Lors de cette procédure pas à pas, vous allez exécuter les tâches suivantes :  
  
-   créer le projet ;  
  
-   créer le contrôle WPF ;  
  
-   héberger des contrôles WPF dans un panneau de disposition ;  
  
-   utiliser des lignes d'alignement pour aligner des contrôles WPF ;  
  
-   ancrer des contrôles WPF.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous devez disposer des composants suivants :  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
## <a name="creating-the-project"></a>Création du projet  
 La première étape consiste à créer le projet Windows Forms.  
  
> [!NOTE]
>  Lors de l'hébergement de contenu WPF, seuls les projets Visual Basic et C# sont pris en charge.  
  
#### <a name="to-create-the-project"></a>Pour créer le projet  
  
-   Créer un nouveau projet d’Application Windows Forms dans Visual Basic ou Visual c# nommé `ArrangeElementHost`.  
  
## <a name="creating-the-wpf-control"></a>Création du contrôle WPF  
 Après avoir ajouté un contrôle WPF au projet, vous pouvez le disposer sur le formulaire.  
  
#### <a name="to-create-wpf-controls"></a>Pour créer des contrôles WPF  
  
1.  Ajoutez un nouveau <xref:System.Windows.Controls.UserControl> WPF au projet. Utilisez le nom par défaut pour le type de contrôle, `UserControl1.xaml`. Pour plus d’informations, consultez [procédure pas à pas : création WPF de contenu dans les Windows Forms au moment du Design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).  
  
2.  En mode Design, assurez-vous que `UserControl1` est sélectionné. Pour plus d’informations, consultez [Comment : sélectionner et déplacer des éléments sur l’aire de conception](http://msdn.microsoft.com/library/54cb70b6-b35b-46e4-a0cc-65189399c474).  
  
3.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.FrameworkElement.Width%2A> et <xref:System.Windows.FrameworkElement.Height%2A> propriétés `200`.  
  
4.  Affectez à la propriété <xref:System.Windows.Controls.Control.Background%2A> la valeur `Blue`.  
  
5.  Générez le projet.  
  
## <a name="hosting-wpf-controls-in-a-layout-panel"></a>Hébergement de contrôles WPF dans un panneau de disposition  
 Vous pouvez utiliser des contrôles WPF dans des panneaux de disposition de la même façon que vous utilisez d'autres contrôles Windows Forms.  
  
#### <a name="to-host-wpf-controls-in-a-layout-panel"></a>Pour héberger des contrôles WPF dans un panneau de disposition  
  
1.  Ouvrez `Form1` dans le Concepteur Windows Forms.  
  
2.  Dans le **boîte à outils**, faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle vers le formulaire.  
  
3.  Sur le <xref:System.Windows.Forms.TableLayoutPanel> panneau des balises actives du contrôle, sélectionnez **supprimer la dernière ligne**.  
  
4.  Augmentez la largeur et la hauteur du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
5.  Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une instance de `UserControl1` dans la première cellule de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost1`.  
  
6.  Dans le **boîte à outils**, double-cliquez sur `UserControl1` pour créer une autre instance dans la deuxième cellule de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
7.  Dans le **structure du Document** fenêtre, sélectionnez `tableLayoutPanel1`. Pour plus d’informations, consultez [fenêtre Structure du Document](http://msdn.microsoft.com/library/9054f2bc-f6f8-4242-9fe0-be71089b12f8).  
  
8.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Forms.Control.Padding%2A> propriété `10, 10, 10, 10`.  
  
     Les deux contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés pour s'adapter à la nouvelle disposition.  
  
## <a name="using-snaplines-to-align-wpf-controls"></a>Utilisation de lignes d'alignement pour aligner des contrôles WPF  
 Les lignes d'alignement permettent d'aligner facilement les contrôles sur un formulaire. Vous pouvez aussi utiliser des lignes d'alignement pour aligner vos contrôles WPF. Pour plus d’informations, consultez [procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
#### <a name="to-use-snaplines-to-align-wpf-controls"></a>Pour utiliser des lignes d'alignement pour aligner des contrôles WPF  
  
1.  À partir de la **boîte à outils**, faites glisser une instance de `UserControl1` sur le formulaire et placez-la dans l’espace sous le <xref:System.Windows.Forms.TableLayoutPanel> contrôle.  
  
     L'instance de `UserControl1` est hébergée dans un nouveau contrôle <xref:System.Windows.Forms.Integration.ElementHost> nommé `elementHost3`.  
  
2.  À l'aide des lignes d'alignement, alignez le bord gauche de `elementHost3` avec le bord gauche du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
3.  À l'aide des lignes d'alignement, affectez à `elementHost3` la même largeur que celle du contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
4.  Déplacez `elementHost3` vers le contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce qu'une ligne d'alignement centrale apparaisse entre les contrôles.  
  
5.  Dans le **propriétés** fenêtre, définissez la valeur de la propriété de marge à `20, 20, 20, 20`.  
  
6.  Déplacez le `elementHost3` hors du contrôle <xref:System.Windows.Forms.TableLayoutPanel> jusqu'à ce que la ligne d'alignement centrale réapparaisse. La ligne d'alignement centrale indique maintenant une marge de 20.  
  
7.  Déplacez `elementHost3` vers la droite jusqu'à ce que son bord gauche soit aligné avec le bord gauche de `elementHost1`.  
  
8.  Modifiez la largeur de `elementHost3` jusqu'à ce que son bord droit soit aligné avec le bord droit de `elementHost2`.  
  
## <a name="anchoring-and-docking-wpf-controls"></a>Ancrage de contrôles WPF  
 Un contrôle WPF hébergé sur un formulaire a le même comportement d'ancrage que d'autres contrôles Windows Forms.  
  
#### <a name="to-anchor-and-dock-wpf-controls"></a>Pour ancrer des contrôles WPF  
  
1.  Sélectionnez `elementHost1`.  
  
2.  Dans le **propriétés** , configurez la <xref:System.Windows.Forms.Control.Anchor%2A> propriété **haut, bas, gauche, droite**.  
  
3.  Agrandissez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
     Le contrôle `elementHost1` est redimensionné pour remplir la cellule.  
  
4.  Sélectionnez `elementHost2`.  
  
5.  Dans le **propriétés** fenêtre, définissez la valeur de la <xref:System.Windows.Forms.Control.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Le contrôle `elementHost2` est redimensionné pour remplir la cellule.  
  
6.  Sélectionnez le contrôle <xref:System.Windows.Forms.TableLayoutPanel>.  
  
7.  Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Top>.  
  
8.  Sélectionnez `elementHost3`.  
  
9. Affectez à sa propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.  
  
     Le contrôle `elementHost3` est redimensionné pour remplir l'espace restant sur le formulaire.  
  
10. Redimensionnez le formulaire.  
  
     Les trois contrôles <xref:System.Windows.Forms.Integration.ElementHost> sont redimensionnés correctement.  
  
     Pour plus d’informations, consultez [Comment : ancrage et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Guide pratique pour ancrer et arrimer des contrôles enfants dans un contrôle TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Guide pratique pour aligner un contrôle sur les bords des formulaires au moment du design](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l’aide des lignes d’alignement](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Migration et interopérabilité](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [Utilisation de contrôles WPF](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [Concepteur WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
