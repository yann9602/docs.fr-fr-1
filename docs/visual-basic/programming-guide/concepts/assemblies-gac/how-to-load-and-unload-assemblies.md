---
title: "Comment : charger et décharger des assemblys (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd52a1094dba16c7e1bcba5bface9e13747cd4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="c2498-102">Comment : charger et décharger des assemblys (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2498-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="c2498-103">Les assemblys référencés par votre programme sont chargés automatiquement au moment de la génération, mais il est également possible de charger des assemblys spécifiques dans le domaine d’application actif au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="c2498-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="c2498-104">Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="c2498-104">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
 <span data-ttu-id="c2498-105">Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="c2498-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="c2498-106">Même si l’assembly passe hors de portée, le fichier d’assembly proprement dit restera chargé jusqu’à ce que tous les domaines d’application qui le contiennent soient déchargés.</span><span class="sxs-lookup"><span data-stu-id="c2498-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="c2498-107">Si vous souhaitez décharger uniquement certains assemblys, créez un domaine d’application, exécutez le code à l’intérieur de ce domaine, puis déchargez le domaine.</span><span class="sxs-lookup"><span data-stu-id="c2498-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="c2498-108">Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="c2498-108">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="c2498-109">Pour charger un assembly dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="c2498-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="c2498-110">Utilisez une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain> et <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="c2498-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="c2498-111">Pour plus d’informations, consultez [Guide pratique pour charger des assemblys dans un domaine d’Application](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="c2498-111">For more information, see [How to: Load Assemblies into an Application Domain](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="c2498-112">Pour décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="c2498-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="c2498-113">Il n’existe aucun moyen de décharger un assembly spécifique sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="c2498-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="c2498-114">Utilisez la méthode `Unload` de <xref:System.AppDomain> pour décharger les domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="c2498-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="c2498-115">Pour plus d’informations, consultez [Guide pratique pour décharger un domaine d’Application](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span><span class="sxs-lookup"><span data-stu-id="c2498-115">For more information, see [How to: Unload an Application Domain](../../../../framework/app-domains/how-to-unload-an-application-domain.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2498-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2498-116">See Also</span></span>  
 [<span data-ttu-id="c2498-117">Concepts de programmation</span><span class="sxs-lookup"><span data-stu-id="c2498-117">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)  
 [<span data-ttu-id="c2498-118">Assemblys et le Global Assembly Cache (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2498-118">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="c2498-119">Guide pratique pour charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="c2498-119">How to: Load Assemblies into an Application Domain</span></span>](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
