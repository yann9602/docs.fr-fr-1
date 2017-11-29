---
title: GetCORRequiredVersion, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORRequiredVersion
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetCORRequiredVersion
helpviewer_keywords: GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 05267819a1c61c55220f477173069ddf51edaeb4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="7eb29-102">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="7eb29-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="7eb29-103">Obtient le numéro de version de runtime (CLR) de langage commun requis.</span><span class="sxs-lookup"><span data-stu-id="7eb29-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="7eb29-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7eb29-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7eb29-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7eb29-105">Syntax</span></span>  
  
```  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7eb29-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7eb29-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="7eb29-107">[out] Une mémoire tampon qui contient une chaîne qui spécifie le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="7eb29-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7eb29-108">[in] La taille, en octets, de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7eb29-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="7eb29-109">[out] Le nombre d’octets retournés dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="7eb29-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7eb29-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7eb29-110">Requirements</span></span>  
 <span data-ttu-id="7eb29-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7eb29-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7eb29-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7eb29-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7eb29-113">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7eb29-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7eb29-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7eb29-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7eb29-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7eb29-115">See Also</span></span>  
 [<span data-ttu-id="7eb29-116">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="7eb29-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
