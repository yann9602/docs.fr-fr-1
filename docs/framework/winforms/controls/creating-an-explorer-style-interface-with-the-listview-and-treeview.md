---
title: "Procédure pas à pas : création d’une interface de style Explorateur avec les contrôles ListView et TreeView à l’aide du concepteur"
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
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 200c5bbb5a162c1e585fc35f9c8cb3f63eb0368e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Procédure pas à pas : création d’une interface de style Explorateur avec les contrôles ListView et TreeView à l’aide du concepteur
Un des avantages de Visual Studio est la capacité de créer des applications Windows Forms de qualité professionnelle en un court laps de temps. Un scénario commun consiste à créer une interface utilisateur (IU) avec <xref:System.Windows.Forms.ListView> et <xref:System.Windows.Forms.TreeView> les contrôles qui ressemble à la fonctionnalité Explorateur Windows des systèmes d’exploitation Windows. L’Explorateur Windows affiche une structure hiérarchique des fichiers et dossiers sur l’ordinateur d’un utilisateur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Pour créer le formulaire contenant un contrôle ListView et TreeView  
  
1.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :  
  
    1.  Dans les catégories, choisissez **Visual Basic** ou **Visual C#**.  
  
    2.  Dans la liste des modèles, choisissez **Application Windows Forms**.  
  
3.  Cliquez sur **OK**. Un nouveau projet Windows Forms est créé.  
  
4.  Ajouter un <xref:System.Windows.Forms.SplitContainer> au formulaire et définissez ses <xref:System.Windows.Forms.SplitContainer.Dock%2A> propriété <xref:System.Windows.Forms.DockStyle.Fill>.  
  
5.  Ajouter un <xref:System.Windows.Forms.ImageList> nommé `imageList1` au formulaire et utilisez la fenêtre Propriétés pour ajouter deux images : une image de dossier et une image de document, dans cet ordre.  
  
6.  Ajouter un <xref:System.Windows.Forms.TreeView> contrôle nommé `treeview1` au formulaire et placez-le sur le côté gauche de la <xref:System.Windows.Forms.SplitContainer> contrôle. Dans la fenêtre Propriétés pour `treeView1` procédez comme suit :  
  
    1.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> la valeur `imagelist1.`  
  
7.  Ajouter un <xref:System.Windows.Forms.ListView> contrôle nommé `listView1` au formulaire et le placer sur le côté droit de la <xref:System.Windows.Forms.SplitContainer> contrôle. Dans la fenêtre Propriétés pour `listview1` procédez comme suit :  
  
    1.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    2.  Affectez à la propriété <xref:System.Windows.Forms.ListView.View%2A> la valeur <xref:System.Windows.Forms.View.Details>.  
  
    3.  Ouvrez l’éditeur de collections ColumnHeader en cliquant sur le bouton de sélection (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) dans le <xref:System.Windows.Forms.ListView.Columns%2A> propriété**.** Ajoutez trois colonnes et définir leurs <xref:System.Windows.Forms.ColumnHeader.Text%2A> propriété `Name`, `Type`, et `Last Modified`, respectivement. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
    4.  Affectez à la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A> la valeur `imageList1.`  
  
8.  Implémentez le code pour remplir la <xref:System.Windows.Forms.TreeView> avec les nœuds et les sous-nœuds. Ajoutez ce code à la `Form1` classe.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Étant donné que le code précédent utilise l’espace de noms System.IO, ajoutez l’utilisation appropriée, ou importer l’instruction en haut du formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Appelez la méthode d’installation à partir de l’étape précédente dans le constructeur du formulaire ou <xref:System.Windows.Forms.Form.Load> méthode de gestion d’événements. Ajoutez ce code au constructeur de formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Gérer les <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement `treeview1` **,** et implémentez le code pour remplir `listview1` avec le contenu d’un nœud lorsque l’utilisateur clique sur un nœud. Ajoutez ce code à la `Form1` classe.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Si vous utilisez c#, assurez-vous d’avoir le <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement associé à sa méthode de gestion d’événements. Ajoutez ce code au constructeur de formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un formulaire fractionné contenant un <xref:System.Windows.Forms.TreeView> contrôle qui affiche le répertoire du projet sur le côté gauche, et un <xref:System.Windows.Forms.ListView> contrôle sur le côté droit avec trois colonnes. Vous pouvez parcourir le <xref:System.Windows.Forms.TreeView> en sélectionnant des nœuds de répertoire et le <xref:System.Windows.Forms.ListView> est rempli avec le contenu du répertoire sélectionné.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous donne un exemple de la façon dont vous pouvez utiliser <xref:System.Windows.Forms.TreeView> et <xref:System.Windows.Forms.ListView> ensemble les contrôles. Pour plus d’informations sur ces contrôles, consultez les rubriques suivantes :  
  
-   [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Guide pratique pour ajouter des fonctions de recherche à un contrôle ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Guide pratique pour attacher un menu contextuel à un nœud TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.TreeView>  
 [Contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [Guide pratique pour ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)  
 [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Guide pratique pour ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
