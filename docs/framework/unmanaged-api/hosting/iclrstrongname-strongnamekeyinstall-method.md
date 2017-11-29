---
title: "Méthode ICLRStrongName::StrongNameKeyInstall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameKeyInstall
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 241421761b87bf9f3baf7315c2ac8e9ebd499486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="1188f-102">Méthode ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="1188f-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="1188f-103">Importe une paire de clés publique/privée dans un conteneur.</span><span class="sxs-lookup"><span data-stu-id="1188f-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1188f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1188f-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1188f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1188f-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="1188f-106">[in] Le nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1188f-106">[in] The name of the key container.</span></span> <span data-ttu-id="1188f-107">`wszKeyContainer`doit être une chaîne non vide.</span><span class="sxs-lookup"><span data-stu-id="1188f-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1188f-108">[in] La paire de clés binaire.</span><span class="sxs-lookup"><span data-stu-id="1188f-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1188f-109">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="1188f-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1188f-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1188f-110">Return Value</span></span>  
 <span data-ttu-id="1188f-111">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="1188f-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1188f-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="1188f-112">Remarks</span></span>  
 <span data-ttu-id="1188f-113">Utilisez le [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) méthode pour supprimer le conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="1188f-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1188f-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1188f-114">Requirements</span></span>  
 <span data-ttu-id="1188f-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1188f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1188f-116">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="1188f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1188f-117">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1188f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1188f-118">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1188f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1188f-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1188f-119">See Also</span></span>  
 [<span data-ttu-id="1188f-120">StrongNameKeyDelete (méthode)</span><span class="sxs-lookup"><span data-stu-id="1188f-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="1188f-121">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="1188f-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
