---
title: "Comment : afficher des onglets alignés sur le côté à l'aide de TabControl"
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
- tab pages [Windows Forms], displaying side-aligned tabs
- tabs [Windows Forms], displaying side-aligned tabs
- TabControl control [Windows Forms], displaying side-aligned tabs
ms.assetid: 110d5abd-3ae3-4ded-95bf-778aaac798a0
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0dcbf2cc1aee1333ad5062f2a467adfd0dbe00c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-side-aligned-tabs-with-tabcontrol"></a>Comment : afficher des onglets alignés sur le côté à l'aide de TabControl
La propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> de <xref:System.Windows.Forms.TabControl> prend en charge l'affichage vertical des onglets (le long du bord gauche ou droit du contrôle), par opposition à l'affichage horizontal (en haut ou en bas du contrôle). Par défaut, cet affichage vertical offre une expérience utilisateur médiocre, car la propriété <xref:System.Windows.Forms.TabPage.Text%2A> de l'objet <xref:System.Windows.Forms.TabPage> ne s'affiche pas dans l'onglet quand les styles visuels sont activés. De plus, il n'existe aucun moyen direct de contrôler la direction du texte dans l'onglet. Vous pouvez utiliser Owner Draw sur <xref:System.Windows.Forms.TabControl> pour améliorer cette expérience.  
  
 La procédure suivante montre comment afficher des onglets alignés à droite, avec le texte de l'onglet affiché de gauche à droite, à l'aide de la fonctionnalité « Owner Draw ».  
  
### <a name="to-display-right-aligned-tabs"></a>Pour afficher des onglets alignés à droite  
  
1.  Ajoutez un <xref:System.Windows.Forms.TabControl> à votre formulaire.  
  
2.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.Alignment%2A> la valeur <xref:System.Windows.Forms.TabAlignment.Right>.  
  
3.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.SizeMode%2A> la valeur <xref:System.Windows.Forms.TabSizeMode.Fixed> pour que tous les onglets aient la même largeur.  
  
4.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.ItemSize%2A> la taille fixe préférée pour les onglets. N'oubliez pas que la propriété <xref:System.Windows.Forms.TabControl.ItemSize%2A> se comporte comme si les onglets étaient en haut, bien qu'ils soient alignés à droite. Ainsi, pour que les onglets soient plus larges vous devez modifier la propriété <xref:System.Drawing.Size.Height%2A>, et pour qu'ils soient plus hauts vous devez modifier la propriété <xref:System.Drawing.Size.Width%2A>.  
  
     Pour un résultat optimal avec l'exemple de code ci-dessous, affectez la valeur 25 à la propriété <xref:System.Drawing.Size.Width%2A> et la valeur 100 à la propriété <xref:System.Drawing.Size.Height%2A>.  
  
5.  Affectez à la propriété <xref:System.Windows.Forms.TabControl.DrawMode%2A> la valeur <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>.  
  
6.  Définissez un gestionnaire pour l'événement <xref:System.Windows.Forms.TabControl.DrawItem> de <xref:System.Windows.Forms.TabControl> qui affiche le texte de gauche à droite.  
  
     [!code-csharp[TabControl.RightAlignedTabs#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/TabControl.RightAlignedTabs/CS/Form1.cs#1)]
     [!code-vb[TabControl.RightAlignedTabs#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/TabControl.RightAlignedTabs/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [TabControl, contrôle](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)
