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
ms.openlocfilehash: 31738e205d0b2b88cbb049607eeb027db873db3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="client-application-services"></a>Services d'application cliente
Les services d’application cliente facilitent la création d’applications Windows qui utilisent les services d’application de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] inclus dans les extensions AJAX Microsoft ASP.NET 2.0. Ces services permettent à plusieurs applications web et Windows de partager des informations utilisateur et fonctionnalités de gestion des utilisateurs à partir d'un seul serveur. Par exemple, vous pouvez utiliser ces services pour effectuer les tâches suivantes :  
  
-   Authentifier un utilisateur. Vous pouvez utiliser le service d'authentification pour vérifier l'identité d'un utilisateur.  
  
-   Déterminer le ou les rôles d'un utilisateur authentifié. Vous pouvez utiliser le service de rôles pour modifier l'interface utilisateur de votre application en fonction du rôle de l'utilisateur. Par exemple, vous pouvez fournir des fonctionnalités supplémentaires pour les utilisateurs figurant dans un rôle d'administrateur.  
  
-   Stocker des paramètres d'application par utilisateur situés sur le serveur et y accéder. Vous pouvez utiliser le service de paramètres web (également appelé service de profil) pour partager des paramètres entre plusieurs applications et emplacements.  
  
 Les services d'application cliente tirent parti du modèle d'extensibilité de services web via des fournisseurs de services clients que vous pouvez spécifier dans vos fichiers de configuration d'application. Ces fournisseurs de services incluent des fonctionnalités hors connexion qui utilisent un cache local pour l'authentification, les rôles et les données de paramètres quand une connexion réseau n'est pas disponible.  
  
 Pour plus d'informations sur les services d'application [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consultez [Vue d'ensemble des services d'application ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Vue d'ensemble des services d'application cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Décrit les fonctionnalités disponibles via les fournisseurs de services d’application cliente.  
  
 [Comment : configurer les services d’application cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Décrit comment utiliser le Concepteur de projets [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour activer et configurer les services d'application. Décrit également les modifications correspondantes apportées à votre fichier App.config.  
  
 [Comment : implémenter la connexion utilisateur avec les services d'application cliente](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Décrit comment valider un utilisateur quand votre application est configurée pour utiliser un fournisseur de services d'authentification client.  
  
 [Procédure pas à pas : utilisation des services d'application cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Décrit comment combiner toutes les fonctionnalités de services d’application cliente dans une application unique. Cette procédure pas à pas fournit des conseils de bout en bout. Par exemple, elle inclut des instructions sur la création d'une application de service web ASP.NET que vous pouvez utiliser pour tester les services d'application cliente.  
  
## <a name="reference"></a>Référence  
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
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble des Services d’Application ASP.NET](http://msdn.microsoft.com/library/1162e529-0d70-44b2-b3ab-83e60c695013)  
 [Utilisation de l’authentification par formulaire avec Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)  
 [À l’aide des informations sur les rôles avec Microsoft Ajax](http://msdn.microsoft.com/library/280f6ad9-ba1a-4fc9-b0cc-22e39e54a82d)  
 [À l’aide des informations de profil avec Microsoft Ajax](http://msdn.microsoft.com/library/91239ae6-d01c-4f4e-a433-eb9040dbed61)  
 [Authentification ASP.NET](http://msdn.microsoft.com/library/fc10b0ef-4ce4-4a7f-9174-886325221ee1)  
 [Gestion des autorisations à l’aide des rôles](http://msdn.microsoft.com/library/01954ce4-39a2-487f-8153-a69f6f6f3195)    
 [Vue d'ensemble des paramètres d'application](../../../docs/framework/winforms/advanced/application-settings-overview.md)
