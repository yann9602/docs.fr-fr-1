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
ms.workload: dotnet
ms.openlocfilehash: e8dc31877ba3550fa8faf610b831dfd2e7b313ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="b1caf-102">IMetaDataImport2::GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="b1caf-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="b1caf-103">Obtient une valeur identifiant la nature du code dans le fichier exécutable portable (PE) fichier, en général un fichier DLL ou EXE, qui est défini dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="b1caf-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1caf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1caf-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b1caf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1caf-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="b1caf-106">[out] Un pointeur vers une valeur de la [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) énumération qui décrit le fichier PE.</span><span class="sxs-lookup"><span data-stu-id="b1caf-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="b1caf-107">[out] Pointeur vers une valeur qui identifie l’architecture de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b1caf-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="b1caf-108">Consultez la section suivante pour les valeurs possibles.</span><span class="sxs-lookup"><span data-stu-id="b1caf-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1caf-109">Notes</span><span class="sxs-lookup"><span data-stu-id="b1caf-109">Remarks</span></span>  
 <span data-ttu-id="b1caf-110">La valeur référencée par la `pdwMachine` paramètre peut être une des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="b1caf-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="b1caf-111">Value</span><span class="sxs-lookup"><span data-stu-id="b1caf-111">Value</span></span>|<span data-ttu-id="b1caf-112">Architecture de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="b1caf-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="b1caf-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="b1caf-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="b1caf-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="b1caf-114">0x014C</span></span>|<span data-ttu-id="b1caf-115">x86</span><span class="sxs-lookup"><span data-stu-id="b1caf-115">x86</span></span>|  
|<span data-ttu-id="b1caf-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="b1caf-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="b1caf-117">0 x 0200</span><span class="sxs-lookup"><span data-stu-id="b1caf-117">0x0200</span></span>|<span data-ttu-id="b1caf-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="b1caf-118">Intel IPF</span></span>|  
|<span data-ttu-id="b1caf-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="b1caf-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="b1caf-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="b1caf-120">0x8664</span></span>|<span data-ttu-id="b1caf-121">X64</span><span class="sxs-lookup"><span data-stu-id="b1caf-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1caf-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b1caf-122">Requirements</span></span>  
 <span data-ttu-id="b1caf-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1caf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1caf-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b1caf-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1caf-125">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1caf-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1caf-126">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1caf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1caf-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1caf-127">See Also</span></span>  
 [<span data-ttu-id="b1caf-128">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b1caf-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="b1caf-129">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b1caf-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b1caf-130">CorPEKind, énumération</span><span class="sxs-lookup"><span data-stu-id="b1caf-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
