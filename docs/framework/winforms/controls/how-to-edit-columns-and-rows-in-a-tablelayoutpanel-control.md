---
title: "Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Comment : modifier des colonnes et des lignes dans un contrôle TableLayoutPanel
Vous pouvez utiliser l’éditeur de collections de la <xref:System.Windows.Forms.TableLayoutPanel> contrôle, appelée la **Styles de ligne et colonne** boîte de dialogue pour modifier les lignes et colonnes de vos contrôles.  
  
> [!NOTE]
>  Si vous voulez un contrôle couvre plusieurs lignes ou colonnes, définissez la `RowSpan` et `ColumnSpan` propriétés sur le contrôle. Pour plus d'informations, consultez [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Si vous souhaitez aligner un contrôle dans une cellule, ou si vous souhaitez un contrôle à étendre dans une cellule, utilisez du contrôle <xref:System.Windows.Forms.Control.Anchor%2A> propriété. Pour plus d'informations, consultez [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Pour modifier les lignes et colonnes  
  
1.  Faites glisser un <xref:System.Windows.Forms.TableLayoutPanel> contrôle depuis la **boîte à outils** vers votre formulaire.  
  
2.  Cliquez sur le <xref:System.Windows.Forms.TableLayoutPanel> glyphe de balise active du contrôle (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) et sélectionnez **modifier les lignes et colonnes** pour ouvrir le  **Styles de ligne et colonne** boîte de dialogue. Vous pouvez également avec le bouton droit sur le <xref:System.Windows.Forms.TableLayoutPanel> de contrôle et sélectionnez **modifier les lignes et colonnes** dans le menu contextuel.  
  
3.  Pour ajouter ou supprimer des colonnes, sélectionnez **colonnes** à partir de la **type de membre** zone de liste déroulante.  
  
4.  Pour ajouter ou supprimer des lignes, sélectionnez **lignes** à partir de la **type de membre** zone de liste déroulante.  
  
5.  Cliquez sur le **ajouter** pour ajouter une ligne ou une colonne à la fin de la **membre** liste.  
  
6.  Cliquez sur le **insérer** pour ajouter une ligne ou une colonne avant l’élément actuellement sélectionné dans la liste.  
  
7.  Si vous ajoutez une ligne ou colonne, sélectionnez le **Type de taille** pour la nouvelle ligne ou la colonne. Pour plus d'informations, consultez <xref:System.Windows.Forms.SizeType>.  
  
8.  Pour supprimer une ligne ou colonne, cliquez sur le **supprimer** bouton pour supprimer l’élément actuellement sélectionné dans le **membre** liste.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.SizeType>  
 [TableLayoutPanel, contrôle](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
