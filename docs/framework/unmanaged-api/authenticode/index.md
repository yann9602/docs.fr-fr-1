---
title: "Authenticode (Informations de référence sur les API non managées)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e90a13ebf46f1891061c78435b7ba47d68de001d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="baf70-102">Authenticode (Informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="baf70-102">Authenticode (Unmanaged API Reference)</span></span>
<span data-ttu-id="baf70-103">Prend en charge le module de création et de vérification des licences XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="baf70-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="baf70-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="baf70-104">In This Section</span></span>  
 [<span data-ttu-id="baf70-105">_Axlgetissuerpublickeyhash, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-105">_AxlGetIssuerPublicKeyHash Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="baf70-106">Récupère le hachage SHA-1 de la clé publique associée à la clé privée utilisée pour signer le certificat spécifié.</span><span class="sxs-lookup"><span data-stu-id="baf70-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="baf70-107">_Axlpublickeyblobtopublickeytoken, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="baf70-108">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="baf70-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="baf70-109">_AxlRSAKeyValueToPublicKeyToken, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="baf70-110">Convertit un modulo et un exposant en un jeton de clé publique de nom fort.</span><span class="sxs-lookup"><span data-stu-id="baf70-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="baf70-111">CertFreeAuthenticodeSignerInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-111">CertFreeAuthenticodeSignerInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="baf70-112">Libère les ressources allouées pour la structure AXL_AUTHENTICODE_SIGNER_INFO.</span><span class="sxs-lookup"><span data-stu-id="baf70-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="baf70-113">CertFreeAuthenticodeTimestamperInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="baf70-114">Libère les ressources allouées pour la structure AXL_AUTHENTICODE_TIMESTAMPER_INFO.</span><span class="sxs-lookup"><span data-stu-id="baf70-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="baf70-115">CertTimestampAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-115">CertTimestampAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="baf70-116">Effectue un horodatage d'une licence XrML Authenticode créée par CertCreateAuthenticodeLicense.</span><span class="sxs-lookup"><span data-stu-id="baf70-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="baf70-117">CertVerifyAuthenticodeLicense, fonction</span><span class="sxs-lookup"><span data-stu-id="baf70-117">CertVerifyAuthenticodeLicense Function</span></span>](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="baf70-118">Vérifie la validité d'une licence XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="baf70-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="baf70-119">Axl_authenticode_signer_info, Structure</span><span class="sxs-lookup"><span data-stu-id="baf70-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="baf70-120">Définit les informations du signataire Authenticode.</span><span class="sxs-lookup"><span data-stu-id="baf70-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="baf70-121">Axl_authenticode_timestamper_info, Structure</span><span class="sxs-lookup"><span data-stu-id="baf70-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="baf70-122">Définit les informations de l'horodateur Authenticode.</span><span class="sxs-lookup"><span data-stu-id="baf70-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="baf70-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baf70-123">See Also</span></span>  
 [<span data-ttu-id="baf70-124">Informations de référence sur les API non managées</span><span class="sxs-lookup"><span data-stu-id="baf70-124">Unmanaged API Reference</span></span>](../../../../docs/framework/unmanaged-api/index.md)
