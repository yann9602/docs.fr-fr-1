---
title: "Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fdb57cf2134ee4f221a26db61cfdcc48dc92548
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a><span data-ttu-id="1be25-102">Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur</span><span class="sxs-lookup"><span data-stu-id="1be25-102">How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer</span></span>
<span data-ttu-id="1be25-103">Windows Forms <xref:System.Windows.Forms.DataGridView> contrôle doit contenir des colonnes pour afficher des données.</span><span class="sxs-lookup"><span data-stu-id="1be25-103">The Windows Forms <xref:System.Windows.Forms.DataGridView> control must contain columns in order to display data.</span></span> <span data-ttu-id="1be25-104">Si vous envisagez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous-même.</span><span class="sxs-lookup"><span data-stu-id="1be25-104">If you plan to populate the control manually, you must add the columns yourself.</span></span> <span data-ttu-id="1be25-105">Ou bien, vous pouvez lier le contrôle à une source de données, ce qui génère et remplit automatiquement les colonnes.</span><span class="sxs-lookup"><span data-stu-id="1be25-105">Alternately, you can bind the control to a data source, which generates and populates the columns automatically.</span></span> <span data-ttu-id="1be25-106">Si la source de données contient plus de colonnes que vous souhaitez afficher, vous pouvez supprimer les colonnes inutiles.</span><span class="sxs-lookup"><span data-stu-id="1be25-106">If the data source contains more columns than you want to display, you can remove the unwanted columns.</span></span>  
  
 <span data-ttu-id="1be25-107">Les procédures suivantes requièrent une **Application Windows** projet avec un formulaire contenant un <xref:System.Windows.Forms.DataGridView> contrôle.</span><span class="sxs-lookup"><span data-stu-id="1be25-107">The following procedures require a **Windows Application** project with a form containing a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="1be25-108">Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’Application Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) et [Comment : ajouter des contrôles aux Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1be25-108">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1be25-109">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="1be25-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1be25-110">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="1be25-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1be25-111">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="1be25-111">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-a-column-using-the-designer"></a><span data-ttu-id="1be25-112">Pour ajouter une colonne à l’aide du Concepteur</span><span class="sxs-lookup"><span data-stu-id="1be25-112">To add a column using the designer</span></span>  
  
1.  <span data-ttu-id="1be25-113">Cliquez sur le glyphe de balise active (![glyphe de balise active](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit de la <xref:System.Windows.Forms.DataGridView> contrôler, puis sélectionnez **ajouter une colonne**.</span><span class="sxs-lookup"><span data-stu-id="1be25-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) on the upper-right corner of the <xref:System.Windows.Forms.DataGridView> control, and then select **Add Column**.</span></span>  
  
2.  <span data-ttu-id="1be25-114">Dans le **ajouter une colonne** boîte de dialogue, choisissez le **colonne liée aux données** option et sélectionnez une colonne de la source de données ou choisissez la **colonne indépendante** option et définissez la colonne à l’aide des champs fournis.</span><span class="sxs-lookup"><span data-stu-id="1be25-114">In the **Add Column** dialog box, choose the **Databound Column** option and select a column from the data source, or choose the **Unbound Column** option and define the column using the fields provided.</span></span>  
  
3.  <span data-ttu-id="1be25-115">Cliquez sur le **ajouter** pour ajouter la colonne, qui n’apparaissent dans le concepteur si les colonnes existantes ne remplissent pas déjà de la zone d’affichage de contrôle.</span><span class="sxs-lookup"><span data-stu-id="1be25-115">Click the **Add** button to add the column, causing it to appear in the designer if the existing columns do not already fill the control display area.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1be25-116">Vous pouvez modifier les propriétés des colonnes dans le **modifier les colonnes** la boîte de dialogue, vous pouvez accéder à partir de la balise du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1be25-116">You can modify column properties in the **Edit Columns** dialog box, which you can access from the control's smart tag.</span></span>  
  
### <a name="to-remove-a-column-using-the-designer"></a><span data-ttu-id="1be25-117">Pour supprimer une colonne à l’aide du Concepteur</span><span class="sxs-lookup"><span data-stu-id="1be25-117">To remove a column using the designer</span></span>  
  
1.  <span data-ttu-id="1be25-118">Choisissez **modifier les colonnes** à partir de la balise du contrôle.</span><span class="sxs-lookup"><span data-stu-id="1be25-118">Choose **Edit Columns** from the control's smart tag.</span></span>  
  
2.  <span data-ttu-id="1be25-119">Sélectionnez une colonne dans la **colonnes sélectionnées** liste.</span><span class="sxs-lookup"><span data-stu-id="1be25-119">Select a column from the **Selected Columns** list.</span></span>  
  
3.  <span data-ttu-id="1be25-120">Cliquez sur le **supprimer** bouton pour supprimer la colonne, qui n’apparaît plus dans le concepteur.</span><span class="sxs-lookup"><span data-stu-id="1be25-120">Click the **Remove** button to delete the column, causing it to disappear from the designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be25-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1be25-121">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="1be25-122">Comment : créer un projet d’Application Windows</span><span class="sxs-lookup"><span data-stu-id="1be25-122">How to: Create a Windows Application Project</span></span>](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)  
 [<span data-ttu-id="1be25-123">Comment : ajouter des contrôles à des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1be25-123">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)
