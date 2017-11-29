---
title: CertTimestampAuthenticodeLicense, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CertTimestampAuthenticodeLicense
api_location: clr.dll
api_type: DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 42ec863e9accbd2156b6eeed5857ff86075cf0a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="certtimestampauthenticodelicense-function"></a><span data-ttu-id="ab14d-102">CertTimestampAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="ab14d-102">CertTimestampAuthenticodeLicense Function</span></span>
<span data-ttu-id="ab14d-103">Horodate une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="ab14d-103">Time-stamps an Authenticode XrML license.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab14d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab14d-104">Syntax</span></span>  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab14d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab14d-105">Parameters</span></span>  
 `pSignedLicenseBlob`  
 <span data-ttu-id="ab14d-106">[en entrée] La licence XrML Authenticode signée à horodater.</span><span class="sxs-lookup"><span data-stu-id="ab14d-106">[in] The signed Authenticode XrML license to be time-stamped.</span></span> <span data-ttu-id="ab14d-107">Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="ab14d-107">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
 `pwszTimestampURI`  
 <span data-ttu-id="ab14d-108">[en entrée] L'URI du server d'horodatage.</span><span class="sxs-lookup"><span data-stu-id="ab14d-108">[in] The time-stamp server's URI.</span></span>  
  
 `pTimestampSignatureBlob`  
 <span data-ttu-id="ab14d-109">[en sortie] Un pointeur vers CRYPT_DATA_BLOB pour recevoir la signature de l'horodatage codé en base64.</span><span class="sxs-lookup"><span data-stu-id="ab14d-109">[out] A pointer to CRYPT_DATA_BLOB to receive the base64-encoded time-stamp signature.</span></span> <span data-ttu-id="ab14d-110">Il incombe l’appelant de libérer `pTimestampSignatureBlob` -> `pbData` avec `HepFree()` après utilisation.</span><span class="sxs-lookup"><span data-stu-id="ab14d-110">It is the caller's responsibility to free `pTimestampSignatureBlob`->`pbData` with `HepFree()` after use.</span></span> <span data-ttu-id="ab14d-111">Consultez le [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span><span class="sxs-lookup"><span data-stu-id="ab14d-111">See the [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab14d-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="ab14d-112">Remarks</span></span>  
 <span data-ttu-id="ab14d-113">La signature de l'horodatage est en réalité un message PKCS #7 SignedData dont le contenu est la forme binaire de la valeur de SignatureValue de la signature de la licence.</span><span class="sxs-lookup"><span data-stu-id="ab14d-113">The time-stamp signature is actually a PKCS #7 SignedData message whose content is the binary form of the SignatureValue from the license's signature.</span></span> <span data-ttu-id="ab14d-114">Ceci agit comme une contre-signature de la licence.</span><span class="sxs-lookup"><span data-stu-id="ab14d-114">Basically, this acts as a counter-signature of the license.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab14d-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab14d-115">Return Value</span></span>  
 <span data-ttu-id="ab14d-116">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="ab14d-116">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="ab14d-117">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="ab14d-117">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab14d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab14d-118">See Also</span></span>  
 [<span data-ttu-id="ab14d-119">Authenticode</span><span class="sxs-lookup"><span data-stu-id="ab14d-119">Authenticode</span></span>](../../../../docs/framework/unmanaged-api/authenticode/index.md)
