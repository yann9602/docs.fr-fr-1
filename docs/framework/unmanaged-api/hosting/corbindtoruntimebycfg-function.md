---
title: CorBindToRuntimeByCfg, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dccd777ef20f68d091cfdd7939c57a1f8d42ad5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="1fb9a-102">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="1fb9a-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="1fb9a-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version qui sont lu à partir d’un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="1fb9a-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1fb9a-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb9a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fb9a-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1fb9a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1fb9a-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="1fb9a-107">[in] Un pointeur vers un `IStream` objet qui lit le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="1fb9a-108">[in] Réservé à un usage ultérieur.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-108">[in] Reserved for future use.</span></span> <span data-ttu-id="1fb9a-109">Utilisez 0 (zéro) comme valeur.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="1fb9a-110">[in] Une valeur de la [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) énumération qui spécifie le comportement de démarrage du CLR.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="1fb9a-111">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="1fb9a-112">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="1fb9a-113">[in] Le `IID` d’un le `ICorRuntimeHost` ou `ICLRRuntimeHost` interface.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="1fb9a-114">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="1fb9a-115">[out] Pointeur vers l’adresse de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fb9a-116">Notes</span><span class="sxs-lookup"><span data-stu-id="1fb9a-116">Remarks</span></span>  
 <span data-ttu-id="1fb9a-117">Le format du fichier XML est modélisé d’après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="1fb9a-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="1fb9a-118">Pour plus d’informations sur les fichiers XML, consultez [schéma de fichier de Configuration](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="1fb9a-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fb9a-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1fb9a-119">Requirements</span></span>  
 <span data-ttu-id="1fb9a-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fb9a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb9a-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1fb9a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1fb9a-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1fb9a-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1fb9a-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb9a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb9a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fb9a-124">See Also</span></span>  
 [<span data-ttu-id="1fb9a-125">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="1fb9a-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="1fb9a-126">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="1fb9a-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="1fb9a-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="1fb9a-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="1fb9a-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="1fb9a-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="1fb9a-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="1fb9a-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="1fb9a-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="1fb9a-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
