---
title: Guide pratique pour supprimer un assembly du Global Assembly Cache
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a17478c350d789d320e97d6b50d6f5f9daaf6db3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a><span data-ttu-id="e0c3f-102">Guide pratique pour supprimer un assembly du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e0c3f-102">How to: Remove an Assembly from the Global Assembly Cache</span></span>
<span data-ttu-id="e0c3f-103">Il existe deux façons de supprimer un assembly du Global Assembly Cache (GAC) :</span><span class="sxs-lookup"><span data-stu-id="e0c3f-103">There are two ways to remove an assembly from the global assembly cache (GAC):</span></span>  
  
-   <span data-ttu-id="e0c3f-104">Utilisation de l’[outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="e0c3f-104">By using the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span> <span data-ttu-id="e0c3f-105">Vous pouvez utiliser cette option pour désinstaller des assemblys que vous avez placés dans le GAC lors du développement et des tests.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-105">You can use this option to uninstall assemblies that you've placed in the GAC during development and testing.</span></span>  
  
-   <span data-ttu-id="e0c3f-106">Utilisation de [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span><span class="sxs-lookup"><span data-stu-id="e0c3f-106">By using [Windows Installer](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx).</span></span> <span data-ttu-id="e0c3f-107">Utilisez cette option pour désinstaller des assemblys quand vous testez des packages d'installation et pour les systèmes de production.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-107">You should use this option to uninstall assemblies when testing installation packages and for production systems.</span></span>  
  
### <a name="removing-an-assembly-with-gacutilexe"></a><span data-ttu-id="e0c3f-108">Suppression d'un assembly avec Gacutil.exe</span><span class="sxs-lookup"><span data-stu-id="e0c3f-108">Removing an assembly with Gacutil.exe</span></span>  
  
1.  <span data-ttu-id="e0c3f-109">À l'invite de commandes, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e0c3f-109">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="e0c3f-110">**gacutil –u** \<*nom_assembly*></span><span class="sxs-lookup"><span data-stu-id="e0c3f-110">**gacutil –u** \<*assembly name*></span></span>  
  
     <span data-ttu-id="e0c3f-111">Dans cette commande, *nom_assembly* est le nom de l’assembly à supprimer du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-111">In this command, *assembly name* is the name of the assembly to remove from the global assembly cache.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="e0c3f-112">Vous ne devez pas utiliser Gacutil.exe pour supprimer des assemblys sur des systèmes de production, en raison de la possibilité que l'assembly soit encore requis par certaines applications.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-112">You should not use Gacutil.exe to remove assemblies on production systems because of the possibility that the assembly may still be required by some application.</span></span> <span data-ttu-id="e0c3f-113">Au lieu de cela, vous devez utiliser Windows Installer, qui conserve un comptage des références pour chaque assembly qu'il installe dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-113">Instead, you should use the Windows Installer, which maintains a reference count for each assembly it installs in the GAC.</span></span>  
  
 <span data-ttu-id="e0c3f-114">L'exemple suivant supprime un assembly nommé `hello.dll` du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-114">The following example removes an assembly named `hello.dll` from the global assembly cache.</span></span>  
  
```  
gacutil -u hello  
```  
  
### <a name="removing-an-assembly-with-windows-installer"></a><span data-ttu-id="e0c3f-115">Suppression d'un assembly avec Windows Installer</span><span class="sxs-lookup"><span data-stu-id="e0c3f-115">Removing an assembly with Windows Installer</span></span>  
  
1.  <span data-ttu-id="e0c3f-116">Dans l’application **Programmes et fonctionnalités** du **Panneau de configuration**, sélectionnez l’application que vous voulez désinstaller.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-116">From the **Programs and Features** app in **Control Panel**, select the app that you want to uninstall.</span></span> <span data-ttu-id="e0c3f-117">Si le package d'installation a placé les assemblys dans le GAC, Windows Installer les supprime s'ils ne sont pas utilisés par une autre application.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-117">If the installation package placed assemblies in the GAC, Windows Installer will remove them if they are not used by another application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e0c3f-118">Windows Installer conserve un comptage des références pour les assemblys installés dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-118">Windows Installer maintains a reference count for assemblies installed in the GAC.</span></span> <span data-ttu-id="e0c3f-119">Un assembly est supprimé du GAC seulement quand son comptage des références atteint zéro, ce qui indique qu'il n'est utilisé par aucune application installée par un package Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="e0c3f-119">An assembly is removed from the GAC only when its reference count reaches zero, which indicates that it is not used by any application installed by a Windows Installer package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c3f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0c3f-120">See Also</span></span>  
 [<span data-ttu-id="e0c3f-121">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e0c3f-121">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="e0c3f-122">Guide pratique pour installer un assembly dans le Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="e0c3f-122">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="e0c3f-123">Gacutil.exe (outil Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="e0c3f-123">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
