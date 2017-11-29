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
ms.openlocfilehash: f1742025bed977dfd377a78db42df42c1bc43966
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="fusion-interfaces"></a><span data-ttu-id="ec5f7-102">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="ec5f7-102">Fusion Interfaces</span></span>
<span data-ttu-id="ec5f7-103">Cette section décrit les interfaces non managées que l’API de fusion utilise pour accéder aux propriétés des ressources d’une application et pour localiser les versions correctes de ces ressources pour l’application.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-103">This section describes the unmanaged interfaces that the fusion API uses to access the properties of an application's resources and to locate the correct versions of those resources for the application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec5f7-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ec5f7-104">In This Section</span></span>  
 [<span data-ttu-id="ec5f7-105">IAppIdAuthority (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-105">IAppIdAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)  
 <span data-ttu-id="ec5f7-106">Fournit des méthodes qui génèrent et comparer les clés pour les identités d’application et les références.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-106">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
 [<span data-ttu-id="ec5f7-107">IAssemblyCache (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-107">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 <span data-ttu-id="ec5f7-108">Fournit une représentation du global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-108">Provides a representation of the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ec5f7-109">IAssemblyCacheItem (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-109">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)  
 <span data-ttu-id="ec5f7-110">Représente un seul assembly dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-110">Represents a single assembly in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ec5f7-111">IAssemblyEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-111">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)  
 <span data-ttu-id="ec5f7-112">Représente un énumérateur pour un tableau de `IAssemblyName` objets.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-112">Represents an enumerator for an array of `IAssemblyName` objects.</span></span>  
  
 [<span data-ttu-id="ec5f7-113">IAssemblyName (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-113">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 <span data-ttu-id="ec5f7-114">Fournit des méthodes pour décrire et travailler avec l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-114">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
 [<span data-ttu-id="ec5f7-115">IDefinitionAppId (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-115">IDefinitionAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md)  
 <span data-ttu-id="ec5f7-116">Représente un identificateur unique pour le code qui définit l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-116">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ec5f7-117">IDefinitionIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-117">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 <span data-ttu-id="ec5f7-118">Représente la signature unique du code qui définit l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-118">Represents the unique signature of the code that defines the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ec5f7-119">IEnumDefinitionIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-119">IEnumDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md)  
 <span data-ttu-id="ec5f7-120">Sert d’énumérateur pour une collection de `IDefinitionIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-120">Serves as the enumerator for a collection of `IDefinitionIdentity` objects.</span></span>  
  
 [<span data-ttu-id="ec5f7-121">IEnumIDENTITY_ATTRIBUTE (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-121">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)  
 <span data-ttu-id="ec5f7-122">Sert d’énumérateur pour les attributs de l’objet de code dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-122">Serves as an enumerator for the attributes of the code object in the current scope.</span></span>  
  
 [<span data-ttu-id="ec5f7-123">IEnumReferenceIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-123">IEnumReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumreferenceidentity-interface.md)  
 <span data-ttu-id="ec5f7-124">Sert d’énumérateur pour une collection de `IReferenceIdentity` objets.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-124">Serves as an enumerator for a collection of `IReferenceIdentity` objects.</span></span>  
  
 [<span data-ttu-id="ec5f7-125">IIdentityAuthority (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-125">IIdentityAuthority Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)  
 <span data-ttu-id="ec5f7-126">Gère les clés d’identité pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-126">Manages identity keys for code objects.</span></span>  
  
 [<span data-ttu-id="ec5f7-127">IInstallReferenceEnum (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-127">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 <span data-ttu-id="ec5f7-128">Représente un énumérateur pour les assemblys référencés installés dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-128">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ec5f7-129">IInstallReferenceItem (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-129">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 <span data-ttu-id="ec5f7-130">Représente un élément installé dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-130">Represents an item installed in the global assembly cache.</span></span>  
  
 [<span data-ttu-id="ec5f7-131">IReferenceAppId (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-131">IReferenceAppId Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md)  
 <span data-ttu-id="ec5f7-132">Représente une référence à l’identificateur unique pour l’application dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-132">Represents a reference to the unique identifier for the application in the current scope.</span></span>  
  
 [<span data-ttu-id="ec5f7-133">IReferenceIdentity (Interface)</span><span class="sxs-lookup"><span data-stu-id="ec5f7-133">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)  
 <span data-ttu-id="ec5f7-134">Représente une référence à la signature unique d’un objet de code.</span><span class="sxs-lookup"><span data-stu-id="ec5f7-134">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec5f7-135">Référence</span><span class="sxs-lookup"><span data-stu-id="ec5f7-135">Reference</span></span>  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a><span data-ttu-id="ec5f7-136">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ec5f7-136">Related Sections</span></span>  
 [<span data-ttu-id="ec5f7-137">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="ec5f7-137">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
  
 [<span data-ttu-id="ec5f7-138">Énumérations de fusion</span><span class="sxs-lookup"><span data-stu-id="ec5f7-138">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [<span data-ttu-id="ec5f7-139">Structures de fusion</span><span class="sxs-lookup"><span data-stu-id="ec5f7-139">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
