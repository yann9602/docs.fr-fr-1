---
title: Interfaces de fusion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9226eba1b9f03138180430b2abb960f43f4b4260
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-interfaces"></a><span data-ttu-id="fd833-102">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="fd833-102">Fusion Interfaces</span></span>
<span data-ttu-id="fd833-103">Cette section décrit les interfaces non managées que l’API de fusion utilise pour accéder aux propriétés des ressources d’une application et pour localiser les versions correctes de ces ressources pour l’application.</span><span class="sxs-lookup"><span data-stu-id="fd833-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd833-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="fd833-104">In This Section</span></span>  
 [<span data-ttu-id="fd833-105">IAppIdAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="fd833-106">Fournit des méthodes qui génèrent et comparer les clés pour les identités d’application et les références.</span><span class="sxs-lookup"><span data-stu-id="fd833-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="fd833-107">IAssemblyCache, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="fd833-108">Fournit une représentation du global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="fd833-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="fd833-109">IAssemblyCacheItem, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="fd833-110">Représente un seul assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="fd833-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="fd833-111">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="fd833-112">Représente un énumérateur pour un tableau de `IAssemblyName` objets.</span><span class="sxs-lookup"><span data-stu-id="fd833-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="fd833-113">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="fd833-114">Fournit des méthodes pour décrire et travailler avec l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="fd833-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="fd833-115">IDefinitionAppId, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="fd833-116">Représente un identificateur unique pour le code qui définit l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="fd833-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="fd833-117">IDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="fd833-118">Représente la signature unique du code qui définit l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="fd833-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="fd833-119">IEnumDefinitionIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="fd833-120">Sert d’énumérateur pour une collection de `IDefinitionIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="fd833-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="fd833-121">IEnumIDENTITY_ATTRIBUTE, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="fd833-122">Sert d’énumérateur pour les attributs de l’objet de code dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="fd833-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="fd833-123">IEnumReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="fd833-124">Sert d’énumérateur pour une collection de `IReferenceIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="fd833-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="fd833-125">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="fd833-126">Gère les clés d’identité pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="fd833-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="fd833-127">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="fd833-128">Représente un énumérateur pour les assemblys référencés installés dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="fd833-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="fd833-129">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="fd833-130">Représente un élément installé dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="fd833-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="fd833-131">IReferenceAppId, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="fd833-132">Représente une référence à l’identificateur unique pour l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="fd833-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="fd833-133">IReferenceIdentity, interface</span><span class="sxs-lookup"><span data-stu-id="fd833-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="fd833-134">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="fd833-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fd833-135">Référence</span><span class="sxs-lookup"><span data-stu-id="fd833-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="fd833-136">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="fd833-136">Related Sections</span></span>  
 [<span data-ttu-id="fd833-137">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="fd833-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="fd833-138">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="fd833-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="fd833-139">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="fd833-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
