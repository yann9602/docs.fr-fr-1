---
title: "IMetaDataDispenserEx::GetCORSystemDirectory, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="f7c06-102">IMetaDataDispenserEx::GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="f7c06-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="f7c06-103">Obtient le répertoire qui contient le common language runtime (CLR) actuel.</span><span class="sxs-lookup"><span data-stu-id="f7c06-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="f7c06-104">Cette méthode est prise en charge uniquement pour une utilisation par les débogueurs out-of-process.</span><span class="sxs-lookup"><span data-stu-id="f7c06-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="f7c06-105">Si elle est appelée à partir d’un autre composant, elle retournera E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f7c06-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7c06-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7c06-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7c06-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f7c06-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="f7c06-108">[out] La mémoire tampon pour recevoir le nom de répertoire.</span><span class="sxs-lookup"><span data-stu-id="f7c06-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="f7c06-109">[in] La taille, en octets, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f7c06-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="f7c06-110">[out] Le nombre d’octets retournés dans `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="f7c06-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7c06-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f7c06-111">Requirements</span></span>  
 <span data-ttu-id="f7c06-112">**Plateforme :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7c06-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7c06-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f7c06-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f7c06-114">**Bibliothèque :** utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7c06-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f7c06-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7c06-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c06-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7c06-116">See Also</span></span>  
 [<span data-ttu-id="f7c06-117">IMetaDataDispenserEx (Interface)</span><span class="sxs-lookup"><span data-stu-id="f7c06-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="f7c06-118">IMetaDataDispenser (Interface)</span><span class="sxs-lookup"><span data-stu-id="f7c06-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
