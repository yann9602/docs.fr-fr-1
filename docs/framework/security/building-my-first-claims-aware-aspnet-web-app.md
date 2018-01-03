---
title: "Création de ma première application web ASP.NET prenant en charge les revendications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 182f7c1646e112026852efcb5bb110607fe19360
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="4a821-102">Création de ma première application web ASP.NET prenant en charge les revendications</span><span class="sxs-lookup"><span data-stu-id="4a821-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="4a821-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="4a821-103">Applies To</span></span>  
  
-   <span data-ttu-id="4a821-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="4a821-104">Windows Identity Foundation (WIF)</span></span>  
  
-   <span data-ttu-id="4a821-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4a821-105">ASP.NET</span></span>  
  
 <span data-ttu-id="4a821-106">Cette rubrique décrit le scénario de création des applications Web qui prennent en charge les revendications ASP.NET à l'aide de WIF.</span><span class="sxs-lookup"><span data-stu-id="4a821-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="4a821-107">Il y a généralement trois participants dans un scénario d'application qui prend en charge les revendications : l'application elle-même, l'utilisateur final et le service d'émission de jeton de sécurité (STS).</span><span class="sxs-lookup"><span data-stu-id="4a821-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="4a821-108">L'illustration suivante décrit ce scénario :</span><span class="sxs-lookup"><span data-stu-id="4a821-108">The following figure describes this scenario:</span></span>  
  
 <span data-ttu-id="4a821-109">![Application web basique WIF](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span><span class="sxs-lookup"><span data-stu-id="4a821-109">![WIF Basic Web App](../../../docs/framework/security/media/wifbasicwebapp.gif "WIFBasicWebApp")</span></span>  
  
1.  <span data-ttu-id="4a821-110">L'application prenant en charge les revendications utilise WIF pour identifier des demandes non authentifiées et pour les rediriger vers STS.</span><span class="sxs-lookup"><span data-stu-id="4a821-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2.  <span data-ttu-id="4a821-111">L'utilisateur final fournit les informations d'identification à STS et une fois qu'il est authentifié, un jeton est émis par STS pour l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4a821-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3.  <span data-ttu-id="4a821-112">L'utilisateur est redirigé à partir de STS vers l'application prenant en charge les revendications avec le jeton publié par STS dans la demande.</span><span class="sxs-lookup"><span data-stu-id="4a821-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4.  <span data-ttu-id="4a821-113">L'application qui prend en charge les revendications est configurée pour approuver STS et les jetons qu'il émet.</span><span class="sxs-lookup"><span data-stu-id="4a821-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="4a821-114">L'application qui prend en charge les revendications utilise WIF pour valider le jeton et l'analyser.</span><span class="sxs-lookup"><span data-stu-id="4a821-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="4a821-115">Les développeurs utilisent l’API WIF et les types appropriés (par exemple **ClaimsPrincpal**) pour les besoins de l’application, tels que l’implémentation de l’autorisation pour cette dernière.</span><span class="sxs-lookup"><span data-stu-id="4a821-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincpal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="4a821-116">À partir de la version .NET 4.5, WIF fait partie du package .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4a821-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="4a821-117">Le fait d’avoir les classes WIF directement disponibles dans l’infrastructure permet une intégration plus profonde de l’identité basée sur les revendications dans .NET, facilitant ainsi l’utilisation des revendications.</span><span class="sxs-lookup"><span data-stu-id="4a821-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="4a821-118">Avec WIF 4.5, vous n'avez pas besoin d'installer de composant hors plage pour démarrer le développement d'applications Web qui prennent en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="4a821-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="4a821-119">Les classes WIF sont maintenant réparties sur plusieurs assemblys, les principaux étant System.Security.Claims, System.IdentityModel et System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="4a821-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="4a821-120">STS est un service qui émet des jetons en cas de réussite de l'authentification.</span><span class="sxs-lookup"><span data-stu-id="4a821-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="4a821-121">Microsoft propose deux STS standard compatibles :</span><span class="sxs-lookup"><span data-stu-id="4a821-121">Microsoft offers two industry standard STS’s:</span></span>  
  
-   <span data-ttu-id="4a821-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span><span class="sxs-lookup"><span data-stu-id="4a821-122">[Active Directory Federation Services (AD FS) 2.0](http://go.microsoft.com/fwlink/?LinkID=247516) (http://go.microsoft.com/fwlink/?LinkID=247516)</span></span>  
  
-   <span data-ttu-id="4a821-123">[Microsoft Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span><span class="sxs-lookup"><span data-stu-id="4a821-123">[Windows Azure Access Control Service (ACS)](http://go.microsoft.com/fwlink/?LinkID=247517) (http://go.microsoft.com/fwlink/?LinkID=247517).</span></span>  
  
 <span data-ttu-id="4a821-124">AD FS 2.0 fait partie de Windows Server R2 et peut être utilisé comme un STS pour les scénarios sur site.</span><span class="sxs-lookup"><span data-stu-id="4a821-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="4a821-125">ACS est un service Cloud, proposé dans le cadre de la plateforme Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="4a821-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="4a821-126">À des fins de test ou à titre éducatif, vous pouvez également utiliser d'autres STS pour générer des applications qui prennent en charge les revendications.</span><span class="sxs-lookup"><span data-stu-id="4a821-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="4a821-127">Par exemple, vous pouvez utiliser le service STS de développement local qui fait partie de l’outil [Identity and Access Tool pour Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) disponible gratuitement en ligne.</span><span class="sxs-lookup"><span data-stu-id="4a821-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](http://go.microsoft.com/fwlink/?LinkID=245849) (http://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="4a821-128">Pour créer votre première application ASP.NET. NET prenant en charge les revendications à l'aide de WIF, suivez les instructions de l'une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a821-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
-   [<span data-ttu-id="4a821-129">Guide pratique pour générer une application web ASP.NET MVC prenant en charge les revendications à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="4a821-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
-   [<span data-ttu-id="4a821-130">Guide pratique pour générer une application Web Forms ASP.NET prenant en charge les revendications à l’aide de WIF</span><span class="sxs-lookup"><span data-stu-id="4a821-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
-   [<span data-ttu-id="4a821-131">Guide pratique pour générer une application ASP.NET prenant en charge les revendications à l’aide de l’authentification basée sur les formulaires</span><span class="sxs-lookup"><span data-stu-id="4a821-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="4a821-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a821-132">See Also</span></span>  
 [<span data-ttu-id="4a821-133">Prise en main de WIF</span><span class="sxs-lookup"><span data-stu-id="4a821-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
