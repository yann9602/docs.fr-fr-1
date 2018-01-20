---
title: CorBindToCurrentRuntime, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: HeaderDef
f1_keywords: CorBindToCurrentRuntime
helpviewer_keywords: CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fed8829f8f14833724d1770273ff905d6f5eabf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="7baaf-102">CorBindToCurrentRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="7baaf-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="7baaf-103">Charge le common language runtime (CLR) dans un processus à l’aide des informations de version stockées dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7baaf-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="7baaf-104">Le format du fichier XML est modélisé d’après le fichier de configuration d’application standard.</span><span class="sxs-lookup"><span data-stu-id="7baaf-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="7baaf-105">Pour plus d’informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="7baaf-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="7baaf-106">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7baaf-106">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="7baaf-107">Consultez [chargement le Common Language Runtime dans un processus](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span><span class="sxs-lookup"><span data-stu-id="7baaf-107">See [Loading the Common Language Runtime into a Process](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7baaf-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7baaf-108">Syntax</span></span>  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7baaf-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7baaf-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="7baaf-110">[in] Le nom d’un fichier de configuration qui spécifie la version du CLR à charger.</span><span class="sxs-lookup"><span data-stu-id="7baaf-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="7baaf-111">Si le nom de fichier n’est pas pleinement qualifié, il est supposé pour être dans le même répertoire que l’exécutable qui effectue l’appel.</span><span class="sxs-lookup"><span data-stu-id="7baaf-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="7baaf-112">La version du runtime à charger est décrite par l’attribut de version dans le [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="7baaf-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="7baaf-113">Si aucune version n’est spécifiée, ou si le `<requiredRuntime>` élément ne peut pas être trouvé, la dernière version du CLR qui est installé sur l’ordinateur est chargée.</span><span class="sxs-lookup"><span data-stu-id="7baaf-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="7baaf-114">[in] Le `CLSID` de la coclasse qui implémente le [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou le [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7baaf-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="7baaf-115">Valeurs prises en charge sont CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="7baaf-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="7baaf-116">[in] Le `IID` de l’interface demandée.</span><span class="sxs-lookup"><span data-stu-id="7baaf-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="7baaf-117">Valeurs prises en charge sont IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="7baaf-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="7baaf-118">[out] Pointeur d’interface retourné.</span><span class="sxs-lookup"><span data-stu-id="7baaf-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7baaf-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7baaf-119">Requirements</span></span>  
 <span data-ttu-id="7baaf-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7baaf-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7baaf-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7baaf-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7baaf-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7baaf-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7baaf-123">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7baaf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7baaf-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7baaf-124">See Also</span></span>  
 [<span data-ttu-id="7baaf-125">CorBindToRuntime, fonction</span><span class="sxs-lookup"><span data-stu-id="7baaf-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="7baaf-126">CorBindToRuntimeByCfg, fonction</span><span class="sxs-lookup"><span data-stu-id="7baaf-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [<span data-ttu-id="7baaf-127">CorBindToRuntimeEx, fonction</span><span class="sxs-lookup"><span data-stu-id="7baaf-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="7baaf-128">CorBindToRuntimeHost, fonction</span><span class="sxs-lookup"><span data-stu-id="7baaf-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="7baaf-129">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="7baaf-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="7baaf-130">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="7baaf-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
