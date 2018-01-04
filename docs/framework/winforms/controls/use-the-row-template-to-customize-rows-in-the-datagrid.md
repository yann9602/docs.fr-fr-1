---
title: "Comment : utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms"
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
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4898ed7ddff6ca1800ba9380707ad989cbec1125
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a>Comment : utiliser le modèle de ligne pour personnaliser les lignes du contrôle DataGridView Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle utilise le modèle de ligne comme base pour toutes les lignes qu’il ajoute au contrôle via la liaison de données ou lorsque vous appelez le <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> méthode sans spécifier une ligne existante à utiliser.  
  
 Le modèle de ligne vous donne un plus grand contrôle sur l’apparence et le comportement des lignes que la <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> fournit de la propriété. Le modèle de ligne, vous pouvez définir les <xref:System.Windows.Forms.DataGridViewRow> propriétés, y compris <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.  
  
 Il existe certaines situations où vous devez utiliser le modèle de ligne pour obtenir un effet particulier. Par exemple, les informations de hauteur de ligne ne peut pas être stockées dans un <xref:System.Windows.Forms.DataGridViewCellStyle>, vous devez utiliser un modèle de ligne pour modifier la hauteur par défaut utilisée par toutes les lignes. Le modèle de ligne est également utile lorsque vous créez vos propres classes dérivées de <xref:System.Windows.Forms.DataGridViewRow> et vous souhaitez que votre type personnalisé utilisé lorsque de nouvelles lignes sont ajoutées au contrôle.  
  
> [!NOTE]
>  Le modèle de ligne est utilisé uniquement lorsque des lignes sont ajoutées. Vous ne pouvez pas modifier les lignes existantes en modifiant le modèle de ligne.  
  
### <a name="to-use-the-row-template"></a>Pour utiliser le modèle de ligne  
  
-   Définir des propriétés sur l’objet récupéré à partir de la <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> propriété.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;  
  
-   des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>  
 [Mises en forme et styles de base dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)
