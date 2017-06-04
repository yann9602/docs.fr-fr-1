---
title: "M&#233;canismes de contr&#244;le d&#39;acc&#232;s | Microsoft Docs"
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
  - "contrôle d'accès (WCF)"
  - "sécurité WCF"
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# M&#233;canismes de contr&#244;le d&#39;acc&#232;s
Vous pouvez contrôler l'accès de plusieurs façons avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].Cette rubrique présente brièvement les différents mécanismes et suggère quand utiliser chacun ; elle a pour objectif de vous aider à sélectionner le mécanisme approprié à utiliser.Les technologies d'accès sont répertoriées par ordre de complexité.La plus simple est le <xref:System.Security.Permissions.PrincipalPermissionAttribute> ; la plus complexe est le modèle d'identité.  
  
 Outre ces mécanismes, l'emprunt d'identité et la délégation avec [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sont expliqués dans [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> permet de restreindre l'accès à une méthode de service.Lorsque l'attribut est appliqué à une méthode, il permet de demander l'identité d'un appelant spécifique ou son appartenance à un groupe Windows ou à un rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].Si le client est authentifié à l'aide d'un certificat X.509, il bénéficie d'une identité principale qui se compose du nom du sujet auquel s'ajoute l'empreinte numérique du certificat.  
  
 Utilisez l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> pour contrôler l'accès aux ressources sur l'ordinateur où le service s'exécute et pour contrôler si les utilisateurs du service feront toujours partie du même domaine Windows sur lequel le service s'exécute.Vous pouvez créer facilement des groupes Windows disposant de niveaux d'accès spécifiés \(tels qu'aucun, lecture seule ou lecture et écriture\).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de l'attribut, consultez [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'identité, consultez [Identité du service et authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## Fournisseur d'appartenances ASP.NET  
 Une des fonctionnalités d'[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est le fournisseur d'appartenances.Bien que le fournisseur d'appartenances ne soit pas techniquement un mécanisme de contrôle d'accès, il permet de contrôler l'accès au service en limitant le jeu d'identités possibles qui peuvent accéder au point de terminaison du service.La fonctionnalité d'appartenance inclut une base de données qui peut être remplie avec des associations nom d'utilisateur\/mot de passe qui permettent aux utilisateurs d'un site Web d'établir des comptes avec le site.Pour accéder à un service qui utilise le fournisseur d'appartenances, un utilisateur doit se connecter avec son nom d'utilisateur et son mot de passe.  
  
> [!NOTE]
>  Vous devez remplir la base de données à l'aide de la fonctionnalité [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour qu'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] puisse l'utiliser à des fins d'autorisation.  
  
 Vous pouvez également utiliser la fonctionnalité d'appartenance si vous avez déjà une base de données d'appartenance provenant d'un site Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] existant et que vous souhaitez permettre aux mêmes utilisateurs d'utiliser votre service en utilisant les mêmes noms d'utilisateur et mots de passe.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de la fonctionnalité d'appartenance dans un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : utiliser le fournisseur d'appartenances ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## Fournisseur de rôle ASP.NET  
 Une autre fonctionnalité d'[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] est la capacité à gérer l'autorisation à l'aide de rôles.Le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] permet à un développeur de créer des rôles pour les utilisateurs et d'assigner chaque utilisateur à un ou plusieurs rôles.Comme avec le fournisseur d'appartenances, les rôles et les assignations sont stockés dans une base de données et peuvent être remplis à l'aide d'outils fournis par une implémentation particulière du fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].Comme avec la fonctionnalité d'appartenance, les développeurs [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent utiliser les informations dans la base de données pour autoriser les utilisateurs du service au moyen des rôles.Par exemple, ils peuvent utiliser le fournisseur de rôle en association avec le mécanisme de contrôle d'accès `PrincipalPermissionAttribute` décrit précédemment.  
  
 Vous pouvez également utiliser le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] si vous avez une base de données de fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] existante et souhaitez utiliser le même ensemble de règles et d'assignations utilisateur dans votre service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation de la fonctionnalité de fournisseur de rôle, consultez [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## Gestionnaire d'autorisations  
 Une autre fonctionnalité associe le Gestionnaire d'autorisations \(AzMan\) et le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour autoriser les clients.Lorsque [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] héberge un service Web, AzMan peut être intégré dans l'application afin que l'autorisation au service s'effectue via AzMan.Le Gestionnaire de rôles [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] fournit une API qui vous permet de gérer les rôles d'application, d'ajouter et de supprimer des utilisateurs dans des rôles et de vérifier l'appartenance aux rôles, mais elle ne vous permet pas d'effectuer une requête pour savoir si un utilisateur est autorisé à exécuter une tâche nommée ou une opération.AzMan vous permet de définir des opérations individuelles et de les associer dans des tâches.Grâce à AZMan, outre les contrôles de rôle, vous pouvez également vérifier si un utilisateur peut effectuer une tâche.L'affectation des rôles et l'autorisation des tâches peuvent être configurées en dehors de l'application ou effectuées par programme au sein de l'application.Le composant logiciel enfichable Microsoft Management Console \(MMC\) d'administration AzMan permet aux administrateurs de modifier les tâches qu'un rôle peut effectuer au moment de l'exécution et de gérer l'appartenance aux rôles de chaque utilisateur.  
  
 Vous pouvez également utiliser AzMan et le fournisseur de rôle [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] si vous avez déjà accès à une installation AzMan existante et souhaitez autoriser les utilisateurs de votre service à utiliser les fonctionnalités combinées d'AzMan et du fournisseur de rôle.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] AzMan et le fournisseur de rôles [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], consultez [Procédure : utiliser le Gestionnaire d'autorisations \(AzMan\) avec ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=88951).[!INCLUDE[crabout](../../../../includes/crabout-md.md)] l'utilisation d'AzMan et du fournisseur de rôle pour les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], consultez [Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## Modèle d'identité  
 Le modèle d'identité est un ensemble d'API qui vous permettent de gérer des revendications et des stratégies pour autoriser des clients.Le modèle d'identité vous permet d'examiner chaque revendication incluse dans les informations d'identification que l'appelant a utilisée pour s'authentifier auprès du service, de comparer les revendications au jeu de stratégies pour le service et d'accorder ou de refuser l'accès en fonction de cette comparaison.  
  
 Utilisez le modèle d'identité si vous avez besoin d'un contrôle précis et de la capacité de définir des critères spécifiques avant d'accorder l'accès.Par exemple, lorsque vous utilisez <xref:System.Security.Permissions.PrincipalPermissionAttribute>, le critère est simplement que l'identité de l'utilisateur est authentifiée et que l'utilisateur appartient à un rôle spécifique.En revanche, le modèle d'identité vous permet de créer une stratégie stipulant que l'utilisateur doit être majeur et qu'il doit posséder un permis de conduire valide pour pouvoir être autorisé à consulter un document.  
  
 Par exemple, vous pouvez tirer parti du contrôle d'accès basé sur revendication du modèle d'identité lorsque vous utilisez des informations d'identification de fédération dans le scénario de jeton émis.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] la fédération et les jetons émis, consultez [Fédération et jetons émis](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] le modèle d'identité, consultez [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## Voir aussi  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)   
 [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)   
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)