---
title: "Comment : accéder à des objets liés à des lignes DataGridView Windows Forms"
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
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 910730f67024fbe0d292b4a329a36fb3ea8254b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="8ad1a-102">Comment : accéder à des objets liés à des lignes DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ad1a-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="8ad1a-103">Il est parfois utile d’afficher une table d’informations stockée dans une collection d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="8ad1a-104">Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une telle collection, chaque propriété publique est affichée dans sa propre colonne, à moins que la propriété n'ait été marquée comme non consultable avec un <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="8ad1a-105">Par exemple, une collection d’objets `Customer` aurait des colonnes telles que **Nom** et **Adresse**.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="8ad1a-106">Si ces objets contiennent des informations supplémentaires et du code auquel vous souhaitez accéder, vous pouvez l'atteindre via des objets de ligne.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="8ad1a-107">Dans l'exemple de code suivant, les utilisateurs peuvent sélectionner plusieurs lignes et cliquer sur un bouton pour envoyer une facture à chacun des clients correspondants.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="8ad1a-108">Pour accéder à des objets liés à une ligne</span><span class="sxs-lookup"><span data-stu-id="8ad1a-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="8ad1a-109">Utilisez la propriété <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="8ad1a-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="8ad1a-110">Example</span></span>  
 <span data-ttu-id="8ad1a-111">L'exemple de code complet comprend une implémentation `Customer` simple et lie le <xref:System.Windows.Forms.DataGridView> à un <xref:System.Collections.ArrayList> contenant quelques objets `Customer`.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="8ad1a-112">Le gestionnaire d'événements <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.Button?displayProperty=nameWithType> doit accéder aux objets `Customer` par l'intermédiaire des lignes, car la collection de clients n'est pas accessible en dehors du gestionnaire d'événements <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ad1a-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8ad1a-113">Compiling the Code</span></span>  
 <span data-ttu-id="8ad1a-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8ad1a-114">This example requires:</span></span>  
  
-   <span data-ttu-id="8ad1a-115">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="8ad1a-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8ad1a-116">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8ad1a-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8ad1a-117">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="8ad1a-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="8ad1a-118">Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8ad1a-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad1a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8ad1a-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8ad1a-120">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ad1a-120">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="8ad1a-121">Comment : lier des objets aux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8ad1a-121">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)
