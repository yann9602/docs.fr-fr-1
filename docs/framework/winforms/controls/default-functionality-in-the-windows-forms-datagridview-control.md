---
title: "Fonctionnalités par défaut du contrôle DataGridView Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], default functionality in DataGridView control
- DataGridView control [Windows Forms], default functionality
ms.assetid: 4405f697-cad1-4839-9bcd-8ddb09d9f00e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecb8cdaa4e8eb0498259c597e0de3f80c3106549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="default-functionality-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="339dc-102">Fonctionnalités par défaut du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="339dc-102">Default Functionality in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="339dc-103">Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle permet aux utilisateurs d’une quantité importante de fonctionnalités par défaut.</span><span class="sxs-lookup"><span data-stu-id="339dc-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control provides users with a significant amount of default functionality.</span></span>  
  
## <a name="default-functionality"></a><span data-ttu-id="339dc-104">Fonctionnalité par défaut</span><span class="sxs-lookup"><span data-stu-id="339dc-104">Default Functionality</span></span>  
 <span data-ttu-id="339dc-105">Par défaut, un <xref:System.Windows.Forms.DataGridView> contrôle :</span><span class="sxs-lookup"><span data-stu-id="339dc-105">By default, a <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <span data-ttu-id="339dc-106">Affiche automatiquement les en-têtes de colonne et les en-têtes de lignes restent visibles pendant que la table fait défiler verticalement.</span><span class="sxs-lookup"><span data-stu-id="339dc-106">Automatically displays column headers and row headers that remain visible as the table scrolls vertically.</span></span>  
  
-   <span data-ttu-id="339dc-107">A un en-tête de ligne qui contient un indicateur de sélection de la ligne actuelle.</span><span class="sxs-lookup"><span data-stu-id="339dc-107">Has a row header that contains a selection indicator for the current row.</span></span>  
  
-   <span data-ttu-id="339dc-108">A un rectangle de sélection dans la première cellule.</span><span class="sxs-lookup"><span data-stu-id="339dc-108">Has a selection rectangle in the first cell.</span></span>  
  
-   <span data-ttu-id="339dc-109">Contient des colonnes qui peuvent être redimensionnés automatiquement quand l’utilisateur double-clique sur les séparateurs de colonnes.</span><span class="sxs-lookup"><span data-stu-id="339dc-109">Has columns that can be automatically resized when the user double-clicks the column dividers.</span></span>  
  
-   <span data-ttu-id="339dc-110">Prend en charge automatiquement les styles visuels sur Windows XP et la famille Windows Server 2003 lorsque la <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> méthode est appelée à partir de l’application `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="339dc-110">Automatically supports visual styles on Windows XP and the Windows Server 2003 family when the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method is called from the application's `Main` method.</span></span>  
  
 <span data-ttu-id="339dc-111">En outre, le contenu d’un <xref:System.Windows.Forms.DataGridView> contrôle peut être modifié par défaut :</span><span class="sxs-lookup"><span data-stu-id="339dc-111">Additionally, the contents of a <xref:System.Windows.Forms.DataGridView> control can be edited by default:</span></span>  
  
-   <span data-ttu-id="339dc-112">Si l’utilisateur double-clique ou appuie sur F2 dans une cellule, le contrôle met la cellule en mode édition et le contenu de la cellule en tant que l’utilisateur tape des mises à jour automatiquement.</span><span class="sxs-lookup"><span data-stu-id="339dc-112">If the user double-clicks or presses F2 in a cell, the control automatically puts the cell into edit mode and updates the contents of the cell as the user types.</span></span>  
  
-   <span data-ttu-id="339dc-113">Si l’utilisateur fait défiler jusqu'à la fin de la grille, il voit qu’une ligne pour ajouter de nouveaux enregistrements est présente.</span><span class="sxs-lookup"><span data-stu-id="339dc-113">If the user scrolls to the end of the grid, the user will see that a row for adding new records is present.</span></span> <span data-ttu-id="339dc-114">Lorsque l’utilisateur clique sur cette ligne, une nouvelle ligne est ajoutée à la <xref:System.Windows.Forms.DataGridView> contrôle, avec les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="339dc-114">When the user clicks this row, a new row is added to the <xref:System.Windows.Forms.DataGridView> control, with default values.</span></span> <span data-ttu-id="339dc-115">Lorsque l’utilisateur appuie sur ÉCHAP, cette nouvelle ligne disparaît.</span><span class="sxs-lookup"><span data-stu-id="339dc-115">When the user presses ESC, this new row disappears.</span></span>  
  
-   <span data-ttu-id="339dc-116">Si l’utilisateur clique sur un en-tête de ligne, la ligne entière est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="339dc-116">If the user clicks a row header, the whole row is selected.</span></span>  
  
 <span data-ttu-id="339dc-117">Lorsque vous liez un <xref:System.Windows.Forms.DataGridView> contrôle à une source de données en définissant ses <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété, le contrôle :</span><span class="sxs-lookup"><span data-stu-id="339dc-117">When you bind a <xref:System.Windows.Forms.DataGridView> control to a data source by setting its <xref:System.Windows.Forms.DataGridView.DataSource%2A> property, the control:</span></span>  
  
-   <span data-ttu-id="339dc-118">Utilise automatiquement les noms des colonnes de la source de données en tant que le texte d’en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="339dc-118">Automatically uses the names of the data source's columns as the column header text.</span></span>  
  
-   <span data-ttu-id="339dc-119">Est rempli avec le contenu de la source de données.</span><span class="sxs-lookup"><span data-stu-id="339dc-119">Is populated with the contents of the data source.</span></span> <span data-ttu-id="339dc-120"><xref:System.Windows.Forms.DataGridView>les colonnes sont créées automatiquement pour chaque colonne dans la source de données.</span><span class="sxs-lookup"><span data-stu-id="339dc-120"><xref:System.Windows.Forms.DataGridView> columns are automatically created for each column in the data source.</span></span>  
  
-   <span data-ttu-id="339dc-121">Crée une ligne pour chaque ligne visible dans la table.</span><span class="sxs-lookup"><span data-stu-id="339dc-121">Creates a row for each visible row in the table.</span></span>  
  
-   <span data-ttu-id="339dc-122">Trie automatiquement les lignes selon les données sous-jacentes lorsque l’utilisateur clique sur un en-tête de colonne.</span><span class="sxs-lookup"><span data-stu-id="339dc-122">Automatically sorts the rows based on the underlying data when the user clicks a column header.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="339dc-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="339dc-123">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="339dc-124">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="339dc-124">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
