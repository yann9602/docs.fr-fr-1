---
title: Services d'application cliente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- role-based security [.NET Framework], client application services
- client application services
- credentials [.NET Framework]
- Windows-based applications, client application services
- application settings, client application services
- profiles [ASP.NET], client application services
- logins [client application services]
- sharing information and functionality [client application services]
- Web settings [client application services]
- authentication [ASP.NET], client application services
- ASP.NET services, client application services
- client applications, ASP.NET services
- roles [.NET Framework], client application services
- client application services, about client application services
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 597b2d4d37d76ca722ddcebf9fcfeae532f67a00
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="client-application-services"></a><span data-ttu-id="95acc-102">Services d'application cliente</span><span class="sxs-lookup"><span data-stu-id="95acc-102">Client Application Services</span></span>
<span data-ttu-id="95acc-103">Les services d’application cliente facilitent la création d’applications Windows qui utilisent les services d’application de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] inclus dans les extensions AJAX Microsoft ASP.NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="95acc-103">Client application services make it easy for you to create Windows-based applications that use the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] login, roles, and profile application services included in the Microsoft ASP.NET 2.0 AJAX Extensions.</span></span> <span data-ttu-id="95acc-104">Ces services permettent à plusieurs applications web et Windows de partager des informations utilisateur et fonctionnalités de gestion des utilisateurs à partir d'un seul serveur.</span><span class="sxs-lookup"><span data-stu-id="95acc-104">These services enable multiple Web and Windows-based applications to share user information and user-management functionality from a single server.</span></span> <span data-ttu-id="95acc-105">Par exemple, vous pouvez utiliser ces services pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="95acc-105">For example, you can use these services to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="95acc-106">Authentifier un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95acc-106">Authenticate a user.</span></span> <span data-ttu-id="95acc-107">Vous pouvez utiliser le service d'authentification pour vérifier l'identité d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95acc-107">You can use the authentication service to verify a user's identity.</span></span>  
  
-   <span data-ttu-id="95acc-108">Déterminer le ou les rôles d'un utilisateur authentifié.</span><span class="sxs-lookup"><span data-stu-id="95acc-108">Determine the role or roles of an authenticated user.</span></span> <span data-ttu-id="95acc-109">Vous pouvez utiliser le service de rôles pour modifier l'interface utilisateur de votre application en fonction du rôle de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="95acc-109">You can use the roles service to change the user interface of your application depending on the user's role.</span></span> <span data-ttu-id="95acc-110">Par exemple, vous pouvez fournir des fonctionnalités supplémentaires pour les utilisateurs figurant dans un rôle d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="95acc-110">For example, you can provide additional features for users who are in an administrator role.</span></span>  
  
-   <span data-ttu-id="95acc-111">Stocker des paramètres d'application par utilisateur situés sur le serveur et y accéder.</span><span class="sxs-lookup"><span data-stu-id="95acc-111">Store and access per-user application settings located on the server.</span></span> <span data-ttu-id="95acc-112">Vous pouvez utiliser le service de paramètres web (également appelé service de profil) pour partager des paramètres entre plusieurs applications et emplacements.</span><span class="sxs-lookup"><span data-stu-id="95acc-112">You can use the Web settings service (also known as the profile service) to share settings across multiple applications and locations.</span></span>  
  
 <span data-ttu-id="95acc-113">Les services d'application cliente tirent parti du modèle d'extensibilité de services web via des fournisseurs de services clients que vous pouvez spécifier dans vos fichiers de configuration d'application.</span><span class="sxs-lookup"><span data-stu-id="95acc-113">Client application services take advantage of the Web services extensibility model through client service providers that you can specify in your application configuration files.</span></span> <span data-ttu-id="95acc-114">Ces fournisseurs de services incluent des fonctionnalités hors connexion qui utilisent un cache local pour l'authentification, les rôles et les données de paramètres quand une connexion réseau n'est pas disponible.</span><span class="sxs-lookup"><span data-stu-id="95acc-114">These service providers include offline functionality that uses a local cache for authentication, roles, and settings data when a network connection is unavailable.</span></span>  
  
 <span data-ttu-id="95acc-115">Pour plus d'informations sur les services d'application [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consultez [Vue d'ensemble des services d'application ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span><span class="sxs-lookup"><span data-stu-id="95acc-115">For more information about the [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] application services, see [ASP.NET Application Services Overview](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="95acc-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="95acc-116">In This Section</span></span>  
 [<span data-ttu-id="95acc-117">Vue d'ensemble des services d'application cliente</span><span class="sxs-lookup"><span data-stu-id="95acc-117">Client Application Services Overview</span></span>](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 <span data-ttu-id="95acc-118">Décrit les fonctionnalités disponibles via les fournisseurs de services d’application cliente.</span><span class="sxs-lookup"><span data-stu-id="95acc-118">Describes the features available through the client application service providers.</span></span>  
  
 [<span data-ttu-id="95acc-119">Comment : configurer les services d’application cliente</span><span class="sxs-lookup"><span data-stu-id="95acc-119">How to: Configure Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 <span data-ttu-id="95acc-120">Décrit comment utiliser le Concepteur de projets [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour activer et configurer les services d'application.</span><span class="sxs-lookup"><span data-stu-id="95acc-120">Describes how to use the [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] project designer to enable and configuration application services.</span></span> <span data-ttu-id="95acc-121">Décrit également les modifications correspondantes apportées à votre fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="95acc-121">Also describes the corresponding changes to your App.config file.</span></span>  
  
 [<span data-ttu-id="95acc-122">Comment : implémenter la connexion utilisateur avec les services d'application cliente</span><span class="sxs-lookup"><span data-stu-id="95acc-122">How to: Implement User Login with Client Application Services</span></span>](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 <span data-ttu-id="95acc-123">Décrit comment valider un utilisateur quand votre application est configurée pour utiliser un fournisseur de services d'authentification client.</span><span class="sxs-lookup"><span data-stu-id="95acc-123">Describes how to validate a user when your application is configured to use a client authentication service provider.</span></span>  
  
 [<span data-ttu-id="95acc-124">Procédure pas à pas : utilisation des services d'application cliente</span><span class="sxs-lookup"><span data-stu-id="95acc-124">Walkthrough: Using Client Application Services</span></span>](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 <span data-ttu-id="95acc-125">Décrit comment combiner toutes les fonctionnalités de services d’application cliente dans une application unique.</span><span class="sxs-lookup"><span data-stu-id="95acc-125">Describes how to combine all client application services features in a single application.</span></span> <span data-ttu-id="95acc-126">Cette procédure pas à pas fournit des conseils de bout en bout.</span><span class="sxs-lookup"><span data-stu-id="95acc-126">This walkthrough provides end-to-end guidance.</span></span> <span data-ttu-id="95acc-127">Par exemple, elle inclut des instructions sur la création d'une application de service web ASP.NET que vous pouvez utiliser pour tester les services d'application cliente.</span><span class="sxs-lookup"><span data-stu-id="95acc-127">For example, it includes instructions on how to create an ASP.NET Web Service Application that you can use to test client application services.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="95acc-128">Référence</span><span class="sxs-lookup"><span data-stu-id="95acc-128">Reference</span></span>  
 <xref:System.Web.ClientServices.ClientFormsIdentity>  
 <xref:System.Web.ClientServices.ClientRolePrincipal>  
 <xref:System.Web.ClientServices.ConnectivityStatus>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials>  
 <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider>  
 <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientWindowsAuthenticationMembershipProvider>  
 <xref:System.Web.ClientServices.Providers.ClientRoleProvider>  
 <xref:System.Web.ClientServices.Providers.ClientSettingsProvider>  
 <xref:System.Web.ClientServices.Providers.SettingsSavedEventArgs>  
 <xref:System.Web.ClientServices.Providers.UserValidatedEventArgs>  
  
## <a name="see-also"></a><span data-ttu-id="95acc-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95acc-129">See Also</span></span>  
 [<span data-ttu-id="95acc-130">Vue d’ensemble des services d’application ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95acc-130">ASP.NET Application Services Overview</span></span>](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [<span data-ttu-id="95acc-131">Utilisation de l’authentification par formulaire avec Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="95acc-131">Using Forms Authentication with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [<span data-ttu-id="95acc-132">Utilisation des informations sur les rôles avec Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="95acc-132">Using Roles Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [<span data-ttu-id="95acc-133">Utilisation des informations de profil avec Microsoft Ajax</span><span class="sxs-lookup"><span data-stu-id="95acc-133">Using Profile Information with Microsoft Ajax</span></span>](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [<span data-ttu-id="95acc-134">Authentification ASP.NET</span><span class="sxs-lookup"><span data-stu-id="95acc-134">ASP.NET Authentication</span></span>](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 <span data-ttu-id="95acc-135">[Gestion des autorisations à l’aide des rôles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span><span class="sxs-lookup"><span data-stu-id="95acc-135">[Managing Authorization Using Roles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)  </span></span>  
 [<span data-ttu-id="95acc-136">Vue d'ensemble des paramètres d'application</span><span class="sxs-lookup"><span data-stu-id="95acc-136">Application Settings Overview</span></span>](../../../docs/framework/winforms/advanced/application-settings-overview.md)
