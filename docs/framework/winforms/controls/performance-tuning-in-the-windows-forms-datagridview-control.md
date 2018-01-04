---
title: "Réglage des performances dans le contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0171bf4fa056de2dd06c2f7e431ea55a8dab1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e1f1b-102">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e1f1b-103">Lorsque vous travaillez avec grandes quantités de données, le `DataGridView` contrôle peut consommer une grande quantité de mémoire, sauf si vous l’utilisez avec précaution.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="e1f1b-104">Sur les clients avec une mémoire limitée, vous pouvez éviter certains cette surcharge en évitant les fonctionnalités qui ont un coût de mémoire élevée.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="e1f1b-105">Vous pouvez également gérer tout ou partie de la maintenance des données et les tâches de récupération à l’aide du mode virtuel afin de personnaliser l’utilisation de la mémoire pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1f1b-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e1f1b-106">In This Section</span></span>  
 [<span data-ttu-id="e1f1b-107">Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e1f1b-108">Décrit comment utiliser le `DataGridView` contrôle de façon à éviter de trop handicaper les performances et l’utilisation inutile de mémoire lorsque vous travaillez avec grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="e1f1b-109">Mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e1f1b-110">Décrit comment utiliser le mode virtuel pour compléter ou remplacer le mécanisme de liaison de données standard.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="e1f1b-111">Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="e1f1b-112">Décrit comment implémenter des gestionnaires pour plusieurs événements de mode virtuel.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="e1f1b-113">Montre également comment implémenter la restauration au niveau des lignes et validation pour les modifications de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="e1f1b-114">Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="e1f1b-115">Décrit comment charger des données à la demande, ce qui est utile lorsque vous avez plus de données à afficher que la mémoire du client peut stocker.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e1f1b-116">Référence</span><span class="sxs-lookup"><span data-stu-id="e1f1b-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="e1f1b-117">Fournit la documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="e1f1b-118">Fournit la documentation de référence pour le <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="e1f1b-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1f1b-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1f1b-119">See Also</span></span>  
 [<span data-ttu-id="e1f1b-120">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="e1f1b-120">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="e1f1b-121">Modes d’affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e1f1b-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
