---
title: "IMetaDataImport2::GetPEKind, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fc963f38a845db67bb5b5d377ecabf9a40c359f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="cf4d0-102">IMetaDataImport2::GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="cf4d0-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="cf4d0-103">Obtient une valeur identifiant la nature du code dans le fichier exécutable portable (PE) fichier, en général un fichier DLL ou EXE, qui est défini dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf4d0-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf4d0-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf4d0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf4d0-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="cf4d0-106">[out] Un pointeur vers une valeur de la [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) énumération qui décrit le fichier PE.</span><span class="sxs-lookup"><span data-stu-id="cf4d0-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="cf4d0-107">[out] Pointeur vers une valeur qui identifie l’architecture de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cf4d0-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="cf4d0-108">Consultez la section suivante pour les valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="cf4d0-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf4d0-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="cf4d0-109">Remarks</span></span>  
 <span data-ttu-id="cf4d0-110">La valeur référencée par la `pdwMachine` paramètre peut être une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="cf4d0-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="cf4d0-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="cf4d0-111">Value</span></span>|<span data-ttu-id="cf4d0-112">Architecture de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="cf4d0-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="cf4d0-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="cf4d0-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="cf4d0-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="cf4d0-114">0x014C</span></span>|<span data-ttu-id="cf4d0-115">x86</span><span class="sxs-lookup"><span data-stu-id="cf4d0-115">x86</span></span>|  
|<span data-ttu-id="cf4d0-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="cf4d0-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="cf4d0-117">0 x 0200</span><span class="sxs-lookup"><span data-stu-id="cf4d0-117">0x0200</span></span>|<span data-ttu-id="cf4d0-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="cf4d0-118">Intel IPF</span></span>|  
|<span data-ttu-id="cf4d0-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="cf4d0-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="cf4d0-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="cf4d0-120">0x8664</span></span>|<span data-ttu-id="cf4d0-121">x64</span><span class="sxs-lookup"><span data-stu-id="cf4d0-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf4d0-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf4d0-122">Requirements</span></span>  
 <span data-ttu-id="cf4d0-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf4d0-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4d0-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cf4d0-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cf4d0-125">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cf4d0-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf4d0-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4d0-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4d0-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf4d0-127">See Also</span></span>  
 [<span data-ttu-id="cf4d0-128">IMetaDataImport2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4d0-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="cf4d0-129">IMetaDataImport (Interface)</span><span class="sxs-lookup"><span data-stu-id="cf4d0-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="cf4d0-130">CorPEKind (énumération)</span><span class="sxs-lookup"><span data-stu-id="cf4d0-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
