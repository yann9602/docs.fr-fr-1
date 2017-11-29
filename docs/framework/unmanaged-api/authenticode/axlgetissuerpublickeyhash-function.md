---
title: _AxlGetIssuerPublicKeyHash, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlGetIssuerPublicKeyHash
api_location: clr.dll
api_type: DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 38be1f621425797e27fc41cb3192a628ebbfdb0c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a><span data-ttu-id="7443e-102">_AxlGetIssuerPublicKeyHash, fonction</span><span class="sxs-lookup"><span data-stu-id="7443e-102">_AxlGetIssuerPublicKeyHash Function</span></span>
<span data-ttu-id="7443e-103">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="7443e-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7443e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7443e-104">Syntax</span></span>  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7443e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7443e-105">Parameters</span></span>  
 `pChainContext`  
 <span data-ttu-id="7443e-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="7443e-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="7443e-107">Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="7443e-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="7443e-108">[en sortie] Un pointeur vers WCHAR * pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="7443e-108">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7443e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7443e-109">Return Value</span></span>  
 <span data-ttu-id="7443e-110">`S_OK` si la fonction réussit, sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="7443e-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7443e-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7443e-111">See Also</span></span>  
 [<span data-ttu-id="7443e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="7443e-112">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
