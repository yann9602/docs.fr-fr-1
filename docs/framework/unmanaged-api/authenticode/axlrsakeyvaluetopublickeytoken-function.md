---
title: _AxlRSAKeyValueToPublicKeyToken, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4af27a2abf1a0bcf4d79eda389c5f79f0ecb1eef
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="f0a5a-102">_AxlRSAKeyValueToPublicKeyToken, fonction</span><span class="sxs-lookup"><span data-stu-id="f0a5a-102">_AxlRSAKeyValueToPublicKeyToken Function</span></span>
<span data-ttu-id="f0a5a-103">Convertit un modulo et un exposant en un jeton de clé publique de nom fort.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0a5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0a5a-104">Syntax</span></span>  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0a5a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f0a5a-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="f0a5a-106">[in] L’objet blob Modulus codé en base64 (à partir de la \<modulo > élément).</span><span class="sxs-lookup"><span data-stu-id="f0a5a-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="f0a5a-107">Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="f0a5a-108">[in] L’objet blob Exponent codé en base64 (à partir de la \<exposant > élément).</span><span class="sxs-lookup"><span data-stu-id="f0a5a-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="f0a5a-109">Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-109">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="f0a5a-110">[en sortie] Un pointeur vers WCHAR * pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-110">[out] A pointer to WCHAR * to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0a5a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f0a5a-111">Return Value</span></span>  
 <span data-ttu-id="f0a5a-112">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="f0a5a-113">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="f0a5a-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0a5a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0a5a-114">See Also</span></span>  
 [<span data-ttu-id="f0a5a-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="f0a5a-115">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
