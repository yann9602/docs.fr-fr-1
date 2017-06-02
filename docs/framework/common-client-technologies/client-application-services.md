---
title: "Services d&#39;application cliente | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "paramètres d'application, services d'application cliente"
  - "services ASP.NET, services d'application cliente"
  - "authentification (ASP.NET), services d'application cliente"
  - "services d'application cliente"
  - "services d'application cliente, à propos des services d'application cliente"
  - "applications clientes, services ASP.NET"
  - "informations d'identification (.NET Framework)"
  - "connexions (services d'application cliente)"
  - "profils (ASP.NET), services d'application cliente"
  - "sécurité basée sur les rôles (.NET Framework), services d'application cliente"
  - "rôles (.NET Framework), services d'application cliente"
  - "partager des informations et des fonctionnalités (services d'application cliente)"
  - "paramètres Web (services d'application cliente)"
  - "applications Windows, services d'application cliente"
ms.assetid: 1487d8df-089e-4f21-abfb-a791a652b58e
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Services d&#39;application cliente
Les services d'application cliente facilitent la création d'applications Windows qui utilisent les services d'application de connexion, de rôles et de profil [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] inclus dans les extensions AJAX Microsoft ASP.NET 2.0.  Ces services permettent à plusieurs applications web et Windows de partager des informations utilisateur et fonctionnalités de gestion des utilisateurs à partir d'un seul serveur.  Par exemple, vous pouvez utiliser ces services pour effectuer les tâches suivantes :  
  
-   Authentifier un utilisateur.  Vous pouvez utiliser le service d'authentification pour vérifier l'identité d'un utilisateur.  
  
-   Déterminer le ou les rôles d'un utilisateur authentifié.  Vous pouvez utiliser le service de rôles pour modifier l'interface utilisateur de votre application en fonction du rôle de l'utilisateur.  Par exemple, vous pouvez fournir des fonctionnalités supplémentaires pour les utilisateurs figurant dans un rôle d'administrateur.  
  
-   Stocker des paramètres d'application par utilisateur situés sur le serveur et y accéder.  Vous pouvez utiliser le service de paramètres web \(également appelé service de profil\) pour partager des paramètres entre plusieurs applications et emplacements.  
  
 Les services d'application cliente tirent parti du modèle d'extensibilité de services web via des fournisseurs de services clients que vous pouvez spécifier dans vos fichiers de configuration d'application.  Ces fournisseurs de services incluent des fonctionnalités hors connexion qui utilisent un cache local pour l'authentification, les rôles et les données de paramètres quand une connexion réseau n'est pas disponible.  
  
 Pour plus d'informations sur les services d'application [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)], consultez [ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md).  
  
## Dans cette section  
 [Vue d'ensemble des services d'application cliente](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 Décrit les fonctionnalités disponibles via les fournisseurs de services d'application cliente.  
  
 [Comment : configurer les services d'application cliente](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 Décrit comment utiliser le Concepteur de projets [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] pour activer et configurer les services d'application.  Décrit également les modifications correspondantes apportées à votre fichier App.config.  
  
 [Comment : implémenter la connexion utilisateur avec les services d'application cliente](../../../docs/framework/common-client-technologies/how-to-implement-user-login-with-client-application-services.md)  
 Décrit comment valider un utilisateur quand votre application est configurée pour utiliser un fournisseur de services d'authentification client.  
  
 [Procédure pas à pas : utilisation des services d'application cliente](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 Décrit comment combiner toutes les fonctionnalités de services d'application cliente dans une application unique.  Cette procédure pas à pas fournit des conseils de bout en bout.  Par exemple, elle inclut des instructions sur la création d'une application de service web ASP.NET que vous pouvez utiliser pour tester les services d'application cliente.  
  
## Référence  
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
  
## Voir aussi  
 [ASP.NET Application Services Overview](../Topic/ASP.NET%20Application%20Services%20Overview.md)   
 [Using Forms Authentication with Microsoft Ajax](../Topic/Using%20Forms%20Authentication%20with%20Microsoft%20Ajax.md)   
 [Using Roles Information with Microsoft Ajax](../Topic/Using%20Roles%20Information%20with%20Microsoft%20Ajax.md)   
 [Using Profile Information with Microsoft Ajax](../Topic/Using%20Profile%20Information%20with%20Microsoft%20Ajax.md)   
 [ASP.NET Authentication](../Topic/ASP.NET%20Authentication.md)   
 [Managing Authorization Using Roles](../Topic/Managing%20Authorization%20Using%20Roles.md)   
 [OLD NIB: Managing Application Settings](http://msdn.microsoft.com/fr-fr/7de3c3bd-e0dc-4e75-a1aa-7b0ecfaac4fc)   
 [Vue d'ensemble des paramètres d'application](../../../docs/framework/winforms/advanced/application-settings-overview.md)