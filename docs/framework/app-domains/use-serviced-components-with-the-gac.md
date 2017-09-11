---
title: Utilisation de composants de service avec le Global Assembly Cache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 493ca9a2da4a06528eab9b87db78a5b7a49a2f1d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a><span data-ttu-id="c0663-102">Utilisation de composants de service avec le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="c0663-102">Using Serviced Components with the Global Assembly Cache</span></span>
<span data-ttu-id="c0663-103">Les composants pris en charge (composants COM+ de code managé) doivent être placés dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c0663-103">Serviced components (managed code COM+ components) should be put in the global assembly cache.</span></span> <span data-ttu-id="c0663-104">Dans certains scénarios, le common language runtime et les services COM+ peuvent gérer des composants pris en charge qui ne sont pas dans le Global Assembly Cache ; dans d’autres scénarios, cela est impossible.</span><span class="sxs-lookup"><span data-stu-id="c0663-104">In some scenarios, the common language runtime and COM+ Services can handle serviced components that are not in the global assembly cache; in other scenarios, they cannot.</span></span> <span data-ttu-id="c0663-105">Les scénarios suivants illustrent ce principe :</span><span class="sxs-lookup"><span data-stu-id="c0663-105">The following scenarios illustrate this:</span></span>  
  
-   <span data-ttu-id="c0663-106">Pour les composants pris en charge dans une application serveur COM+, l’assembly contenant les composants doit être dans le Global Assembly Cache, car Dllhost.exe ne s’exécute pas dans le même répertoire que celui qui contient les composants pris en charge.</span><span class="sxs-lookup"><span data-stu-id="c0663-106">For serviced components in a COM+ Server application, the assembly containing the components must be in the global assembly cache, because Dllhost.exe does not run in the same directory as the one that contains the serviced components.</span></span>  
  
-   <span data-ttu-id="c0663-107">Pour les composants pris en charge dans une application bibliothèque COM+, le runtime et les services COM+ peuvent résoudre la référence à l’assembly contenant les composants en effectuant une recherche dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="c0663-107">For serviced components in a COM+ Library application, the runtime and COM+ Services can resolve the reference to the assembly containing the components by searching in the current directory.</span></span> <span data-ttu-id="c0663-108">Dans ce cas, l’assembly ne devra pas se trouver dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="c0663-108">In this case, the assembly does not have to be in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="c0663-109">Pour les composants pris en charge dans une application ASP.NET, la situation est différente.</span><span class="sxs-lookup"><span data-stu-id="c0663-109">For serviced components in an ASP.NET application, the situation is different.</span></span> <span data-ttu-id="c0663-110">Si vous placez l’assembly contenant les composants pris en charge dans le répertoire bin de la base de l’application, et que vous utilisez l’inscription à la demande, l’assembly sera mis en mémoire fantôme dans le cache de téléchargement, car ASP.NET tire parti des possibilités de mémoire fantôme du runtime.</span><span class="sxs-lookup"><span data-stu-id="c0663-110">If you place the assembly containing the serviced components in the bin directory of the application base and use on-demand registration, the assembly will be shadow-copied into the download cache because ASP.NET leverages the shadow capabilities of the runtime.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0663-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0663-111">See Also</span></span>  
 <span data-ttu-id="c0663-112">[Utilisation d’assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span><span class="sxs-lookup"><span data-stu-id="c0663-112">[Working with Assemblies and the Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md) </span></span>  
 [<span data-ttu-id="c0663-113">Gacutil.exe (outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="c0663-113">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)

