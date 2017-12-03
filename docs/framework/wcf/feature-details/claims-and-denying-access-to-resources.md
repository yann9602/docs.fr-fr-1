---
title: "Revendications et refus de l'accès aux ressources"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 00d6a797b8099313c15d075457ee757c1f22f744
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="fc2b8-102">Revendications et refus de l'accès aux ressources</span><span class="sxs-lookup"><span data-stu-id="fc2b8-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fc2b8-103"> prend en charge un mécanisme d'autorisation basé sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="fc2b8-104">Tout en permettant l'accès aux ressources en fonction de la présence de certaines revendications, les systèmes refusent souvent cet accès en fonction de la présence d'autres revendications.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="fc2b8-105">Les systèmes de ce type doivent rechercher dans <xref:System.IdentityModel.Policy.AuthorizationContext> les revendications qui donnent lieu à un refus d'accès avant de rechercher celles donnant lieu à une autorisation d'accès.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="fc2b8-106">Par exemple, un système peut refuser l'accès à une ressource à toute personne qui dispose d'une revendication de type `Age`, d'un droit <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> et d'une valeur de ressource `Under 21` uniquement si cette identité a également une revendication de type `Name`, un droit <xref:System.IdentityModel.Claims.Rights.Identity%2A> et une valeur de ressource `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="fc2b8-107">En d'autres termes, le système refuse l'accès à toute personne de moins de 21 ans et accorde l'accès si le nom est Mallory.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="fc2b8-108">Pour implémenter correctement cette sémantique, il est important de rechercher dans un premier temps la revendication `Age` et de déterminer si l'âge de la personne se situe au-dessous de 21 ans.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="fc2b8-109">Sinon, si Mallory à moins de 21 ans, alors l'accès à la ressource pourra être accordé uniquement sur la base de la revendication `Name`.</span><span class="sxs-lookup"><span data-stu-id="fc2b8-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2b8-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc2b8-110">See Also</span></span>  
 [<span data-ttu-id="fc2b8-111">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="fc2b8-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="fc2b8-112">Revendications et jetons</span><span class="sxs-lookup"><span data-stu-id="fc2b8-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
