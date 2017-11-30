---
title: "Création de revendications et valeurs de ressource"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a553a33f4747e2e5ed51f675a8db2d90da65fb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="8b686-102">Création de revendications et valeurs de ressource</span><span class="sxs-lookup"><span data-stu-id="8b686-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="8b686-103">La classe <xref:System.IdentityModel.Claims.Claim> fournit plusieurs méthodes de création d'instances de types de revendications intégrés.</span><span class="sxs-lookup"><span data-stu-id="8b686-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="8b686-104">Parmi ces méthodes, les suivantes n'effectuent pas de vérification de format ou de sémantique sur la ressource fournie :</span><span class="sxs-lookup"><span data-stu-id="8b686-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="8b686-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (ne vérifie pas la longueur ou contenu du tableau d'octets)</span><span class="sxs-lookup"><span data-stu-id="8b686-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="8b686-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (ne vérifie pas la longueur ou contenu du tableau d'octets)</span><span class="sxs-lookup"><span data-stu-id="8b686-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="8b686-107">Lorsque vous appelez les méthodes ci-dessus, vous devez vous assurer que les valeurs de ressource passées sont au format approprié ou qu'elles contiennent le type d'informations correct (ou les deux).</span><span class="sxs-lookup"><span data-stu-id="8b686-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="8b686-108">Les méthodes suivantes prennent des types spécifiques :</span><span class="sxs-lookup"><span data-stu-id="8b686-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="8b686-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b686-109">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="8b686-110">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="8b686-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
