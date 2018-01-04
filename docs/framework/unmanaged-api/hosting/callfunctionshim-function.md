---
title: CallFunctionShim, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CallFunctionShim
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CallFunctionShim
helpviewer_keywords: CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 12c399c876a244d0c27e34b41e08c284d7429bac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="bb438-102">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="bb438-102">CallFunctionShim Function</span></span>
<span data-ttu-id="bb438-103">Effectue un appel à la fonction qui porte le nom spécifié et les paramètres dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bb438-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="bb438-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb438-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb438-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb438-105">Syntax</span></span>  
  
```  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bb438-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bb438-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="bb438-107">[in] Le nom de la bibliothèque qui contient la fonction.</span><span class="sxs-lookup"><span data-stu-id="bb438-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="bb438-108">[in] Le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="bb438-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="bb438-109">[in] Le premier argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="bb438-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="bb438-110">[in] Le deuxième argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="bb438-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="bb438-111">[in] La version de la bibliothèque qui contient la fonction.</span><span class="sxs-lookup"><span data-stu-id="bb438-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="bb438-112">[in] Réservé à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="bb438-112">[in] Reserved for future use.</span></span> <span data-ttu-id="bb438-113">Passez zéro dans ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="bb438-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb438-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb438-114">Requirements</span></span>  
 <span data-ttu-id="bb438-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb438-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb438-116">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb438-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb438-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb438-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb438-118">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb438-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb438-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb438-119">See Also</span></span>  
 [<span data-ttu-id="bb438-120">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="bb438-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
