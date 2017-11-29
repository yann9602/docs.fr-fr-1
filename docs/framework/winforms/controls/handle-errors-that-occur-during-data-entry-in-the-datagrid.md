---
title: "Comment : gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms"
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
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aec9ac6523c014b5e5b39629b4deaeee54295577
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8de60-102">Comment : gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de60-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8de60-103">L'exemple de code suivant montre comment utiliser le contrôle <xref:System.Windows.Forms.DataGridView> pour signaler des erreurs de saisie de données à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8de60-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="8de60-104">Pour obtenir une explication complète de cet exemple de code, consultez [procédure pas à pas : gestion des erreurs qui se produisent pendant la saisie de données dans le contrôle DataGridView Windows Forms](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="8de60-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8de60-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="8de60-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8de60-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8de60-106">Compiling the Code</span></span>  
 <span data-ttu-id="8de60-107">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="8de60-107">This example requires:</span></span>  
  
-   <span data-ttu-id="8de60-108">des références aux assemblys System, System.Data, System.Windows.Forms et System.XML.</span><span class="sxs-lookup"><span data-stu-id="8de60-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="8de60-109">Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consultez [Génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [Génération à partir de la ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8de60-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8de60-110">Vous pouvez également générer cet exemple dans [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] en collant le code dans un nouveau projet.</span><span class="sxs-lookup"><span data-stu-id="8de60-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="8de60-111">Consultez également [Guide pratique pour compiler et exécuter un exemple complet de code Windows Forms à l’aide de Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8de60-111">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8de60-112">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8de60-112">.NET Framework Security</span></span>  
 <span data-ttu-id="8de60-113">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="8de60-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="8de60-114">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="8de60-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="8de60-115">Pour plus d’informations, consultez [Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="8de60-115">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8de60-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8de60-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="8de60-117">Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de60-117">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 [<span data-ttu-id="8de60-118">Saisie de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de60-118">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="8de60-119">Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8de60-119">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="8de60-120">Protection des informations de connexion</span><span class="sxs-lookup"><span data-stu-id="8de60-120">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)
