---
title: "Méthode ICLRStrongName::StrongNameGetBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d4ae90367cb84c97d5964ceb815943249af7b240
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="04f02-102">Méthode ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="04f02-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="04f02-103">Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="04f02-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04f02-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04f02-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04f02-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="04f02-106">[in] Un chemin d’accès valide au fichier exécutable à charger.</span><span class="sxs-lookup"><span data-stu-id="04f02-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="04f02-107">[in] La mémoire tampon dans laquelle charger le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="04f02-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="04f02-108">[dans, out] La taille maximale, en octets, demandée `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="04f02-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="04f02-109">Au retour, la taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="04f02-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04f02-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="04f02-110">Return Value</span></span>  
 <span data-ttu-id="04f02-111">`S_OK`Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (voir [valeurs HRESULT courantes](http://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="04f02-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04f02-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="04f02-112">Requirements</span></span>  
 <span data-ttu-id="04f02-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f02-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f02-114">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="04f02-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="04f02-115">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04f02-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04f02-116">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f02-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f02-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04f02-117">See Also</span></span>  
 [<span data-ttu-id="04f02-118">StrongNameGetBlobFromImage (méthode)</span><span class="sxs-lookup"><span data-stu-id="04f02-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="04f02-119">ICLRStrongName Interface</span><span class="sxs-lookup"><span data-stu-id="04f02-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
