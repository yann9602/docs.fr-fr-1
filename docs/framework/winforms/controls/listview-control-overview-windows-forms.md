---
title: "Vue d&#39;ensemble du contr&#244;le ListView (Windows Forms) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ListView"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Liste (vues)"
  - "listes"
  - "ListView (contrôle Windows Forms), à propos du contrôle ListView"
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Vue d&#39;ensemble du contr&#244;le ListView (Windows Forms)
Le contrôle <xref:System.Windows.Forms.ListView> Windows Forms affiche une liste d'éléments avec des icônes.  Vous pouvez l'utiliser pour créer une interface semblable au volet droit de l'Explorateur Windows.  Ce contrôle possède quatre modes d'affichage : LargeIcon, SmallIcon, List et Details.  
  
## Ce que vous pouvez faire avec le contrôle ListView  
  
> [!NOTE]
>  Un mode d'affichage supplémentaire, Mosaïque, est uniquement disponible sur Windows XP et le système d'exploitation Windows Server 2003.  Pour plus d'informations, consultez [Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-enable-tile-view-in-a-windows-forms-listview-control.md).  
  
 Le mode LargeIcon affiche de grandes icônes en regard du texte de l'élément ; les éléments sont disposés sur plusieurs colonnes si la taille du contrôle le permet.  Le mode SmallIcon est identique au précédent, mais les icônes affichées sont plus petites.  Le mode List affiche des petites icônes, mais toujours sur une seule colonne.  Le mode Détails affiche les éléments dans plusieurs colonnes.  Pour plus d'informations, consultez [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  Le mode d'affichage est déterminé par la propriété <xref:System.Windows.Forms.ListView.View%2A>.  Tous les modes peuvent afficher des images issues de listes d'images.  Pour plus d'informations, consultez [Comment : afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md).  
  
 Le tableau suivant répertorie quelques\-uns des membres <xref:System.Windows.Forms.ListView> et les affichages dans lesquels ils sont valides.  
  
|Membre ListView|Vue|  
|---------------------|---------|  
|Propriété <xref:System.Windows.Forms.ListView.Alignment%2A>|<xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Propriété <xref:System.Windows.Forms.ListView.AutoArrange%2A>|<xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Méthode <xref:System.Windows.Forms.ListView.AutoResizeColumn%2A>|<xref:System.Windows.Forms.View>|  
|Propriété <xref:System.Windows.Forms.ListView.Columns%2A>|<xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Événement <xref:System.Windows.Forms.ListView.DrawSubItem>|<xref:System.Windows.Forms.View>|  
|Méthode <xref:System.Windows.Forms.ListView.FindItemWithText%2A>|<xref:System.Windows.Forms.View>, <xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Méthode <xref:System.Windows.Forms.ListView.FindNearestItem%2A>|<xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Méthode <xref:System.Windows.Forms.ListView.GetItemAt%2A>|<xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
|Propriété <xref:System.Windows.Forms.ListView.Groups%2A>|Tous les affichages sauf <xref:System.Windows.Forms.View>|  
|Propriété <xref:System.Windows.Forms.ListView.HeaderStyle%2A>|<xref:System.Windows.Forms.View>.|  
|Propriété <xref:System.Windows.Forms.ListView.InsertionMark%2A>|<xref:System.Windows.Forms.View>, <xref:System.Windows.Forms.View> ou <xref:System.Windows.Forms.View>|  
  
 La principale propriété du contrôle <xref:System.Windows.Forms.ListView> est <xref:System.Windows.Forms.ListView.Items%2A>, qui contient les éléments affichés par le contrôle.  La propriété <xref:System.Windows.Forms.ListView.SelectedItems%2A> contient une collection des éléments actuellement sélectionnés dans le contrôle.  Si la propriété <xref:System.Windows.Forms.ListView.MultiSelect%2A> a la valeur `true`, l'utilisateur peut sélectionner plusieurs éléments, par exemple pour effectuer une opération glisser\-déplacer de plusieurs éléments simultanément vers un autre contrôle.  Le contrôle <xref:System.Windows.Forms.ListView> peut afficher des cases à cocher à côté des éléments si la propriété <xref:System.Windows.Forms.ListView.CheckBoxes%2A> a la valeur `true`.  
  
 La propriété <xref:System.Windows.Forms.ListView.Activation%2A> détermine quel type d'action l'utilisateur doit choisir pour activer un élément de la liste. Les options sont <xref:System.Windows.Forms.ItemActivation>, <xref:System.Windows.Forms.ItemActivation> et <xref:System.Windows.Forms.ItemActivation>.  L'activation <xref:System.Windows.Forms.ItemActivation> requiert un simple clic pour activer l'élément.  L'activation <xref:System.Windows.Forms.ItemActivation> requiert que l'utilisateur double\-clique pour activer un élément ; un simple clic modifie la couleur du texte de l'élément.  L'activation <xref:System.Windows.Forms.ItemActivation> requiert que l'utilisateur double\-clique pour activer un élément, mais l'élément ne change pas d'apparence.  
  
 Le contrôle <xref:System.Windows.Forms.ListView> prend également en charge les styles visuels et les autres fonctionnalités disponibles sur la plateforme Windows XP \(regroupement, affichage en mosaïque et marques d'insertion\).  Pour plus d'informations, consultez [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/fr-fr/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0).  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)   
 [Comment : ajouter des colonnes au contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)   
 [Comment : afficher des icônes pour le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)   
 [Comment : afficher des sous\-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)   
 [Comment : sélectionner un élément dans le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-an-item-in-the-windows-forms-listview-control.md)   
 [Comment : grouper des éléments dans un contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)   
 [Comment : afficher une marque d'insertion dans un contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)   
 [Comment : ajouter des fonctions de recherche à un contrôle ListView](../../../../docs/framework/winforms/controls/how-to-add-search-capabilities-to-a-listview-control.md)   
 [Comment : ajouter des informations personnalisées à un contrôle TreeView ou ListView \(Windows Forms\)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)   
 [Comment : créer une interface utilisateur à plusieurs volets à l'aide des Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-multipane-user-interface-with-windows-forms.md)