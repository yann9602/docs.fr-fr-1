---
title: "Génération de mon premier service WCF prenant en charge les revendications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0e6d091-9a97-4888-8f2c-cbcee42d90ee
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 791c86b8f833c6b1a8acb6da3b03cfccdafca0e5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="building-my-first-claims-aware-wcf-service"></a><span data-ttu-id="c520e-102">Génération de mon premier service WCF prenant en charge les revendications</span><span class="sxs-lookup"><span data-stu-id="c520e-102">Building My First Claims-Aware WCF Service</span></span>
## <a name="applies-to"></a><span data-ttu-id="c520e-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="c520e-103">Applies To</span></span>  
  
-   <span data-ttu-id="c520e-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="c520e-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="c520e-105">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="c520e-105">Windows Communication Foundation (WCF)</span></span>  
  
## <a name="overview"></a><span data-ttu-id="c520e-106">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c520e-106">Overview</span></span>  
 <span data-ttu-id="c520e-107">Cette rubrique décrit le scénario de création des services WCF qui prennent en charge les revendications à l'aide de WIF.</span><span class="sxs-lookup"><span data-stu-id="c520e-107">This topic outlines the scenario of building claims-aware WCF services using WIF.</span></span> <span data-ttu-id="c520e-108">Il y a généralement trois participants dans un scénario de service Web qui prend en charge les revendications : le service Web lui-même, l'utilisateur final, et le service d'émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="c520e-108">There are usually three participants in a claims-aware web service scenario: the web service itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="c520e-109">L'illustration suivante décrit ce scénario :</span><span class="sxs-lookup"><span data-stu-id="c520e-109">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="c520e-110">![Service WCF prenant en charge les revendications de base avec WIF](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span><span class="sxs-lookup"><span data-stu-id="c520e-110">![WIF Basic Claims Aware WCF Service](../../../docs/framework/security/media/wifbasicclaimsawarewcfservice.gif "WIFBasicClaimsAwareWCFService")</span></span>  
  
1.  <span data-ttu-id="c520e-111">Le client du service WCF (parfois appelé agent) utilise WIF pour envoyer les informations d'identification à STS et une fois l'authentification réussie, un jeton est émis par STS pour l'agent.</span><span class="sxs-lookup"><span data-stu-id="c520e-111">The WCF service client (sometimes called agent) uses WIF to send credentials to the STS and upon successful authentication, the agent is issued a token by the STS.</span></span>  
  
2.  <span data-ttu-id="c520e-112">L'agent envoie ce jeton émis par STS au service WCF.</span><span class="sxs-lookup"><span data-stu-id="c520e-112">The agent sends this STS-issued token to the WCF service.</span></span>  
  
3.  <span data-ttu-id="c520e-113">Le service WCF qui prend en charge les revendications est configuré pour approuver STS et les jetons qu'il émet.</span><span class="sxs-lookup"><span data-stu-id="c520e-113">The claims-aware WCF service is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="c520e-114">Le service WCF qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser.</span><span class="sxs-lookup"><span data-stu-id="c520e-114">The claims-aware WCF service uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="c520e-115">Les développeurs utilisent l’API WIF et les types appropriés, par exemple **ClaimsPrincipal**, pour les besoins de l’application, tels que l’implémentation de l’autorisation pour cette dernière.</span><span class="sxs-lookup"><span data-stu-id="c520e-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="c520e-116">À partir de la version .NET 4.5, WIF fait partie du package .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c520e-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="c520e-117">Le fait d’avoir les classes WIF directement disponibles dans l’infrastructure permet une intégration plus profonde de l’identité basée sur les revendications dans .NET, facilitant ainsi l’utilisation des revendications.</span><span class="sxs-lookup"><span data-stu-id="c520e-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="c520e-118">Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="c520e-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="c520e-119">Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="c520e-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="c520e-120">STS est un service qui émet des jetons en cas de réussite de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="c520e-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="c520e-121">Microsoft propose deux STS standard compatibles :</span><span class="sxs-lookup"><span data-stu-id="c520e-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="c520e-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="c520e-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="c520e-123">[Microsoft Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="c520e-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="c520e-124">AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site.</span><span class="sxs-lookup"><span data-stu-id="c520e-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="c520e-125">Azure Active Directory Access Control (également appelé Service de contrôle d'accès ou ACS) est un service cloud proposé dans le cadre de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c520e-125">Azure Active Directory Access Control (also known as Access Control Service or ACS) is a cloud service, offered as part of Microsoft Azure.</span></span> <span data-ttu-id="c520e-126">À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="c520e-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="c520e-127">Par exemple, vous pouvez utiliser le service STS de développement local qui fait partie de l’outil [Identity and Access Tool pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) disponible gratuitement en ligne.</span><span class="sxs-lookup"><span data-stu-id="c520e-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="c520e-128">Pour générer votre premier service WCF prenant en charge les revendications à l’aide de WIF, consultez [Guide pratique pour générer un service WCF prenant en charge les revendications à l’aide de WIF](http://msdn.microsoft.com/library/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span><span class="sxs-lookup"><span data-stu-id="c520e-128">To build your first claims-aware WCF service using WIF, see [How To: Build Claims-Aware WCF Service Using WIF](http://msdn.microsoft.com/library/431e6415-62ed-4a9f-af03-f14d2b4dfe6d).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c520e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c520e-129">See Also</span></span>  
 [<span data-ttu-id="c520e-130">Prise en main de WIF</span><span class="sxs-lookup"><span data-stu-id="c520e-130">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
