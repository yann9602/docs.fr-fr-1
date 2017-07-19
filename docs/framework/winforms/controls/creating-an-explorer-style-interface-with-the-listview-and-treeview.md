---
title: "Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une interface de style Explorateur avec les contr&#244;les ListView et TreeView &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "applications de style Explorateur"
  - "applications de style Explorateur, procédures pas à pas"
  - "ListView (contrôle Windows Forms), interface de style Internet Explorer"
  - "ListView (contrôle Windows Forms), explorer-style (interface)"
  - "ListView (contrôle Windows Forms), contrôles TreeView utilisés avec"
  - "TreeView (contrôle Windows Forms), contrôles ListView utilisés avec"
  - "TreeView (contrôle Windows Forms), utiliser pour l'interface de style Internet Explorer"
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Proc&#233;dure pas &#224; pas&#160;: cr&#233;ation d&#39;une interface de style Explorateur avec les contr&#244;les ListView et TreeView &#224; l&#39;aide du concepteur
L'un des avantages de Visual Studio est la capacité de créer des applications Windows Forms de qualité professionnelle en un court laps de temps.  Un scénario courant consiste à créer, avec les contrôles <xref:System.Windows.Forms.ListView> et <xref:System.Windows.Forms.TreeView>, une interface utilisateur qui ressemble à la fonctionnalité Explorateur Windows des systèmes d'exploitation Windows.  L'Explorateur Windows affiche une structure hiérarchique des fichiers et dossiers sur l'ordinateur de l'utilisateur.  
  
> [!NOTE]
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour créer le formulaire qui contient un contrôle TreeView et ListView  
  
1.  Dans le menu **Fichier**, pointez sur **Nouveau**, puis cliquez sur **Projet**.  
  
2.  Dans la boîte de dialogue **Nouveau projet**, effectuez les opérations suivantes :  
  
    1.  Dans les catégories, sélectionnez **Visual Basic** ou **Visual C\#**.  
  
    2.  Dans la liste des modèles, sélectionnez **Windows Forms Application**.  
  
3.  Cliquez sur **OK**.  Un nouveau projet Windows Forms est créé.  
  
4.  Ajoutez un <xref:System.Windows.Forms.SplitContainer> au formulaire, et remplacez sa propriété <xref:System.Windows.Forms.SplitContainer.Dock%2A> par <xref:System.Windows.Forms.DockStyle>.  
  
5.  Ajoutez au formulaire un <xref:System.Windows.Forms.ImageList> nommé `imageList1` et utilisez la fenêtre Propriétés pour ajouter deux images : une image de dossier et une image de document, respectivement.  
  
6.  Ajoutez au formulaire un contrôle <xref:System.Windows.Forms.TreeView> nommé `treeview1`, puis positionnez\-le sur le côté gauche du contrôle <xref:System.Windows.Forms.SplitContainer>.  Dans la fenêtre Propriétés de `treeView1`, définissez les propriétés suivantes :  
  
    1.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
    2.  Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> la valeur `imagelist1.`  
  
7.  Ajoutez au formulaire un contrôle <xref:System.Windows.Forms.ListView> nommé `listView1`, puis positionnez\-le sur le côté droit du contrôle <xref:System.Windows.Forms.SplitContainer>.  Dans la fenêtre Propriétés de `listview1`, définissez les propriétés suivantes :  
  
    1.  Affectez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle>.  
  
    2.  Affectez à la propriété <xref:System.Windows.Forms.ListView.View%2A> la valeur <xref:System.Windows.Forms.View>.  
  
    3.  Ouvrez l'Éditeur de la collection ColumnHeader cliquant sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) dans la propriété  <xref:System.Windows.Forms.ListView.Columns%2A> **.** Ajoutez trois colonnes et attribuez à leur propriété <xref:System.Windows.Forms.ColumnHeader.Text%2A> les valeurs `Name`, `Type` et `Last Modified`, respectivement.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
    4.  Affectez à la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A> la valeur `imageList1.`  
  
8.  Implémentez le code pour remplir le <xref:System.Windows.Forms.TreeView> avec les nœuds et les sous\-nœuds.  Ajoutez ce code à la classe `Form1`.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. Dans la mesure où le code précédent utilise l'espace de noms System.IO, ajoutez l'instruction using ou import appropriée en haut du formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. Appelez la méthode de paramétrage de l'étape précédente dans le constructeur du formulaire ou la méthode de gestion d'événements <xref:System.Windows.Forms.Form.Load>.  Ajoutez ce code au constructeur de formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. Gérez l'événement <xref:System.Windows.Forms.TreeView.NodeMouseClick> pour `treeview1`**,**  et implémentez le code pour remplir `listview1` avec le contenu  d'un nœud lorsque l'utilisateur clique sur un nœud.  Ajoutez ce code à la classe `Form1`.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     Si vous utilisez C\#, assurez\-vous que l'événement <xref:System.Windows.Forms.TreeView.NodeMouseClick> est associé à sa méthode de gestion d'événements.  Ajoutez ce code au constructeur de formulaire.  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## Test de l'application  
 Vous pouvez à présent tester le formulaire afin de vous assurer qu'il se comporte comme prévu.  
  
#### Pour tester le formulaire  
  
-   Appuyez sur F5 pour exécuter l'application.  
  
     Vous verrez un formulaire fractionné qui contient un contrôle <xref:System.Windows.Forms.TreeView> qui affiche un répertoire étiqueté sur le côté gauche, et un contrôle <xref:System.Windows.Forms.ListView> sur le côté droit avec trois colonnes.  Vous pouvez parcourir le <xref:System.Windows.Forms.TreeView> en sélectionnant des nœuds de répertoire ; le contenu du répertoire sélectionné remplit <xref:System.Windows.Forms.ListView>.  
  
## Étapes suivantes  
 Cette application vous donne un exemple de la façon dont vous pouvez utiliser ensemble les contrôles <xref:System.Windows.Forms.TreeView> et <xref:System.Windows.Forms.ListView>.  Pour plus d'informations sur ces contrôles, consultez les rubriques suivantes :  
  
-   [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
-   [Comment : ajouter des fonctions de recherche à un contrôle ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)  
  
-   [Comment : attacher un menu contextuel à un nœud TreeView](../../../../docs/framework/winforms/controls/how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.TreeView>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)