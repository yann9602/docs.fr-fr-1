---
title: "Comment&#160;: modifier des colonnes et des lignes dans un contr&#244;le TableLayoutPanel | Microsoft Docs"
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
  - "net.ComponentModel.StyleCollectionEditor"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "colonnes (Windows Forms), modifier"
  - "lignes (Windows Forms), modifier"
  - "TableLayoutPanel (contrôle Windows Forms), modifier"
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: modifier des colonnes et des lignes dans un contr&#244;le TableLayoutPanel
Vous pouvez utiliser l'éditeur de collections du contrôle <xref:System.Windows.Forms.TableLayoutPanel>, appelé la boîte de dialogue **Styles de ligne et de colonne**, pour modifier les lignes et colonnes de vos contrôles.  
  
> [!NOTE]
>  Si vous souhaitez qu'un contrôle couvre plusieurs lignes ou colonnes, définissez les propriétés `RowSpan` et `ColumnSpan` sur le contrôle.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Si vous souhaitez aligner un contrôle dans une cellule, ou si vous souhaitez étirer un contrôle dans une cellule, utilisez la propriété <xref:System.Windows.Forms.Control.Anchor%2A> du contrôle.  Pour plus d'informations, consultez [Procédure pas à pas : organisation des contrôles dans les Windows Forms à l'aide d'un TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.  Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils**.  Pour plus d'informations, consultez [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/fr-fr/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Pour modifier des lignes et des colonnes  
  
1.  Faites glisser un contrôle <xref:System.Windows.Forms.TableLayoutPanel> de la **Boîte à outils** vers votre formulaire.  
  
2.  Cliquez sur le glyphe \(![Glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) de la balise active du contrôle  <xref:System.Windows.Forms.TableLayoutPanel>, puis sélectionnez **Modifier les lignes et les colonnes** pour ouvrir la boîte de dialogue **Styles de ligne et de colonne**.  Vous pouvez également cliquer avec le bouton droit sur le contrôle <xref:System.Windows.Forms.TableLayoutPanel> et sélectionner **Modifier les lignes et les colonnes** dans le menu contextuel.  
  
3.  Pour ajouter ou supprimer des colonnes, sélectionnez **Colonnes** dans la zone de liste déroulante **Type de membre**.  
  
4.  Pour ajouter ou supprimer des lignes, sélectionnez **Lignes** dans la zone de liste déroulante **Type de membre**.  
  
5.  Cliquez sur le bouton **Ajouter** pour ajouter une ligne ou colonne à la fin de la liste **Membre**.  
  
6.  Cliquez sur le bouton **Insérer** pour ajouter une ligne ou une colonne devant l'élément sélectionné actuellement dans la liste.  
  
7.  Si vous ajoutez une ligne ou colonne, sélectionnez le **Type de taille** pour la nouvelle ligne ou colonne.  Pour plus d'informations, consultez <xref:System.Windows.Forms.SizeType>.  
  
8.  Pour supprimer une ligne ou une colonne, cliquez sur le bouton **Supprimer** pour supprimer l'élément sélectionné actuellement dans la liste **Membre**.  
  
## Voir aussi  
 <xref:System.Windows.Forms.SizeType>   
 [TableLayoutPanel, contrôle](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)