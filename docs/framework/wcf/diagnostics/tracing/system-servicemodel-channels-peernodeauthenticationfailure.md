---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffca9a587bdb32afc252f9719eb35e3139dd3f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="596e3-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="596e3-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="596e3-103">Une négociation de sécurité avec un voisin potentiel n'a pas réussi.</span><span class="sxs-lookup"><span data-stu-id="596e3-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="596e3-104">Description</span><span class="sxs-lookup"><span data-stu-id="596e3-104">Description</span></span>  
 <span data-ttu-id="596e3-105">Cette trace se produit lors de la tentative d'établissement d'une connexion de voisin sécurisée.</span><span class="sxs-lookup"><span data-stu-id="596e3-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="596e3-106">Cela peut arriver lorsque les informations d'identification sont incomplètes ou incorrectes.</span><span class="sxs-lookup"><span data-stu-id="596e3-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="596e3-107">PeerChannel reconnaît un seul type de jeton pour les certificats d'identification X.509 puissants qui fournissent un modèle d'identité performant basé sur le type d'authentification et d'autorisation qui peut être implémenté.</span><span class="sxs-lookup"><span data-stu-id="596e3-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="596e3-108">PeerChannel prend également en charge les applications simples via l'utilisation de mots de passe.</span><span class="sxs-lookup"><span data-stu-id="596e3-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="596e3-109">Les mots de passe peuvent uniquement être utilisés pour autoriser l'entrée à la session, mais ne peuvent pas l'être pour effectuer l'authentification des messages.</span><span class="sxs-lookup"><span data-stu-id="596e3-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="596e3-110">Cela et dû au fait qu'un jeton symétrique partagé par un groupe d'homologues est difficile à utiliser et s'avère inapproprié pour l'authentification de la source.</span><span class="sxs-lookup"><span data-stu-id="596e3-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="596e3-111">Résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="596e3-111">Troubleshooting</span></span>  
 <span data-ttu-id="596e3-112">Vérifiez que tous les voisins ont les informations d'identification de sécurité appropriées.</span><span class="sxs-lookup"><span data-stu-id="596e3-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="596e3-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="596e3-113">See Also</span></span>  
 [<span data-ttu-id="596e3-114">Sécurité de canal homologue</span><span class="sxs-lookup"><span data-stu-id="596e3-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="596e3-115">Suivi</span><span class="sxs-lookup"><span data-stu-id="596e3-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="596e3-116">Utilisation du suivi pour résoudre les problèmes posés par votre application</span><span class="sxs-lookup"><span data-stu-id="596e3-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="596e3-117">Administration et diagnostics</span><span class="sxs-lookup"><span data-stu-id="596e3-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
