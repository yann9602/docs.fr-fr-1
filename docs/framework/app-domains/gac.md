---
title: Global Assembly Cache
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
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9ca51a06e6e7ec89576facf3a70c789325fd893c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="global-assembly-cache"></a><span data-ttu-id="f8be2-102">Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="f8be2-102">Global Assembly Cache</span></span>
<span data-ttu-id="f8be2-103">Chaque ordinateur sur lequel le Common Language Runtime est installé a un cache de code à l’échelle de l’ordinateur appelé Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-103">Each computer where the common language runtime is installed has a machine-wide code cache called the global assembly cache.</span></span> <span data-ttu-id="f8be2-104">Le Global Assembly Cache stocke les assemblys spécialement destinés à être partagés entre plusieurs applications sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f8be2-104">The global assembly cache stores assemblies specifically designated to be shared by several applications on the computer.</span></span>  
  
 <span data-ttu-id="f8be2-105">Vous ne devez partager des assemblys en les installant dans le Global Assembly Cache qu’en cas de nécessité.</span><span class="sxs-lookup"><span data-stu-id="f8be2-105">You should share assemblies by installing them into the global assembly cache only when you need to.</span></span> <span data-ttu-id="f8be2-106">En règle générale, vous devez maintenir les dépendances d’assembly privées et rechercher les assemblys dans le répertoire de l’application, sauf si le partage d’un assembly est explicitement requis.</span><span class="sxs-lookup"><span data-stu-id="f8be2-106">As a general guideline, keep assembly dependencies private, and locate assemblies in the application directory unless sharing an assembly is explicitly required.</span></span> <span data-ttu-id="f8be2-107">En outre, il n’est pas nécessaire d’installer des assemblys dans le Global Assembly Cache pour les rendre accessibles à COM Interop ou au code non managé.</span><span class="sxs-lookup"><span data-stu-id="f8be2-107">In addition, it is not necessary to install assemblies into the global assembly cache to make them accessible to COM interop or unmanaged code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8be2-108">Il existe des scénarios où vous ne souhaitez explicitement pas installer un assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-108">There are scenarios where you explicitly do not want to install an assembly into the global assembly cache.</span></span> <span data-ttu-id="f8be2-109">Si vous placez l’un des assemblys composant une application dans le Global Assembly Cache, vous ne pouvez plus répliquer ni installer l’application en utilisant la commande **xcopy** pour copier le répertoire de l’application.</span><span class="sxs-lookup"><span data-stu-id="f8be2-109">If you place one of the assemblies that make up an application in the global assembly cache, you can no longer replicate or install the application by using the **xcopy** command to copy the application directory.</span></span> <span data-ttu-id="f8be2-110">Vous devez également déplacer l’assembly dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-110">You must move the assembly in the global assembly cache as well.</span></span>  
  
 <span data-ttu-id="f8be2-111">Il existe deux manières de déployer un assembly dans le Global Assembly Cache :</span><span class="sxs-lookup"><span data-stu-id="f8be2-111">There are two ways to deploy an assembly into the global assembly cache:</span></span>  
  
-   <span data-ttu-id="f8be2-112">Utiliser un programme d’installation conçu pour fonctionner avec le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-112">Use an installer designed to work with the global assembly cache.</span></span> <span data-ttu-id="f8be2-113">Il s’agit de l’option par défaut d’installation d’assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-113">This is the preferred option for installing assemblies into the global assembly cache.</span></span>  
  
-   <span data-ttu-id="f8be2-114">Utiliser un outil de développement appelé [Outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) fourni avec le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8be2-114">Use a developer tool called the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md), provided by the [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8be2-115">Dans les scénarios de déploiement, utilisez Windows Installer pour installer des assemblys dans le Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-115">In deployment scenarios, use Windows Installer to install assemblies into the global assembly cache.</span></span> <span data-ttu-id="f8be2-116">Utilisez l’outil Global Assembly Cache uniquement dans les scénarios de développement, car il ne propose pas de fonctionnalités de décompte des références d’assembly et d’autres fonctionnalités disponibles lors de l’utilisation de Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="f8be2-116">Use the Global Assembly Cache tool only in development scenarios, because it does not provide assembly reference counting and other features provided when using the Windows Installer.</span></span>  
  
 <span data-ttu-id="f8be2-117">À compter du .NET Framework 4, l’emplacement par défaut du Global Assembly Cache est **%windir%\Microsoft.NET\assembly**.</span><span class="sxs-lookup"><span data-stu-id="f8be2-117">Starting with the .NET Framework 4, the default location for the global assembly cache is **%windir%\Microsoft.NET\assembly**.</span></span> <span data-ttu-id="f8be2-118">Dans les versions antérieures du .NET Framework, l’emplacement par défaut est **%windir%\assembly**.</span><span class="sxs-lookup"><span data-stu-id="f8be2-118">In earlier versions of the .NET Framework, the default location is **%windir%\assembly**.</span></span>  
  
 <span data-ttu-id="f8be2-119">Les administrateurs protègent souvent le répertoire systemroot en utilisant une liste de contrôle d’accès pour contrôler l’accès en écriture et en exécution.</span><span class="sxs-lookup"><span data-stu-id="f8be2-119">Administrators often protect the systemroot directory using an access control list (ACL) to control write and execute access.</span></span> <span data-ttu-id="f8be2-120">Le Global Assembly Cache étant installé dans un sous-répertoire du répertoire systemroot, il hérite de la liste de contrôle d’accès de ce répertoire.</span><span class="sxs-lookup"><span data-stu-id="f8be2-120">Because the global assembly cache is installed in a subdirectory of the systemroot directory, it inherits that directory's ACL.</span></span> <span data-ttu-id="f8be2-121">Il est recommandé que seuls les utilisateurs disposant de privilèges d’administrateur soient autorisés à supprimer des fichiers du Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="f8be2-121">It is recommended that only users with Administrator privileges be allowed to delete files from the global assembly cache.</span></span>  
  
 <span data-ttu-id="f8be2-122">Les assemblys déployés dans le Global Assembly Cache doivent avoir un nom fort.</span><span class="sxs-lookup"><span data-stu-id="f8be2-122">Assemblies deployed in the global assembly cache must have a strong name.</span></span> <span data-ttu-id="f8be2-123">Quand un assembly est ajouté au Global Assembly Cache, des contrôles d’intégrité sont effectués sur tous les fichiers qui composent l’assembly.</span><span class="sxs-lookup"><span data-stu-id="f8be2-123">When an assembly is added to the global assembly cache, integrity checks are performed on all files that make up the assembly.</span></span> <span data-ttu-id="f8be2-124">Le cache effectue ces contrôles d’intégrité pour vérifier qu’aucun assembly n’a été falsifié, par exemple quand un fichier a changé mais que le manifeste ne reflète pas ce changement.</span><span class="sxs-lookup"><span data-stu-id="f8be2-124">The cache performs these integrity checks to ensure that an assembly has not been tampered with, for example, when a file has changed but the manifest does not reflect the change.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8be2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8be2-125">See Also</span></span>  
 [<span data-ttu-id="f8be2-126">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="f8be2-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="f8be2-127">Utilisation d’assemblys et du Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="f8be2-127">Working with Assemblies and the Global Assembly Cache</span></span>](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [<span data-ttu-id="f8be2-128">Assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="f8be2-128">Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/strong-named-assemblies.md)
