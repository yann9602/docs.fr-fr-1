---
title: "CorCheckDuplicatesFor, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorCheckDuplicatesFor
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCheckDuplicatesFor
helpviewer_keywords: CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c5a9376f6d56e2a21ee474e2724ce5eff8f6f63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corcheckduplicatesfor-enumeration"></a><span data-ttu-id="0d608-102">CorCheckDuplicatesFor, énumération</span><span class="sxs-lookup"><span data-stu-id="0d608-102">CorCheckDuplicatesFor Enumeration</span></span>
<span data-ttu-id="0d608-103">Spécifie les jetons de métadonnées qui seront vérifiés pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="0d608-103">Specifies the metadata tokens that will be checked for duplicates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d608-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d608-104">Syntax</span></span>  
  
```  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =   
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |   
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a><span data-ttu-id="0d608-105">Membres</span><span class="sxs-lookup"><span data-stu-id="0d608-105">Members</span></span>  
  
|<span data-ttu-id="0d608-106">Membre</span><span class="sxs-lookup"><span data-stu-id="0d608-106">Member</span></span>|<span data-ttu-id="0d608-107">Description</span><span class="sxs-lookup"><span data-stu-id="0d608-107">Description</span></span>|  
|------------|-----------------|  
|`MDDupAll`|<span data-ttu-id="0d608-108">Vérifiez tous les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="0d608-108">Check all metadata tokens for duplicates.</span></span>|  
|`MDDupENC`|<span data-ttu-id="0d608-109">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="0d608-109">Not used.</span></span>|  
|`MDNoDupChecks`|<span data-ttu-id="0d608-110">N’activez pas les jetons de métadonnées pour les doublons.</span><span class="sxs-lookup"><span data-stu-id="0d608-110">Do not check metadata tokens for duplicates.</span></span>|  
|`MDDupTypeDef`|<span data-ttu-id="0d608-111">Recherche les doublons des `mdTypeDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-111">Check for duplicates of `mdTypeDef` tokens.</span></span>|  
|`MDDupInterfaceImpl`|<span data-ttu-id="0d608-112">Recherche les doublons des `mdInterfaceImpl` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-112">Check for duplicates of `mdInterfaceImpl` tokens.</span></span>|  
|`MDDupMethodDef`|<span data-ttu-id="0d608-113">Recherche les doublons des `mdMethodDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-113">Check for duplicates of `mdMethodDef` tokens.</span></span>|  
|`MDDupTypeRef`|<span data-ttu-id="0d608-114">Recherche les doublons des `mdTypeRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-114">Check for duplicates of `mdTypeRef` tokens.</span></span>|  
|`MDDupMemberRef`|<span data-ttu-id="0d608-115">Recherche les doublons des `mdMemberRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-115">Check for duplicates of `mdMemberRef` tokens.</span></span>|  
|`MDDupCustomAttribute`|<span data-ttu-id="0d608-116">Recherche les doublons des `mdCustomAttribute` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-116">Check for duplicates of `mdCustomAttribute` tokens.</span></span>|  
|`MDDupParamDef`|<span data-ttu-id="0d608-117">Recherche les doublons des `mdParamDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-117">Check for duplicates of `mdParamDef` tokens.</span></span>|  
|`MDDupPermission`|<span data-ttu-id="0d608-118">Recherche les doublons des `mdPermission` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-118">Check for duplicates of `mdPermission` tokens.</span></span>|  
|`MDDupProperty`|<span data-ttu-id="0d608-119">Recherche les doublons des `mdProperty` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-119">Check for duplicates of `mdProperty` tokens.</span></span>|  
|`MDDupEvent`|<span data-ttu-id="0d608-120">Recherche les doublons des `mdEvent` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-120">Check for duplicates of `mdEvent` tokens.</span></span>|  
|`MDDupFieldDef`|<span data-ttu-id="0d608-121">Recherche les doublons des `mdFieldDef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-121">Check for duplicates of `mdFieldDef` tokens.</span></span>|  
|`MDDupSignature`|<span data-ttu-id="0d608-122">Recherche les doublons des `mdSignature` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-122">Check for duplicates of `mdSignature` tokens.</span></span>|  
|`MDDupModuleRef`|<span data-ttu-id="0d608-123">Recherche les doublons des `mdModuleRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-123">Check for duplicates of `mdModuleRef` tokens.</span></span>|  
|`MDDupTypeSpec`|<span data-ttu-id="0d608-124">Recherche les doublons des `mdTypeSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-124">Check for duplicates of `mdTypeSpec` tokens.</span></span>|  
|`MDDupImplMap`|<span data-ttu-id="0d608-125">Recherche les doublons des `mdImplMap` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-125">Check for duplicates of `mdImplMap` tokens.</span></span>|  
|`MDDupAssemblyRef`|<span data-ttu-id="0d608-126">Recherche les doublons des `mdAssemblyRef` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-126">Check for duplicates of `mdAssemblyRef` tokens.</span></span>|  
|`MDDupFile`|<span data-ttu-id="0d608-127">Recherche les doublons des `mdFile` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-127">Check for duplicates of `mdFile` tokens.</span></span>|  
|`MDDupExportedType`|<span data-ttu-id="0d608-128">Recherche les doublons des `mdExportedType` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-128">Check for duplicates of `mdExportedType` tokens.</span></span>|  
|`MDDupManifestResource`|<span data-ttu-id="0d608-129">Recherche les doublons des `mdManifestResource` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-129">Check for duplicates of `mdManifestResource` tokens.</span></span>|  
|`MDDupGenericParam`|<span data-ttu-id="0d608-130">Recherche les doublons des `mdGenericParam` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-130">Check for duplicates of `mdGenericParam` tokens.</span></span>|  
|`MDDupMethodSpec`|<span data-ttu-id="0d608-131">Recherche les doublons des `mdMethodSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-131">Check for duplicates of `mdMethodSpec` tokens.</span></span>|  
|`MDDupGenericParamConstraint`|<span data-ttu-id="0d608-132">Recherche les doublons des `mdGenericParamConstraint` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-132">Check for duplicates of `mdGenericParamConstraint` tokens.</span></span>|  
|`MDDupAssembly`|<span data-ttu-id="0d608-133">Recherche les doublons des `mdAssembly` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-133">Check for duplicates of `mdAssembly` tokens.</span></span>|  
|`MDDupDefault`|<span data-ttu-id="0d608-134">Vérification des doublons de `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, et `mdMethodSpec` jetons.</span><span class="sxs-lookup"><span data-stu-id="0d608-134">Check for duplicates of `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, and `mdMethodSpec` tokens.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d608-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d608-135">Requirements</span></span>  
 <span data-ttu-id="0d608-136">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d608-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d608-137">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0d608-137">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0d608-138">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d608-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d608-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d608-139">See Also</span></span>  
 [<span data-ttu-id="0d608-140">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="0d608-140">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
