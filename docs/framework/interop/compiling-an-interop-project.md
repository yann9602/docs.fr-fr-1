---
title: "Compilation d'un projet d'interopérabilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc541911670c533caa97c645085ad09bde5eefdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="d7f7e-102">Compilation d'un projet d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d7f7e-102">Compiling an Interop Project</span></span>
<span data-ttu-id="d7f7e-103">Les projets de COM Interop qui référencent un ou plusieurs assemblys contenant des types COM importés sont compilés comme tout autre projet managé.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="d7f7e-104">Vous pouvez référencer des assemblys d’interopérabilité dans un environnement de développement tel que Visual Studio, ou vous pouvez les référencer quand vous utilisez un compilateur de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="d7f7e-105">Dans les deux cas, l’assembly d’interopérabilité doit figurer dans le même répertoire que les autres fichiers projet pour que la compilation réussisse.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="d7f7e-106">Il existe deux façons de référencer des assemblys d’interopérabilité :</span><span class="sxs-lookup"><span data-stu-id="d7f7e-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="d7f7e-107">En utilisant des types interop incorporés : à compter de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], vous pouvez indiquer au compilateur d’incorporer les informations de type d’un assembly d’interopérabilité dans votre exécutable.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="d7f7e-108">Il s'agit de la technique recommandée.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="d7f7e-109">En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="d7f7e-110">Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="d7f7e-111">Les différences entre ces deux techniques sont abordées de manière plus détaillée dans [Utilisation de types COM dans du code managé](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span><span class="sxs-lookup"><span data-stu-id="d7f7e-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
 <span data-ttu-id="d7f7e-112">L’incorporation des types interop avec Visual Studio est illustrée dans [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) et [Procédure pas à pas : incorporation de types provenant d’assemblys managés](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="d7f7e-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) and [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="d7f7e-113">Pour référencer un assembly d’interopérabilité avec un compilateur de ligne de commande et pour incorporer des informations de type dans vos fichiers exécutables, utilisez le commutateur de compilateur [/link (Options du compilateur C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) ou [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7f7e-114">Les applications Visual C++ ne peuvent pas incorporer d’informations de type, mais elles peuvent interagir avec des applications ou des compléments qui le font.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="d7f7e-115">Pour compiler une application qui inclut un assembly PIA quand elle est déployée, utilisez le commutateur de compilateur **/reference** et spécifiez le nom de l’assembly d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="d7f7e-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7f7e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7f7e-116">See Also</span></span>  
 [<span data-ttu-id="d7f7e-117">Exposition de composants COM au .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d7f7e-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="d7f7e-118">Indépendance du langage et composants indépendants du langage</span><span class="sxs-lookup"><span data-stu-id="d7f7e-118">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="d7f7e-119">Utilisation de Types COM en Code managé</span><span class="sxs-lookup"><span data-stu-id="d7f7e-119">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="d7f7e-120">Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="d7f7e-120">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="d7f7e-121">Procédure pas à pas : incorporation de types provenant d’assemblys managés</span><span class="sxs-lookup"><span data-stu-id="d7f7e-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="d7f7e-122">Importation d'une bibliothèque de types sous la forme d'un assembly</span><span class="sxs-lookup"><span data-stu-id="d7f7e-122">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
