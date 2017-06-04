---
title: "Comment&#160;: modifier l&#39;apparence du contr&#244;le TabControl Windows Forms | Microsoft Docs"
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
  - "boutons, afficher les onglets sous forme de"
  - "icônes, afficher sur des onglets"
  - "TabControl (contrôle Windows Forms), modifier l'apparence de la page"
  - "onglets, contrôler l'aspect"
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: modifier l&#39;apparence du contr&#244;le TabControl Windows Forms
Vous pouvez modifier l'apparence des onglets dans les Windows Forms à l'aide des propriétés des objets <xref:System.Windows.Forms.TabControl> et <xref:System.Windows.Forms.TabPage> qui constituent les différents onglets du contrôle.  En définissant ces propriétés, vous pouvez afficher des images sur les onglets, obtenir un affichage vertical des onglets à la place de l'affichage horizontal, afficher plusieurs rangées d'onglets et activer ou désactiver les onglets par programme.  
  
### Pour afficher une icône dans le titre d'un onglet  
  
1.  Ajoutez un contrôle <xref:System.Windows.Forms.ImageList> au formulaire.  
  
2.  Ajoutez des images à la liste d'images.  
  
     Pour plus d'informations sur les listes d'images, consultez [ImageList, composant](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) et [Comment : ajouter ou supprimer des images avec le composant ImageList Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.ImageList%2A> de <xref:System.Windows.Forms.TabControl> le contrôle <xref:System.Windows.Forms.ImageList>.  
  
4.  Affectez à la propriété <xref:System.Windows.Forms.TabPage.ImageIndex%2A> de <xref:System.Windows.Forms.TabPage> l'index d'une image appropriée dans la liste.  
  
### Pour créer plusieurs rangées d'onglets  
  
1.  Ajoutez le nombre de pages d'onglets que vous souhaitez.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.Multiline%2A> de <xref:System.Windows.Forms.TabControl> la valeur `true`.  
  
3.  Si les onglets ne sont pas encore affichés en plusieurs rangées, définissez la propriété <xref:System.Windows.Forms.Control.Width%2A> de <xref:System.Windows.Forms.TabControl> de telle sorte que sa valeur soit inférieure à la largeur de tous les onglets.  
  
### Pour disposer les onglets sur le côté du contrôle  
  
-   Affectez à la propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> de <xref:System.Windows.Forms.TabControl> la valeur <xref:System.Windows.Forms.TabAlignment> ou <xref:System.Windows.Forms.TabAlignment>.  
  
### Pour activer ou désactiver par programmation tous les contrôles sur un onglet  
  
1.  Affectez à la propriété <xref:System.Windows.Forms.TabPage.Enabled%2A> de <xref:System.Windows.Forms.TabPage> la valeur `true` ou `false`.  
  
    ```vb  
    TabPage1.Enabled = False  
  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### Pour afficher les onglets sous forme de boutons  
  
-   Affectez à la propriété <xref:System.Windows.Forms.TabControl.Appearance%2A> de <xref:System.Windows.Forms.TabControl> la valeur <xref:System.Windows.Forms.TabAppearance> ou <xref:System.Windows.Forms.TabAppearance>.  
  
## Voir aussi  
 [TabControl, contrôle](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [Vue d'ensemble du contrôle TabControl](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [Comment : ajouter un contrôle à une page d'onglet](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [Comment : désactiver les pages d'onglets](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [Comment : ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)