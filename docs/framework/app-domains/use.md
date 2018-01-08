---
title: Utilisation des domaines d'application
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application domains, about
- common language runtime, application domains
- runtime, application domains
ms.assetid: c6d99815-e022-4d2c-9420-1d7ab5b9d504
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eade3728c8a51785214cf3d8de53d8a64a668f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-application-domains"></a><span data-ttu-id="0c2cf-102">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-102">Using Application Domains</span></span>
<span data-ttu-id="0c2cf-103">Les domaines d’application fournissent une unité d’isolation pour le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-103">Application domains provide a unit of isolation for the common language runtime.</span></span> <span data-ttu-id="0c2cf-104">Ils sont créés et exécutés dans un processus.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-104">They are created and run inside a process.</span></span> <span data-ttu-id="0c2cf-105">Les domaines d’application sont généralement créés par un hôte de runtime, qui est une application responsable du chargement du runtime dans un processus et de l’exécution du code utilisateur dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-105">Application domains are usually created by a runtime host, which is an application responsible for loading the runtime into a process and executing user code within an application domain.</span></span> <span data-ttu-id="0c2cf-106">L’hôte de runtime crée un processus et un domaine d’application par défaut et exécute le code managé dans ce domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-106">The runtime host creates a process and a default application domain, and runs managed code inside it.</span></span> <span data-ttu-id="0c2cf-107">Les hôtes de runtime comprennent ASP.NET, Microsoft Internet Explorer et le shell Windows.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-107">Runtime hosts include ASP.NET, Microsoft Internet Explorer, and the Windows shell.</span></span>  
  
 <span data-ttu-id="0c2cf-108">Pour la plupart des applications, vous n’êtes pas obligé de créer votre propre domaine d’application ; l’hôte du runtime se charge de créer le domaine d’application dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-108">For most applications, you do not need to create your own application domain; the runtime host creates any necessary application domains for you.</span></span> <span data-ttu-id="0c2cf-109">Toutefois, vous pouvez créer et configurer des domaines d’application supplémentaires si votre application doit isoler du code ou utiliser et décharger des DLL.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-109">However, you can create and configure additional application domains if your application needs to isolate code or to use and unload DLLs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c2cf-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0c2cf-110">In This Section</span></span>  
 [<span data-ttu-id="0c2cf-111">Guide pratique pour créer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-111">How to: Create an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-create-an-application-domain.md)  
 <span data-ttu-id="0c2cf-112">Décrit comment créer un domaine d’application par programmation.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-112">Describes how to programmatically create an application domain.</span></span>  
  
 [<span data-ttu-id="0c2cf-113">Guide pratique pour décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-113">How to: Unload an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-unload-an-application-domain.md)  
 <span data-ttu-id="0c2cf-114">Décrit comment décharger un domaine d’application par programmation.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-114">Describes how to programmatically unload an application domain.</span></span>  
  
 [<span data-ttu-id="0c2cf-115">Guide pratique pour configurer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-115">How to: Configure an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-configure-an-application-domain.md)  
 <span data-ttu-id="0c2cf-116">Propose une introduction à la configuration d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-116">Provides an introduction to configuring an application domain.</span></span>  
  
 [<span data-ttu-id="0c2cf-117">Récupération d'informations d'installation à partir d'un domaine d'application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-117">Retrieving Setup Information from an Application Domain</span></span>](../../../docs/framework/app-domains/retrieve-setup-information.md)  
 <span data-ttu-id="0c2cf-118">Décrit comment récupérer les informations de configuration d’un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-118">Describes how to retrieve setup information from an application domain.</span></span>  
  
 [<span data-ttu-id="0c2cf-119">Guide pratique pour charger des assemblys dans un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-119">How to: Load Assemblies into an Application Domain</span></span>](../../../docs/framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)  
 <span data-ttu-id="0c2cf-120">Décrit comment charger un assembly dans un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-120">Describes how to load an assembly into an application domain.</span></span>  
  
 [<span data-ttu-id="0c2cf-121">Guide pratique pour obtenir des informations relatives au type et aux membres à partir d'un assembly</span><span class="sxs-lookup"><span data-stu-id="0c2cf-121">How to: Obtain Type and Member Information from an Assembly</span></span>](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 <span data-ttu-id="0c2cf-122">Décrit comment récupérer des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-122">Describes how to retrieve information about an assembly.</span></span>  
  
 [<span data-ttu-id="0c2cf-123">Clichés instantanés d'assemblys</span><span class="sxs-lookup"><span data-stu-id="0c2cf-123">Shadow Copying Assemblies</span></span>](../../../docs/framework/app-domains/shadow-copy-assemblies.md)  
 <span data-ttu-id="0c2cf-124">Décrit comment utiliser des clichés instantanés pour mettre à jour des assemblys pendant leur utilisation, et comment configurer des clichés instantanés.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-124">Describes how shadow copying allows updates to assemblies while they are in use, and how to configure shadow copying.</span></span>  
  
 [<span data-ttu-id="0c2cf-125">Guide pratique pour recevoir des notifications des exceptions de première chance</span><span class="sxs-lookup"><span data-stu-id="0c2cf-125">How to: Receive First-Chance Exception Notifications</span></span>](../../../docs/framework/app-domains/how-to-receive-first-chance-exception-notifications.md)  
 <span data-ttu-id="0c2cf-126">Explique comment recevoir une notification indiquant qu’une exception a été levée, avant que le common language runtime ne commence à rechercher des gestionnaires d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-126">Explains how you can receive a notification that an exception has been thrown, before the common language runtime has begun searching for exception handlers.</span></span>  
  
 [<span data-ttu-id="0c2cf-127">Résoudre les chargements d'assemblys</span><span class="sxs-lookup"><span data-stu-id="0c2cf-127">Resolving Assembly Loads</span></span>](../../../docs/framework/app-domains/resolve-assembly-loads.md)  
 <span data-ttu-id="0c2cf-128">Offre des conseils sur l’utilisation de l’événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> pour résoudre les échecs de chargement de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-128">Provides guidance on using the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event to resolve assembly load failures.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0c2cf-129">Référence</span><span class="sxs-lookup"><span data-stu-id="0c2cf-129">Reference</span></span>  
 <xref:System.AppDomain>  
 <span data-ttu-id="0c2cf-130">Représente un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-130">Represents an application domain.</span></span> <span data-ttu-id="0c2cf-131">Fournit des méthodes pour la création et le contrôle des domaines d’application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-131">Provides methods for creating and controlling application domains.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0c2cf-132">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="0c2cf-132">Related Sections</span></span>  
 [<span data-ttu-id="0c2cf-133">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="0c2cf-133">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 <span data-ttu-id="0c2cf-134">Fournit une vue d’ensemble des fonctions exécutées par les assemblys.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-134">Provides an overview of the functions performed by assemblies.</span></span>  
  
 [<span data-ttu-id="0c2cf-135">Programmation à l’aide d’assemblys</span><span class="sxs-lookup"><span data-stu-id="0c2cf-135">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 <span data-ttu-id="0c2cf-136">Décrit comment créer, signer et définir des attributs sur des assemblys.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-136">Describes how to create, sign, and set attributes on assemblies.</span></span>  
  
 [<span data-ttu-id="0c2cf-137">Émission d’assemblys et de méthodes dynamiques</span><span class="sxs-lookup"><span data-stu-id="0c2cf-137">Emitting Dynamic Methods and Assemblies</span></span>](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)  
 <span data-ttu-id="0c2cf-138">Décrit comment créer des assemblys dynamiques.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-138">Describes how to create dynamic assemblies.</span></span>  
  
 [<span data-ttu-id="0c2cf-139">Domaines d’application</span><span class="sxs-lookup"><span data-stu-id="0c2cf-139">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="0c2cf-140">Fournit une vue d'ensemble conceptuelle des domaines d'application.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-140">Provides a conceptual overview of application domains.</span></span>  
  
 [<span data-ttu-id="0c2cf-141">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="0c2cf-141">Reflection Overview</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 <span data-ttu-id="0c2cf-142">Explique comment utiliser la classe **Reflection** pour obtenir des informations sur un assembly.</span><span class="sxs-lookup"><span data-stu-id="0c2cf-142">Describes how to use the **Reflection** class to obtain information about an assembly.</span></span>
