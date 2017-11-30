---
title: GetCLRIdentityManager, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCLRIdentityManager
api_location: mscoree.dll
api_type: COM
f1_keywords: GetCLRIdentityManager
helpviewer_keywords: GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ddc0395b6fd659ecd6a26a3132fccc65bbb961fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="getclridentitymanager-function"></a><span data-ttu-id="81b38-102">GetCLRIdentityManager, fonction</span><span class="sxs-lookup"><span data-stu-id="81b38-102">GetCLRIdentityManager Function</span></span>
<span data-ttu-id="81b38-103">Obtient un pointeur vers une interface qui permet le common language runtime (CLR) pour gérer les identités.</span><span class="sxs-lookup"><span data-stu-id="81b38-103">Gets a pointer to an interface that allows the common language runtime (CLR) to manage identities.</span></span>  
  
 <span data-ttu-id="81b38-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="81b38-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b38-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81b38-105">Syntax</span></span>  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81b38-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81b38-106">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="81b38-107">[in] A `REFIID` (un identificateur d’interface) qui spécifie l’interface à obtenir.</span><span class="sxs-lookup"><span data-stu-id="81b38-107">[in] A `REFIID` (an interface identifier) that specifies which interface to get.</span></span> <span data-ttu-id="81b38-108">Cette valeur doit être IID_ICLRAssemblyIdentityManager ou IID_ICLRHostBindingPolicyManager.</span><span class="sxs-lookup"><span data-stu-id="81b38-108">This value must be either IID_ICLRAssemblyIdentityManager or IID_ICLRHostBindingPolicyManager.</span></span>  
  
 `ppManager`  
 <span data-ttu-id="81b38-109">[out] Un pointeur vers l’adresse un [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) ou [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="81b38-109">[out] A pointer to the address of either an [ICLRAssemblyIdentityManager](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) or an [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81b38-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="81b38-110">Remarks</span></span>  
 <span data-ttu-id="81b38-111">Appelez le [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) fonction permettant d’obtenir un pointeur vers le `GetCLRIdentityManager` (fonction).</span><span class="sxs-lookup"><span data-stu-id="81b38-111">Call the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function to get a pointer to the `GetCLRIdentityManager` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81b38-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="81b38-112">Requirements</span></span>  
 <span data-ttu-id="81b38-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81b38-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81b38-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="81b38-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="81b38-115">**Bibliothèque :** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="81b38-115">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="81b38-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81b38-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b38-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81b38-117">See Also</span></span>  
 [<span data-ttu-id="81b38-118">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="81b38-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
