---
title: "Comment : définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a31e8eb02949c0f6db487e3cd1a6976f2ed37222
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="37cf2-102">Comment : définir des styles de lignes en alternance pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37cf2-102">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="37cf2-103">Les données sous forme de tableau sont souvent présentées aux utilisateurs dans un format de type livre comptable où les lignes en alternance ont des couleurs d'arrière-plan différentes.</span><span class="sxs-lookup"><span data-stu-id="37cf2-103">Tabular data is often presented to users in a ledger-like format where alternating rows have different background colors.</span></span> <span data-ttu-id="37cf2-104">Avec ce format, il est facile pour les utilisateurs de déterminer quelle cellule appartient à quelle ligne, en particulier dans les tableaux larges qui ont beaucoup de colonnes.</span><span class="sxs-lookup"><span data-stu-id="37cf2-104">This format makes it easier for users to tell which cells are in each row, especially with wide tables that have many columns.</span></span>  
  
 <span data-ttu-id="37cf2-105">Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez spécifier des informations de style complètes pour les lignes en alternance.</span><span class="sxs-lookup"><span data-stu-id="37cf2-105">With the <xref:System.Windows.Forms.DataGridView> control, you can specify complete style information for alternating rows.</span></span> <span data-ttu-id="37cf2-106">Cela vous permet d'utiliser des caractéristiques de style comme la couleur de premier plan et la police, en plus de la couleur d'arrière-plan, pour différencier les lignes en alternance.</span><span class="sxs-lookup"><span data-stu-id="37cf2-106">This enables you use style characteristics like foreground color and font, in addition to background color, to differentiate alternating rows.</span></span>  
  
 <span data-ttu-id="37cf2-107">Cette tâche est prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37cf2-107">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="37cf2-108">Consultez également [Comment : définir des Styles de ligne en alternance pour les Windows Forms DataGridView contrôle à l’aide du concepteur](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="37cf2-108">Also see [How to: Set Alternating Row Styles for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).</span></span>  
  
### <a name="to-set-alternating-row-styles-programmatically"></a><span data-ttu-id="37cf2-109">Pour définir des styles de ligne en alternance par programmation</span><span class="sxs-lookup"><span data-stu-id="37cf2-109">To set alternating row styles programmatically</span></span>  
  
-   <span data-ttu-id="37cf2-110">Définissez les propriétés des objets <xref:System.Windows.Forms.DataGridViewCellStyle> retournés par les propriétés <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="37cf2-110">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> objects returned by the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties of the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  <span data-ttu-id="37cf2-111">Les styles spécifiés à l'aide des propriétés <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> et <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> remplacent ceux spécifiés au niveau de la colonne et du <xref:System.Windows.Forms.DataGridView>, mais sont remplacés par ceux définis au niveau de la ligne et de la cellule.</span><span class="sxs-lookup"><span data-stu-id="37cf2-111">The styles specified using the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> and <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> properties override the styles specified on the column and <xref:System.Windows.Forms.DataGridView> level, but are overridden by the styles set on the individual row and cell level.</span></span> <span data-ttu-id="37cf2-112">Pour plus d’informations, consultez [Styles de cellules dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="37cf2-112">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37cf2-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="37cf2-113">Compiling the Code</span></span>  
 <span data-ttu-id="37cf2-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="37cf2-114">This example requires:</span></span>  
  
-   <span data-ttu-id="37cf2-115">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="37cf2-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="37cf2-116">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="37cf2-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="37cf2-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="37cf2-117">Robust Programming</span></span>  
 <span data-ttu-id="37cf2-118">Pour bénéficier d'une extensibilité maximale, vous devez partager des objets <xref:System.Windows.Forms.DataGridViewCellStyle> sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles, plutôt que définir séparément les propriétés de style pour chaque élément séparément.</span><span class="sxs-lookup"><span data-stu-id="37cf2-118">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="37cf2-119">Pour plus d’informations, consultez [meilleures pratiques pour la mise à l’échelle du contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="37cf2-119">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37cf2-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37cf2-120">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [<span data-ttu-id="37cf2-121">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37cf2-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="37cf2-122">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37cf2-122">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="37cf2-123">Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37cf2-123">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="37cf2-124">Guide pratique pour définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="37cf2-124">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
