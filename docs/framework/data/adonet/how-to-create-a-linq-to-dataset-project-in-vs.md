---
title: "Comment : créer un projet LINQ to DataSet dans Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3add191250a10d1d6016263ada0ba53fc8082717
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="e30d0-102">Comment : créer un projet LINQ to DataSet dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e30d0-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="e30d0-103">Les différents types de projets [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] nécessitent certains espaces de noms importés (Visual Basic) ou directives `using` (C#) et références.</span><span class="sxs-lookup"><span data-stu-id="e30d0-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="e30d0-104">Il doit y avoir au minimum une référence à System.Core.dll et une directive `using` pour <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="e30d0-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="e30d0-105">Celles-ci sont fournies par défaut si vous créez un projet [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e30d0-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="e30d0-106"> requiert également une référence à System.Data.dll et System.Data.DataSetExtensions.dll et une directive `Imports` (Visual Basic) ou `using` (C#).</span><span class="sxs-lookup"><span data-stu-id="e30d0-106"> also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="e30d0-107">Si vous effectuez la mise à niveau d'un projet à partir d'une version antérieure de Visual Studio, vous devrez fournir manuellement ces références liées à LINQ.</span><span class="sxs-lookup"><span data-stu-id="e30d0-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="e30d0-108">Il vous faudra également définir manuellement le projet pour cibler le .NET Framework version 3.5.</span><span class="sxs-lookup"><span data-stu-id="e30d0-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e30d0-109">Si vous générez à partir d’une invite de commandes, vous devez référencer manuellement les DLL liées à LINQ dans `drive` **:**\Program Assemblies\Microsoft\Framework\v3.5.</span><span class="sxs-lookup"><span data-stu-id="e30d0-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="e30d0-110">Pour cibler .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="e30d0-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="e30d0-111">Dans [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], créez un nouveau projet Visual Basic ou C#.</span><span class="sxs-lookup"><span data-stu-id="e30d0-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="e30d0-112">Vous pouvez également ouvrir un projet Visual Basic ou C# qui a été créé dans Visual Studio 2005 et suivre les invites pour le convertir en projet [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e30d0-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="e30d0-113">Pour un projet c#, cliquez sur le **projet** menu, puis sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e30d0-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="e30d0-114">Dans le **Application** page de propriétés, sélectionnez .NET Framework 3.5 dans le **Framework cible** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e30d0-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="e30d0-115">Pour un projet Visual Basic, cliquez sur le **projet** menu, puis sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="e30d0-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="e30d0-116">Dans le **compiler** page de propriétés, cliquez sur **Options avancées de compilation** , puis sélectionnez .NET Framework 3.5 dans le **Framework cible (toutes les configurations)** liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="e30d0-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="e30d0-117">Sur le **projet** menu, cliquez sur **ajouter une référence**, cliquez sur le **.NET** onglet, faites défiler jusqu'à **System.Core**, cliquez dessus, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="e30d0-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="e30d0-118">Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Linq> à votre fichier de code source ou votre projet.</span><span class="sxs-lookup"><span data-stu-id="e30d0-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="e30d0-119">Pour plus d’informations, consultez [à l’aide de la Directive](~/docs/csharp/language-reference/keywords/using-directive.md) ou [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e30d0-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="e30d0-120">Pour activer les fonctionnalités LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e30d0-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="e30d0-121">Si nécessaire, suivez les étapes décrites précédemment dans cette rubrique pour ajouter une référence à System.Core.dll et une directive `using` ou un espace de noms importé pour System.Linq.</span><span class="sxs-lookup"><span data-stu-id="e30d0-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="e30d0-122">En c# ou Visual Basic, cliquez sur le **projet** menu, puis sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="e30d0-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="e30d0-123">Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **.NET** onglet si elle n’est pas visible.</span><span class="sxs-lookup"><span data-stu-id="e30d0-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="e30d0-124">Faites défiler jusqu'à **System.Data** et **System.Data.DataSetExtensions** et cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="e30d0-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="e30d0-125">Cliquez sur le **OK** bouton.</span><span class="sxs-lookup"><span data-stu-id="e30d0-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="e30d0-126">Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Data> à votre fichier de code source ou votre projet.</span><span class="sxs-lookup"><span data-stu-id="e30d0-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="e30d0-127">Pour plus d’informations, consultez [à l’aide de la Directive](~/docs/csharp/language-reference/keywords/using-directive.md) ou [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e30d0-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="e30d0-128">Ajouter une référence à System.Data.DataSetExtensions.dll pour la fonctionnalité LINQ to Dataset.</span><span class="sxs-lookup"><span data-stu-id="e30d0-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="e30d0-129">Ajoutez une référence à System.Data.dll si elle n'existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="e30d0-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="e30d0-130">Si vous le souhaitez, ajoutez une directive `using` ou un espace de noms importé pour `System.Data.Common` ou `System.Data.SqlClient`, selon la façon dont vous vous connectez à la base de données.</span><span class="sxs-lookup"><span data-stu-id="e30d0-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e30d0-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e30d0-131">See Also</span></span>  
 [<span data-ttu-id="e30d0-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="e30d0-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="e30d0-133">Bien démarrer avec LINQ</span><span class="sxs-lookup"><span data-stu-id="e30d0-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
