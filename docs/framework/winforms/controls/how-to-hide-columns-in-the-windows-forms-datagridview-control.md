---
title: "Comment : masquer des colonnes du contrôle DataGridView Windows Forms"
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
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4c0dd32e6d0633a18d18905992d5defbe838923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ef746-102">Comment : masquer des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef746-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ef746-103">Parfois, vous souhaiterez afficher uniquement quelques-unes des colonnes qui sont disponibles dans un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ef746-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="ef746-104">Par exemple, vous souhaiterez peut-être afficher une colonne répertoriant les salaires des employés aux utilisateurs disposant d'informations d'identification d'administration et la masquer aux yeux des autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="ef746-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="ef746-105">Ou encore lier le contrôle à une source de données qui contient de nombreuses colonnes, dont vous souhaitez afficher uniquement certaines d'entre elles.</span><span class="sxs-lookup"><span data-stu-id="ef746-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="ef746-106">Dans ce cas, vous supprimerez en général les colonnes que vous ne souhaitez pas afficher, plutôt que de les masquer.</span><span class="sxs-lookup"><span data-stu-id="ef746-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="ef746-107">Dans le contrôle <xref:System.Windows.Forms.DataGridView>, la valeur de propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> d'une colonne détermine si cette colonne est affichée.</span><span class="sxs-lookup"><span data-stu-id="ef746-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="ef746-108">Cette tâche est prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef746-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="ef746-109">Consultez également [Comment : masquer des colonnes dans les Windows Forms DataGridView contrôle à l’aide du concepteur](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ef746-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="ef746-110">Pour masquer une colonne par programmation</span><span class="sxs-lookup"><span data-stu-id="ef746-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="ef746-111">Affectez à la propriété <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="ef746-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="ef746-112">Pour masquer une colonne `CustomerID` qui est générée automatiquement lors de la liaison de données, placez l'exemple de code suivant dans un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.DataBindingComplete>.</span><span class="sxs-lookup"><span data-stu-id="ef746-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef746-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="ef746-113">Compiling the Code</span></span>  
 <span data-ttu-id="ef746-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="ef746-114">This example requires:</span></span>  
  
-   <span data-ttu-id="ef746-115">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` qui contient une colonne nommée `CustomerID` ;</span><span class="sxs-lookup"><span data-stu-id="ef746-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="ef746-116">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef746-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef746-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef746-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ef746-118">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef746-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="ef746-119">Guide pratique pour supprimer les colonnes générées automatiquement d'un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef746-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="ef746-120">Guide pratique pour modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef746-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
