---
title: "Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tile view feature
- ListView control [Windows Forms], tile view
- tiling [Windows Forms], Windows Forms, controls
ms.assetid: 12f0816a-52b8-41ee-a6d9-ded3a8a5817a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cadf31d45f8650336c6ac6257a84655a978a9035
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control-using-the-designer"></a>Comment : activer l'affichage en mosaïque dans un contrôle ListView Windows Forms à l'aide du concepteur
La fonctionnalité d’affichage en mosaïque de le <xref:System.Windows.Forms.ListView> contrôle vous permet de fournir un équilibre visuel entre les informations graphiques et textuelles. Les informations textuelles affichées pour un élément dans l'affichage en mosaïque sont identiques aux informations de colonne définies pour le mode Détails. Affichage en mosaïque fonctionne en association avec le regroupement ou d’insertion marque des fonctionnalités dans le <xref:System.Windows.Forms.ListView> contrôle.  
  
 L’affichage en mosaïque utilise une icône 32 x 32 et plusieurs lignes de texte, comme illustré dans l’image suivante.  
  
 ![Affichage en mosaïque dans un contrôle ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")  
  
 Affichage en mosaïque propriétés et méthodes vous permettent de spécifier les champs de colonne à afficher pour chaque élément et contrôler collectivement la taille et l’apparence de tous les éléments dans une fenêtre d’affichage en mosaïque. Pour plus de clarté, la première ligne de texte dans une mosaïque est toujours le nom de l’élément ; Il ne peut pas être modifié.  
  
 La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ListView> contrôle. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  L'affichage en mosaïque est disponible uniquement sur [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] quand votre application appelle la méthode <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Sur les systèmes d'exploitation antérieurs, tout code lié à l'affichage en mosaïque n'a aucun effet et le contrôle <xref:System.Windows.Forms.ListView> s'affiche en mode Grandes icônes. Pour plus d'informations, consultez <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-tile-view-in-the-designer"></a>Pour définir l’affichage en mosaïque dans le Concepteur  
  
1.  Sélectionnez le <xref:System.Windows.Forms.ListView> contrôle de votre formulaire.  
  
2.  Dans le **propriétés** fenêtre, sélectionnez le <xref:System.Windows.Forms.ListView.View%2A> propriété et choisissez **vignette**.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [Fonctionnalités de Windows XP et contrôles Windows Forms](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Vue d’ensemble du contrôle ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
