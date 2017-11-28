---
title: "assemblys et exécution côte à côte"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d0f5e5d0e9a2385d3ebf1c2f1dc7838de79b27e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="92abd-102">assemblys et exécution côte à côte</span><span class="sxs-lookup"><span data-stu-id="92abd-102">Assemblies and Side-by-Side Execution</span></span>
<span data-ttu-id="92abd-103">L'exécution côte à côte consiste à stocker et exécuter plusieurs versions d'une application ou d'un composant sur un même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="92abd-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="92abd-104">Cela signifie que peuvent coexister simultanément sur un même ordinateur plusieurs versions du runtime ainsi que plusieurs versions d'applications et de composants utilisant une version du runtime.</span><span class="sxs-lookup"><span data-stu-id="92abd-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="92abd-105">L'exécution côte à côte vous offre un meilleur contrôle des versions auxquelles peut être liée une application ainsi que de la version du runtime utilisée par une application.</span><span class="sxs-lookup"><span data-stu-id="92abd-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
 <span data-ttu-id="92abd-106">La prise en charge du stockage et de l'exécution côte à côte de différentes versions du même assembly fait partie intégrante de l'attribution des noms forts et se trouve intégrée à l'infrastructure du runtime.</span><span class="sxs-lookup"><span data-stu-id="92abd-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="92abd-107">Comme le numéro de version de l'assembly avec nom fort fait partie de son identité, le runtime peut stocker plusieurs versions du même assembly dans le Global Assembly Cache et charger ces assemblys au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="92abd-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
 <span data-ttu-id="92abd-108">Bien que le runtime vous permette de créer des applications côte à côte, l'exécution côte à côte n'est pas automatique.</span><span class="sxs-lookup"><span data-stu-id="92abd-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="92abd-109">Pour plus d’informations sur la création d’applications pour une exécution côte à côte, consultez [Indications pour la création de composants pour l’exécution côte à côte](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="92abd-109">For more information on creating applications for side-by-side execution, see [Guidelines for Creating Components for Side-by-Side Execution](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92abd-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92abd-110">See Also</span></span>  
 [<span data-ttu-id="92abd-111">Méthode de localisation des assemblys par le runtime</span><span class="sxs-lookup"><span data-stu-id="92abd-111">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="92abd-112">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="92abd-112">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
