---
title: "Comment&#160;: regrouper des &#233;l&#233;ments dans un contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "regroupement"
  - "groupes, dans des contrôles Windows Forms"
  - "ListView (contrôle Windows Forms), regrouper des éléments"
ms.assetid: 8b615000-69d9-4c64-acaf-b54fa09b69e3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: regrouper des &#233;l&#233;ments dans un contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur
La fonctionnalité de regroupement du contrôle <xref:System.Windows.Forms.ListView> vous permet d'afficher des ensembles connexes d'éléments sous forme de groupes.  Ces groupes sont séparés à l'écran par des en\-têtes de groupes horizontaux qui contiennent les titres des groupes.  Vous pouvez utiliser des groupes <xref:System.Windows.Forms.ListView> pour faciliter la navigation dans les longues listes en regroupant les éléments par ordre alphabétique, par date ou par tout autre regroupement logique.  L'image suivante présente des éléments regroupés.  
  
 ![Groupes ListView](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ListView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
 Pour activer le regroupement, vous devez tout d'abord créer un ou plusieurs objets <xref:System.Windows.Forms.ListViewGroup>, dans le concepteur ou par programme.  Une fois qu'un groupe a été défini, vous pouvez lui assigner des éléments.  
  
> [!NOTE]
>  Les groupes <xref:System.Windows.Forms.ListView> sont disponibles uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] lorsque votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>.  Sur les systèmes d'exploitation antérieurs, tout code concernant les groupes est sans effet et les groupes n'apparaissent pas.  Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=fullName>.  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour ajouter ou supprimer des groupes dans le concepteur  
  
1.  Dans la fenêtre **Propriétés**, cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.ListView.Groups%2A>.  
  
     L'**éditeur de collections ListViewGroup** s'affiche.  
  
2.  Pour ajouter un groupe, cliquez sur le bouton **Ajouter**.  Vous pouvez ensuite définir des propriétés du nouvel groupe, comme les propriétés <xref:System.Windows.Forms.ListViewGroup.Header%2A> et <xref:System.Windows.Forms.ListViewGroup.HeaderAlignment%2A>.  Pour supprimer un groupe, sélectionnez\-le, puis cliquez sur le bouton **Supprimer**.  
  
### Pour assigner des éléments aux groupes dans le concepteur  
  
1.  Dans la fenêtre **Propriétés**, cliquez sur le **bouton de sélection** \(![Capture d'écran VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) situé en regard de la propriété <xref:System.Windows.Forms.ListView.Items%2A>.  
  
     L'**éditeur de collections ListViewItem** s'affiche.  
  
2.  Pour ajouter un nouvel élément, cliquez sur le bouton **Ajouter**.  Vous pouvez ensuite définir des propriétés du nouvel élément, par exemple les propriétés <xref:System.Windows.Forms.ListViewItem.Text%2A> et <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>.  
  
3.  Sélectionnez la propriété <xref:System.Windows.Forms.ListViewItem.Group%2A> et choisissez un groupe dans la liste déroulante.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView>   
 <xref:System.Windows.Forms.ListView.Groups%2A>   
 <xref:System.Windows.Forms.ListViewGroup>   
 [ListView, contrôle](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/fr-fr/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [Comment : ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)