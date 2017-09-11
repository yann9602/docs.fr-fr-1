---
title: "Comment : charger et décharger des assemblys (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbc84236-04b6-4c1b-9672-52773f65a5dc
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2e38be72bb58573b532fa42a569563df0be8301d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-load-and-unload-assemblies-visual-basic"></a><span data-ttu-id="e376a-102">Comment : charger et décharger des assemblys (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e376a-102">How to: Load and Unload Assemblies (Visual Basic)</span></span>
<span data-ttu-id="e376a-103">Les assemblys référencés par votre programme seront chargés automatiquement au moment de la génération, mais il est également possible de charger des assemblys spécifiques dans le domaine d’application actuel lors de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e376a-103">The assemblies referenced by your program will automatically be loaded at build time, but it is also possible to load specific assemblies into the current application domain at runtime.</span></span> <span data-ttu-id="e376a-104">Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span><span class="sxs-lookup"><span data-stu-id="e376a-104">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
 <span data-ttu-id="e376a-105">Il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="e376a-105">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="e376a-106">Même si l’assembly est hors de portée, le fichier d’assembly réel restera chargé jusqu'à ce que tous les domaines d’application qui le contiennent sont déchargées.</span><span class="sxs-lookup"><span data-stu-id="e376a-106">Even if the assembly goes out of scope, the actual assembly file will remain loaded until all application domains that contain it are unloaded.</span></span>  
  
 <span data-ttu-id="e376a-107">Si vous souhaitez décharger certains assemblys, mais pas d’autres, envisagez la création d’un nouveau domaine d’application, l’exécution du code à l’intérieur de ce domaine, puis déchargez le domaine.</span><span class="sxs-lookup"><span data-stu-id="e376a-107">If you want to unload some assemblies but not others, consider creating a new application domain, executing the code inside that domain, and then unloading that application domain.</span></span> <span data-ttu-id="e376a-108">Pour plus d’informations, consultez [Comment : décharger un domaine d’Application](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span><span class="sxs-lookup"><span data-stu-id="e376a-108">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a><span data-ttu-id="e376a-109">Pour charger un assembly dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="e376a-109">To load an assembly into an application domain</span></span>  
  
1.  <span data-ttu-id="e376a-110">Utilisez une des nombreuses méthodes de chargement contenues dans les classes <xref:System.AppDomain>et <xref:System.Reflection>.</xref:System.Reflection> </xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="e376a-110">Use one of the several load methods contained in the classes <xref:System.AppDomain> and <xref:System.Reflection>.</span></span> <span data-ttu-id="e376a-111">Pour plus d’informations, consultez [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span><span class="sxs-lookup"><span data-stu-id="e376a-111">For more information, see [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9).</span></span>  
  
### <a name="to-unload-an-application-domain"></a><span data-ttu-id="e376a-112">Pour décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="e376a-112">To unload an application domain</span></span>  
  
1.  <span data-ttu-id="e376a-113">Il n’existe aucun moyen de décharger un assembly individuel sans décharger tous les domaines d’application qui le contiennent.</span><span class="sxs-lookup"><span data-stu-id="e376a-113">There is no way to unload an individual assembly without unloading all of the application domains that contain it.</span></span> <span data-ttu-id="e376a-114">Utilisez le `Unload` méthode <xref:System.AppDomain>pour décharger les domaines d’application.</xref:System.AppDomain></span><span class="sxs-lookup"><span data-stu-id="e376a-114">Use the `Unload` method from <xref:System.AppDomain> to unload the application domains.</span></span> <span data-ttu-id="e376a-115">Pour plus d’informations, consultez [Comment : décharger un domaine d’Application](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span><span class="sxs-lookup"><span data-stu-id="e376a-115">For more information, see [How to: Unload an Application Domain](http://msdn.microsoft.com/library/f356116d-e415-4f7c-a332-6e6a60227192).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e376a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e376a-116">See Also</span></span>  
 <span data-ttu-id="e376a-117">[Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="e376a-117">[Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="e376a-118"> [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="e376a-118"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="e376a-119"> [Comment : charger des assemblys dans un domaine d’Application](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span><span class="sxs-lookup"><span data-stu-id="e376a-119"> [How to: Load Assemblies into an Application Domain](http://msdn.microsoft.com/library/1432aa2d-bd83-4346-bf3b-a1b7920e2aa9)</span></span>
