---
title: "CorTokenType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorTokenType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorTokenType
helpviewer_keywords: CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1910321942ebac26d8c377f9d156cdf97bd34b62
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="78b57-102">CorTokenType, énumération</span><span class="sxs-lookup"><span data-stu-id="78b57-102">CorTokenType Enumeration</span></span>
<span data-ttu-id="78b57-103">Indique le type de jeton de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="78b57-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b57-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78b57-104">Syntax</span></span>  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="78b57-105">Membres</span><span class="sxs-lookup"><span data-stu-id="78b57-105">Members</span></span>  
  
|<span data-ttu-id="78b57-106">Membre</span><span class="sxs-lookup"><span data-stu-id="78b57-106">Member</span></span>|<span data-ttu-id="78b57-107">Description</span><span class="sxs-lookup"><span data-stu-id="78b57-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="78b57-108">Un `mdModule` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="78b57-109">Un `mdTypeRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="78b57-110">Un `mdTypeDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="78b57-111">Un `mdFieldDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="78b57-112">Un `mdMethodDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="78b57-113">Un `mdParamDef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="78b57-114">Un `mdInterfaceImpl` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="78b57-115">Un `mdMemberRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="78b57-116">Un `mdCustomAttribute` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="78b57-117">Un `mdPermission` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="78b57-118">Un `mdSignature` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="78b57-119">Un `mdEvent` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="78b57-120">Un `mdProperty` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="78b57-121">Un `mdModuleRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="78b57-122">Un `mdTypeSpec` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="78b57-123">Un `mdAssembly` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="78b57-124">Un `mdAssemblyRef` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="78b57-125">Un `mdFile` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="78b57-126">Un `mdExportedType` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="78b57-127">Un `mdManifestResource` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="78b57-128">Un `mdGenericParam` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="78b57-129">Un `mdMethodSpec` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="78b57-130">Un `mdGenericParamConstraint` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="78b57-131">Un `mdString` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="78b57-132">Un `mdName` jeton.</span><span class="sxs-lookup"><span data-stu-id="78b57-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="78b57-133">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="78b57-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78b57-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="78b57-134">Remarks</span></span>  
 <span data-ttu-id="78b57-135">Chaque valeur est égale à la valeur de l’octet dans le jeton de métadonnées correspondant.</span><span class="sxs-lookup"><span data-stu-id="78b57-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78b57-136">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78b57-136">Requirements</span></span>  
 <span data-ttu-id="78b57-137">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78b57-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78b57-138">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="78b57-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="78b57-139">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78b57-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78b57-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78b57-140">See Also</span></span>  
 [<span data-ttu-id="78b57-141">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="78b57-141">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
