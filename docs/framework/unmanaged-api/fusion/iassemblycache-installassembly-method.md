---
title: "IAssemblyCache::InstallAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.InstallAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1207c2dc5b29b8de084ccb9145e886f34e8144b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="fccff-102">IAssemblyCache::InstallAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="fccff-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="fccff-103">Installe l’assembly spécifié dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="fccff-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fccff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fccff-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fccff-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fccff-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="fccff-106">[in] Indicateurs définis dans Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="fccff-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="fccff-107">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="fccff-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="fccff-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0 X 00000001)</span><span class="sxs-lookup"><span data-stu-id="fccff-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="fccff-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0 X 00000002)</span><span class="sxs-lookup"><span data-stu-id="fccff-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="fccff-110">[in] Le chemin d’accès au manifeste de l’assembly à installer.</span><span class="sxs-lookup"><span data-stu-id="fccff-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="fccff-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure qui contient les données pour l’installation.</span><span class="sxs-lookup"><span data-stu-id="fccff-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fccff-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fccff-112">Requirements</span></span>  
 <span data-ttu-id="fccff-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fccff-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fccff-114">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="fccff-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="fccff-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fccff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fccff-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fccff-116">See Also</span></span>  
 [<span data-ttu-id="fccff-117">IAssemblyCache (Interface)</span><span class="sxs-lookup"><span data-stu-id="fccff-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
