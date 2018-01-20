---
title: "Comment : ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 971d3918fd6085bea85e43183ea67745d40e51b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="35546-102">Comment : ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="35546-102">How to: Add Columns to the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="35546-103">Windows Forms <xref:System.Windows.Forms.ListView> contrôle peut afficher plusieurs colonnes pour chaque liste élément lors de la **détails** vue.</span><span class="sxs-lookup"><span data-stu-id="35546-103">The Windows Forms <xref:System.Windows.Forms.ListView> control can display multiple columns for each list item when in the **Details** view.</span></span> <span data-ttu-id="35546-104">Vous pouvez utiliser les colonnes pour afficher plusieurs types d’informations sur chaque élément de liste.</span><span class="sxs-lookup"><span data-stu-id="35546-104">You can use the columns to display several types of information about each list item.</span></span> <span data-ttu-id="35546-105">Par exemple, une liste de fichiers peut afficher le nom de fichier, type de fichier, taille et date de que dernière modification du fichier.</span><span class="sxs-lookup"><span data-stu-id="35546-105">For example, a list of files could display the file name, file type, size, and date the file was last modified.</span></span> <span data-ttu-id="35546-106">Pour plus d’informations sur le remplissage des colonnes une fois qu’elles sont créées, consultez [Comment : afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span><span class="sxs-lookup"><span data-stu-id="35546-106">For information on populating the columns once they are created, see [How to: Display Subitems in Columns with the Windows Forms ListView Control](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).</span></span>  
  
 <span data-ttu-id="35546-107">La procédure suivante requiert un **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.ListView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="35546-107">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="35546-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="35546-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35546-109">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="35546-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="35546-110">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="35546-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="35546-111">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="35546-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-columns-in-the-designer"></a><span data-ttu-id="35546-112">Pour ajouter des colonnes dans le Concepteur</span><span class="sxs-lookup"><span data-stu-id="35546-112">To add columns in the designer</span></span>  
  
1.  <span data-ttu-id="35546-113">Dans le **propriétés** fenêtre, définissez du contrôle <xref:System.Windows.Forms.ListView.View%2A> propriété <xref:System.Windows.Forms.View.Details>.</span><span class="sxs-lookup"><span data-stu-id="35546-113">In the **Properties** window, set the control's <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Details>.</span></span>  
  
2.  <span data-ttu-id="35546-114">Dans le **propriétés** fenêtre, cliquez sur le **points de suspension** bouton (![capture d’écran de VisualStudioEllipsesButton](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) à côté le <xref:System.Windows.Forms.ListView.Columns%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="35546-114">In the **Properties** window, click the **Ellipsis** button (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) next to the <xref:System.Windows.Forms.ListView.Columns%2A> property.</span></span>  
  
     <span data-ttu-id="35546-115">Le **éditeur de Collection ColumnHeader** s’affiche.</span><span class="sxs-lookup"><span data-stu-id="35546-115">The **ColumnHeader Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="35546-116">Utilisez le **ajouter** bouton pour ajouter de nouvelles colonnes.</span><span class="sxs-lookup"><span data-stu-id="35546-116">Use the **Add** button to add new columns.</span></span> <span data-ttu-id="35546-117">Vous pouvez ensuite sélectionner l’en-tête de colonne et définir son texte (la légende de la colonne) ainsi que l’alignement du texte et la largeur.</span><span class="sxs-lookup"><span data-stu-id="35546-117">You can then select the column header and set its text (the caption of the column), text alignment, and width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35546-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35546-118">See Also</span></span>  
 [<span data-ttu-id="35546-119">Vue d’ensemble du contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="35546-119">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="35546-120">Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35546-120">How to: Add and Remove Items with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="35546-121">Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35546-121">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="35546-122">Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="35546-122">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="35546-123">Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="35546-123">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
