---
title: Assemblys multifichiers
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- command-line compilers
- assembly manifest, multifile assemblies
- code modules
- multifile assemblies
ms.assetid: 13509e73-db77-4645-8165-aad8dfaedff6
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fead0a944b464ffd8f72dca6da33fd97404fe2d1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="multifile-assemblies"></a><span data-ttu-id="0b423-102">Assemblys multifichiers</span><span class="sxs-lookup"><span data-stu-id="0b423-102">Multifile Assemblies</span></span>
<span data-ttu-id="0b423-103">Vous pouvez créer des assemblys multifichiers à l’aide de compilateurs de ligne de commande ou [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] avec Visual C++.</span><span class="sxs-lookup"><span data-stu-id="0b423-103">You can create multifile assemblies using command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] with Visual C++.</span></span> <span data-ttu-id="0b423-104">L’un des fichiers de l’assembly doit contenir le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0b423-104">One file in the assembly must contain the assembly manifest.</span></span> <span data-ttu-id="0b423-105">Un assembly qui démarre une application doit également contenir un point d’entrée, tel que la méthode Main ou WinMain.</span><span class="sxs-lookup"><span data-stu-id="0b423-105">An assembly that starts an application must also contain an entry point, such as a Main or WinMain method.</span></span>  
  
 <span data-ttu-id="0b423-106">Supposons, par exemple, que vous possédiez une application contenant deux modules de code, Client.cs et Stringer.cs.</span><span class="sxs-lookup"><span data-stu-id="0b423-106">For example, suppose you have an application that contains two code modules, Client.cs and Stringer.cs.</span></span> <span data-ttu-id="0b423-107">Stringer.cs crée l’espace de noms `myStringer` qui est référencé par le code contenu dans Client.cs.</span><span class="sxs-lookup"><span data-stu-id="0b423-107">Stringer.cs creates the `myStringer` namespace that is referenced by the code in Client.cs.</span></span> <span data-ttu-id="0b423-108">Client.cs contient la méthode `Main` qui est le point d’entrée de l’application.</span><span class="sxs-lookup"><span data-stu-id="0b423-108">Client.cs contains the `Main` method, which is the application's entry point.</span></span> <span data-ttu-id="0b423-109">Dans cet exemple, vous compilez les deux modules de code, puis créez un troisième fichier qui contient le manifeste d’assembly, qui lance l’application.</span><span class="sxs-lookup"><span data-stu-id="0b423-109">In this example, you compile the two code modules, and then create a third file that contains the assembly manifest, which launches the application.</span></span> <span data-ttu-id="0b423-110">Le manifeste d’assembly référence les modules `Client` et `Stringer`.</span><span class="sxs-lookup"><span data-stu-id="0b423-110">The assembly manifest references both the `Client` and `Stringer` modules.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b423-111">Les assemblys multifichiers ne peuvent avoir qu’un seul point d’entrée, même si l’assembly a plusieurs modules de code.</span><span class="sxs-lookup"><span data-stu-id="0b423-111">Multifile assemblies can have only one entry point, even if the assembly has multiple code modules.</span></span>  
  
 <span data-ttu-id="0b423-112">Il est possible de créer un assembly multifichier pour plusieurs raisons :</span><span class="sxs-lookup"><span data-stu-id="0b423-112">There are several reasons you might want to create a multifile assembly:</span></span>  
  
-   <span data-ttu-id="0b423-113">Pour combiner des modules écrits dans différents langages.</span><span class="sxs-lookup"><span data-stu-id="0b423-113">To combine modules written in different languages.</span></span> <span data-ttu-id="0b423-114">Il s’agit de la raison la plus courante de créer un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="0b423-114">This is the most common reason for creating a multifile assembly.</span></span>  
  
-   <span data-ttu-id="0b423-115">Pour optimiser le téléchargement d’une application en plaçant des types rarement utilisés dans un module qui n’est téléchargé que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="0b423-115">To optimize downloading an application by putting seldom-used types in a module that is downloaded only when needed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0b423-116">Si vous créez des applications destinées à être téléchargées à l’aide de la balise `<object>` avec Microsoft Internet Explorer, il est important de créer des assemblys multifichiers.</span><span class="sxs-lookup"><span data-stu-id="0b423-116">If you are creating applications that will be downloaded using the `<object>` tag with Microsoft Internet Explorer, it is important that you create multifile assemblies.</span></span> <span data-ttu-id="0b423-117">Dans ce scénario, vous créez un fichier distinct de vos modules de code, qui contient uniquement le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0b423-117">In this scenario, you create a file separate from your code modules that contains only the assembly manifest.</span></span> <span data-ttu-id="0b423-118">Internet Explorer télécharge d’abord le manifeste d’assembly, puis crée des threads de travail pour télécharger tout assembly ou module supplémentaire requis.</span><span class="sxs-lookup"><span data-stu-id="0b423-118">Internet Explorer downloads the assembly manifest first, and then creates worker threads to download any additional modules or assemblies required.</span></span> <span data-ttu-id="0b423-119">Pendant le téléchargement du fichier contenant le manifeste d’assembly, Internet Explorer ne répond pas aux entrées d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0b423-119">While the file containing the assembly manifest is being downloaded, Internet Explorer will be unresponsive to user input.</span></span> <span data-ttu-id="0b423-120">La durée de non-réponse d’Internet Explorer est proportionnelle à la taille du fichier contenant le manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="0b423-120">The smaller the file containing the assembly manifest, the less time Internet Explorer will be unresponsive.</span></span>  
  
-   <span data-ttu-id="0b423-121">Pour combiner des modules de code écrits par plusieurs développeurs.</span><span class="sxs-lookup"><span data-stu-id="0b423-121">To combine code modules written by several developers.</span></span> <span data-ttu-id="0b423-122">Même si chaque développeur peut compiler chaque module de code dans un assembly, ceci peut forcer l’exposition publique de certains types qui ne sont pas exposés si tous les modules sont placés dans un assembly multifichier.</span><span class="sxs-lookup"><span data-stu-id="0b423-122">Although each developer can compile each code module into an assembly, this can force some types to be exposed publicly that are not exposed if all modules are put into a multifile assembly.</span></span>  
  
 <span data-ttu-id="0b423-123">Une fois l’assembly créé, vous pouvez signer le fichier qui contient le manifeste d’assembly (donc, l’assembly) ou attribuer au fichier (et à l’assembly) un nom fort et le placer dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="0b423-123">Once you create the assembly, you can sign the file that contains the assembly manifest (and hence the assembly), or you can give the file (and the assembly) a strong name and put it in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b423-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b423-124">See Also</span></span>  
 [<span data-ttu-id="0b423-125">Guide pratique pour générer un assembly multifichier</span><span class="sxs-lookup"><span data-stu-id="0b423-125">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="0b423-126">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="0b423-126">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
