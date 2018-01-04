---
title: "Méthode ICLRStrongName::StrongNameKeyDelete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyDelete
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b3a1d742ac2ad74d327afe4dce097d0f11e5cfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="a6363-102">Méthode ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="a6363-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="a6363-103">Supprime le conteneur de clé spécifié.</span><span class="sxs-lookup"><span data-stu-id="a6363-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6363-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6363-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6363-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a6363-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="a6363-106">[in] Le nom du conteneur de clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="a6363-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6363-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a6363-107">Return Value</span></span>  
 <span data-ttu-id="a6363-108">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="a6363-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6363-109">Notes</span><span class="sxs-lookup"><span data-stu-id="a6363-109">Remarks</span></span>  
 <span data-ttu-id="a6363-110">Utilisez le [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) méthode d’importation d’une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="a6363-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6363-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a6363-111">Requirements</span></span>  
 <span data-ttu-id="a6363-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6363-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6363-113">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a6363-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a6363-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a6363-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6363-115">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6363-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6363-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6363-116">See Also</span></span>  
 [<span data-ttu-id="a6363-117">StrongNameKeyInstall, méthode</span><span class="sxs-lookup"><span data-stu-id="a6363-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="a6363-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a6363-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
