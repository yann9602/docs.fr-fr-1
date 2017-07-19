---
title: "Comment&#160;: d&#233;finir des ic&#244;nes pour le contr&#244;le TreeView Windows Forms | Microsoft Docs"
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
  - "exemples (Windows Forms), TreeView (contrôle)"
  - "icônes, paramètre du contrôle TreeView"
  - "ImageList (composant Windows Forms), ajouter des images"
  - "nœuds d'arbre dans le contrôle TreeView, icônes"
  - "TreeView (contrôle Windows Forms), icônes de nœuds"
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
caps.latest.revision: 18
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Comment&#160;: d&#233;finir des ic&#244;nes pour le contr&#244;le TreeView Windows Forms
Le contrôle <xref:System.Windows.Forms.TreeView> Windows Forms peut afficher des icônes en regard de chaque nœud.  Les icônes sont positionnées à gauche du texte de nœud.  Pour afficher ces icônes, vous devez associer l'arborescence à un contrôle <xref:System.Windows.Forms.ImageList>.  Pour plus d'informations sur les listes d'images, consultez [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Un bogue dans Microsoft .NET Framework version 1.1 empêche l'affichage des images sur les nœuds <xref:System.Windows.Forms.TreeView> lorsque votre application appelle <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>.  Pour résoudre ce problème, appelez <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=fullName> dans votre méthode `Main` immédiatement après avoir appelé <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>.  Cette erreur est corrigée dans [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### Pour afficher des images dans une arborescence  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> du contrôle <xref:System.Windows.Forms.TreeView> le contrôle <xref:System.Windows.Forms.ImageList> existant que vous souhaitez utiliser.  
  
     Ces propriétés peuvent être définies dans le concepteur à l'aide de la fenêtre Propriétés ou dans le code.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  Définissez les propriétés <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> et <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> du nœud.  La propriété <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> détermine l'image affichée pour les états normal et développé du nœud, tandis que la propriété <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> détermine l'image affichée pour son état sélectionné.  
  
     Ces propriétés peuvent être définies dans le code ou dans l'Éditeur TreeNode.  Pour afficher l'Éditeur TreeNode, cliquez sur le bouton de sélection \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) en regard de la propriété <xref:System.Windows.Forms.TreeView.Nodes%2A> dans la fenêtre Propriétés.  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## Voir aussi  
 [Vue d'ensemble du contrôle TreeView](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)   
 [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)   
 [Comment : itérer au sein de tous les nœuds d'un contrôle TreeView Windows Forms](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)   
 [Comment : identifier le nœud de TreeView sur lequel un clic est effectué](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)