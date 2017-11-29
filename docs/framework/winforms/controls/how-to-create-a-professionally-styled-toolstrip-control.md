---
title: "Comment : créer un contrôle ToolStrip de style professionnel"
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
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0199bad54d7b4ed4f1ed63b22914f8f99bbf6e85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a><span data-ttu-id="203ff-102">Comment : créer un contrôle ToolStrip de style professionnel</span><span class="sxs-lookup"><span data-stu-id="203ff-102">How to: Create a Professionally Styled ToolStrip Control</span></span>
<span data-ttu-id="203ff-103">Vous pouvez donner aux contrôles <xref:System.Windows.Forms.ToolStrip> de votre application une apparence et un comportement professionnels en écrivant votre propre classe dérivée du type <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.</span><span class="sxs-lookup"><span data-stu-id="203ff-103">You can give your application’s <xref:System.Windows.Forms.ToolStrip> controls a professional appearance and behavior (look and feel) by writing your own class derived from the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> type.</span></span>  
  
 <span data-ttu-id="203ff-104">[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]propose une prise en charge étendue pour cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="203ff-104">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="203ff-105">Consultez [Procédure pas à pas : création d’un contrôle ToolStrip de style professionnel](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span><span class="sxs-lookup"><span data-stu-id="203ff-105">See [Walkthrough: Creating a Professionally Styled ToolStrip Control](../../../../docs/framework/winforms/controls/walkthrough-creating-a-professionally-styled-toolstrip-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="203ff-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="203ff-106">Example</span></span>  
 <span data-ttu-id="203ff-107">L’exemple de code suivant montre comment utiliser <xref:System.Windows.Forms.ToolStrip> des contrôles pour créer un contrôle composite qui reproduit le **volet de Navigation** fourni par Microsoft® Outlook®.</span><span class="sxs-lookup"><span data-stu-id="203ff-107">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStrip> controls to create a composite control that mimics the **Navigation Pane** provided by Microsoft® Outlook®.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="203ff-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="203ff-108">Compiling the Code</span></span>  
 <span data-ttu-id="203ff-109">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="203ff-109">This example requires:</span></span>  
  
-   <span data-ttu-id="203ff-110">Références aux assemblys System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="203ff-110">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="203ff-111">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="203ff-111">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="203ff-112">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="203ff-112">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="203ff-113">Consultez [Procédure pas à pas : création d’un contrôle ToolStrip de style professionnel](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="203ff-113">Also see [Walkthrough: Creating a Professionally Styled ToolStrip Control](http://msdn.microsoft.com/library/ms233664\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="203ff-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="203ff-114">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="203ff-115">Contrôle ToolStrip</span><span class="sxs-lookup"><span data-stu-id="203ff-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="203ff-116">Comment : fournir des éléments de menu standard à un formulaire</span><span class="sxs-lookup"><span data-stu-id="203ff-116">How to: Provide Standard Menu Items to a Form</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
