---
title: "Autorisation dans WCF | Microsoft Docs"
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
  - "autorisation (WCF)"
  - "sécurité [WCF], autorisation"
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# Autorisation dans WCF
L'autorisation est le processus qui consiste à contrôler l'accès et les droits aux ressources, telles que les services ou fichiers.Les rubriques de cette section vous indiquent comment effectuer cette tâche de base dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] de diverses manières.  
  
## Dans cette section  
 [Mécanismes de contrôle d'accès](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 Fournit une présentation des mécanismes d'autorisation dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et des suggestions d'utilisation.  
  
 [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Illustre le processus de limitation de l'accès à un service avec le <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Décrit les différentes étapes de la configuration d'un service pour lui permettre d'utiliser la fonctionnalité de fournisseur de rôle de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].  
  
 [Comment : utiliser le fournisseur de rôle du Gestionnaire d'autorisations ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] peut utiliser le Gestionnaire d'autorisations pour gérer l'autorisation pour un site Web.[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut de la même façon tirer parti de la combinaison [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]\/Gestionnaire d'autorisations pour l'autorisation des clients.  
  
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 Explique les principes de base de l'utilisation de l'infrastructure Modèle d'identité pour l'autorisation basée sur les revendications.  
  
 [Délégation et emprunt d'identité](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 Explique la différence entre la délégation et l'emprunt d'identité.  
  
## Référence  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## Rubriques connexes  
 [Authentification](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## Voir aussi  
 [Vue d'ensemble de la sécurité](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Modèle de sécurité pour Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)