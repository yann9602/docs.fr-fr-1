---
title: "Guide pratique pour charger et décharger des assemblys (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6bf6de24f4cbc3f3bd855b6d2cafa8120ebd90ee
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-load-and-unload-assemblies-c"></a><span data-ttu-id="3d900-102">Guide pratique pour charger et décharger des assemblys (C#)</span><span class="sxs-lookup"><span data-stu-id="3d900-102">How to: Load and Unload Assemblies (C#)</span></span>
<span data-ttu-id="3d900-103">Les assemblys référencés par votre programme sont chargés automatiquement au moment de la génération, mais il est également possible de charger des assemblys spécifiques dans le domaine d’application actif au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="3d900-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="3d900-104">Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="3d900-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="3d900-105">Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="3d900-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="3d900-106">Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés.</span><span class="sxs-lookup"><span data-stu-id="3d900-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="3d900-107">Si vous souhaitez décharger uniquement certains assemblys, créez un domaine d’application, exécutez le code à l’intérieur de ce domaine, puis déchargez le domaine.</span><span class="sxs-lookup"><span data-stu-id="3d900-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="3d900-108">Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="3d900-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="3d900-109">Pour charger un assembly dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="3d900-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="3d900-110">Utilisez une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain> et <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="3d900-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="3d900-111">Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="3d900-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="3d900-112">Pour décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="3d900-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="3d900-113">Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="3d900-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="3d900-114">Utilisez la méthode `Unload` de <xref:System.AppDomain> pour décharger les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="3d900-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="3d900-115">Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="3d900-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d900-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d900-116">See Also</span></span>  
 <span data-ttu-id="3d900-117">[Guide de programmation C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d900-117">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="3d900-118">[Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d900-118">[Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
 [<span data-ttu-id="3d900-119">Guide pratique pour charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="3d900-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)

