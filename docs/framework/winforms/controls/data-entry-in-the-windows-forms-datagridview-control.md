---
title: "Saisie de données dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399520738c53e149e7a5539a62a5d4599e26a8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6310f-102">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6310f-103">Le `DataGridView` contrôle fournit plusieurs fonctionnalités qui permettent de modifier de manière dont les utilisateurs ajoutent ou modifient des données dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="6310f-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="6310f-104">Par exemple, entrée de données peut rendre plus efficace en fournissant des valeurs par défaut pour les nouvelles lignes et en avertissant les utilisateurs lorsque des erreurs se produisent.</span><span class="sxs-lookup"><span data-stu-id="6310f-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6310f-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6310f-105">In This Section</span></span>  
 [<span data-ttu-id="6310f-106">Guide pratique pour spécifier le mode édition pour le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6310f-107">Décrit comment modifier la façon dont les utilisateurs commencent à modifier les cellules.</span><span class="sxs-lookup"><span data-stu-id="6310f-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="6310f-108">Guide pratique pour spécifier des valeurs par défaut pour les nouvelles lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="6310f-109">Décrit comment préremplir la ligne pour les nouveaux enregistrements de gagner du temps de saisie de données.</span><span class="sxs-lookup"><span data-stu-id="6310f-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="6310f-110">Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6310f-111">Décrit la ligne pour les nouveaux enregistrements en détail, y compris sur son masquage, sur la personnalisation de son apparence et son rapport avec la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span><span class="sxs-lookup"><span data-stu-id="6310f-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="6310f-112">Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6310f-113">Décrit comment valider l’entrée d’utilisateur pour éviter les erreurs de mise en forme de saisie de données.</span><span class="sxs-lookup"><span data-stu-id="6310f-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="6310f-114">Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="6310f-115">Décrit comment gérer les erreurs de saisie de données qui proviennent de la source de données lorsque l’utilisateur tente de valider une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="6310f-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6310f-116">Référence</span><span class="sxs-lookup"><span data-stu-id="6310f-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="6310f-117">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="6310f-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="6310f-118">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.EditMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="6310f-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="6310f-119">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> événement.</span><span class="sxs-lookup"><span data-stu-id="6310f-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="6310f-120">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.DataError> événement.</span><span class="sxs-lookup"><span data-stu-id="6310f-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="6310f-121">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.CellValidating> événement.</span><span class="sxs-lookup"><span data-stu-id="6310f-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6310f-122">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="6310f-122">Related Sections</span></span>  
 [<span data-ttu-id="6310f-123">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6310f-124">Fournit des rubriques qui décrivent comment remplir le contrôle de données manuellement ou à partir de la source de données externe.</span><span class="sxs-lookup"><span data-stu-id="6310f-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6310f-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6310f-125">See Also</span></span>  
 [<span data-ttu-id="6310f-126">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="6310f-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="6310f-127">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6310f-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
