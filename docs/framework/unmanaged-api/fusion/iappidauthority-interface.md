---
title: IAppIdAuthority, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppIdAuthority
api_location: fusion.dll
api_type: COM
f1_keywords: IAppIdAuthority
helpviewer_keywords: IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c51aac28864cba5f538f7829ba4112b141c9a3c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iappidauthority-interface"></a><span data-ttu-id="4020e-102">IAppIdAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="4020e-102">IAppIdAuthority Interface</span></span>
<span data-ttu-id="4020e-103">Fournit des méthodes qui génèrent et comparer les clés pour les identités d’application et les références.</span><span class="sxs-lookup"><span data-stu-id="4020e-103">Provides methods that generate and compare keys for application identities and references.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4020e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4020e-104">Methods</span></span>  
  
|<span data-ttu-id="4020e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="4020e-105">Method</span></span>|<span data-ttu-id="4020e-106">Description</span><span class="sxs-lookup"><span data-stu-id="4020e-106">Description</span></span>|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|<span data-ttu-id="4020e-107">Obtient une valeur qui indique si les deux spécifiés [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances sont égales.</span><span class="sxs-lookup"><span data-stu-id="4020e-107">Gets a value that indicates whether the two specified [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) instances are equal.</span></span> <span data-ttu-id="4020e-108">Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="4020e-108">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreReferencesEqual`|<span data-ttu-id="4020e-109">Obtient une valeur qui indique si les deux spécifiés [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances sont égales.</span><span class="sxs-lookup"><span data-stu-id="4020e-109">Gets a value that indicates whether the two specified [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) instances are equal.</span></span> <span data-ttu-id="4020e-110">Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="4020e-110">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|<span data-ttu-id="4020e-111">Obtient une valeur qui indique si les deux définitions de chaîne spécifié sont égale.</span><span class="sxs-lookup"><span data-stu-id="4020e-111">Gets a value that indicates whether the two specified string definitions are equal.</span></span> <span data-ttu-id="4020e-112">Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="4020e-112">You can pass the flag value IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::AreTextualReferencesEqual`|<span data-ttu-id="4020e-113">Obtient une valeur qui indique si les deux références de chaîne spécifié sont égaux.</span><span class="sxs-lookup"><span data-stu-id="4020e-113">Gets a value that indicates whether the two specified string references are equal.</span></span> <span data-ttu-id="4020e-114">Vous pouvez passer la valeur d’indicateur IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION pour ignorer leurs informations de version respectives.</span><span class="sxs-lookup"><span data-stu-id="4020e-114">You can pass the flag value IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION to ignore their respective version information.</span></span>|  
|`IAppIdAuthority::CreateDefinition`|<span data-ttu-id="4020e-115">Obtient un pointeur d’interface qui vient d’être généré `IDefinitionAppId` instance qui représente l’assembly dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="4020e-115">Gets an interface pointer to a newly generated `IDefinitionAppId` instance that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::CreateReference`|<span data-ttu-id="4020e-116">Obtient un pointeur d’interface nouvellement créé `IReferenceAppId` qui représente l’assembly dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="4020e-116">Gets an interface pointer to a newly created `IReferenceAppId` that represents the assembly in the current scope.</span></span>|  
|`IAppIdAuthority::DefinitionToText`|<span data-ttu-id="4020e-117">Obtient une version de chaîne spécifié `IDefinitionAppId`, à l’aide des valeurs d’indicateur spécifiées.</span><span class="sxs-lookup"><span data-stu-id="4020e-117">Gets a string version of the specified `IDefinitionAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|<span data-ttu-id="4020e-118">Obtient une valeur qui indique si le texte spécifié `IDefinitionAppId` et `IReferenceAppId` représentent le même assembly.</span><span class="sxs-lookup"><span data-stu-id="4020e-118">Gets a value that indicates whether the specified `IDefinitionAppId` and `IReferenceAppId` represent the same assembly.</span></span>|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|<span data-ttu-id="4020e-119">Obtient une valeur qui indique si la chaîne de définition spécifié et la chaîne de référence représentent le même assembly.</span><span class="sxs-lookup"><span data-stu-id="4020e-119">Gets a value that indicates whether the specified definition string and reference string represent the same assembly.</span></span>|  
|`IAppIdAuthority::GenerateDefinitionKey`|<span data-ttu-id="4020e-120">Obtient une clé de chaîne qui représente l’élément `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="4020e-120">Gets a string key that represents the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::GenerateReferenceKey`|<span data-ttu-id="4020e-121">Obtient une clé de chaîne qui représente l’élément `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="4020e-121">Gets a string key that represents the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::HashDefinition`|<span data-ttu-id="4020e-122">Obtient une clé de hachage spécifié `IDefinitionAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="4020e-122">Gets a hash key for the specified `IDefinitionAppId` instance.</span></span>|  
|`IAppIdAuthority::HashReference`|<span data-ttu-id="4020e-123">Obtient une clé de hachage spécifié `IReferenceAppId` instance.</span><span class="sxs-lookup"><span data-stu-id="4020e-123">Gets a hash key for the specified `IReferenceAppId` instance.</span></span>|  
|`IAppIdAuthority::ReferenceToText`|<span data-ttu-id="4020e-124">Obtient une version de chaîne spécifié `IReferenceAppId`, à l’aide des valeurs d’indicateur spécifiées.</span><span class="sxs-lookup"><span data-stu-id="4020e-124">Gets a string version of the specified `IReferenceAppId`, using the specified flag values.</span></span>|  
|`IAppIdAuthority::TextToDefinition`|<span data-ttu-id="4020e-125">Obtient un pointeur d’interface vers un `IDefinitionAppId` instance qui représente l’assembly référencé par la clé de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4020e-125">Gets an interface pointer to an `IDefinitionAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
|`IAppIdAuthority::TextToReference`|<span data-ttu-id="4020e-126">Obtient un pointeur d’interface vers un `IReferenceAppId` instance qui représente l’assembly référencé par la clé de chaîne spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4020e-126">Gets an interface pointer to an `IReferenceAppId` instance that represents the assembly referenced by the specified string key.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4020e-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4020e-127">Requirements</span></span>  
 <span data-ttu-id="4020e-128">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4020e-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4020e-129">**En-tête :** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="4020e-129">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="4020e-130">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4020e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4020e-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4020e-131">See Also</span></span>  
 [<span data-ttu-id="4020e-132">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="4020e-132">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
