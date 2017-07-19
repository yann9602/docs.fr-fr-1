---
title: "Comment&#160;: activer l&#39;affichage en mosa&#239;que dans un contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur | Microsoft Docs"
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
  - "ListView (contrôle Windows Forms), affichage en mosaïque"
  - "affichage en mosaïque (fonctionnalité)"
  - "mosaïque, Windows Forms, contrôles"
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: activer l&#39;affichage en mosa&#239;que dans un contr&#244;le ListView Windows Forms &#224; l&#39;aide du concepteur
La fonctionnalité d'affichage en mosaïque du contrôle <xref:System.Windows.Forms.ListView> permet de fournir un équilibre visuel entre des informations graphiques et textuelles.  Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont les mêmes que les informations de colonne définies pour le mode Détails.  L'affichage en mosaïque fonctionne en association avec les fonctions de regroupement ou de marques d'insertion dans le contrôle <xref:System.Windows.Forms.ListView>.  
  
 L'affichage en mosaïque utilise une icône de 32 x 32 et plusieurs lignes de texte, comme l'illustre l'image suivante.  
  
 ![Affichage en mosaïque dans un contrôle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Les propriétés et méthodes de l'affichage en mosaïque vous permettent de spécifier les champs de colonne à afficher pour chaque élément, ainsi que de contrôler collectivement la taille et l'apparence de tous les éléments d'une fenêtre d'affichage en mosaïque.  Pour des raisons de clarté, la première ligne de texte d'une mosaïque est toujours le nom de l'élément ; elle ne peut pas être modifiée.  
  
 La procédure suivante requiert un projet d'**application Windows** avec un formulaire qui contient un contrôle <xref:System.Windows.Forms.ListView>.  Pour plus d'informations sur la configuration d'un tel projet, consultez [How to: Create a Windows Application Project](http://msdn.microsoft.com/fr-fr/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles à des Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  L'affichage en mosaïque est uniquement disponible sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] lorsque votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=fullName>.  Sur les systèmes d'exploitation antérieurs, tout code en rapport avec l'affichage en mosaïque est sans effet, et le contrôle <xref:System.Windows.Forms.ListView> s'affiche en mode Grandes icônes.  Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.View%2A?displayProperty=fullName>.  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour définir l'affichage en mosaïque dans le concepteur  
  
1.  Sélectionnez le contrôle <xref:System.Windows.Forms.ListView> sur le formulaire.  
  
2.  Dans la fenêtre **Propriétés**, sélectionnez la propriété <xref:System.Windows.Forms.ListView.View%2A>, puis choisissez **Mosaïque**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.ListView.TileSize%2A>   
 [Windows XP Features and Windows Forms Controls](http://msdn.microsoft.com/fr-fr/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)   
 [Vue d'ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)