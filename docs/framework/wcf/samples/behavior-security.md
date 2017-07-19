---
title: "S&#233;curit&#233; des comportements | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# S&#233;curit&#233; des comportements
Cette section contient des exemples qui indiquent comment configurer la sécurité des comportements de service.  
  
## Dans cette section  
 [Service Auditing Behavior](../../../../docs/framework/wcf/samples/service-auditing-behavior.md)  
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> pour activer l'audit des événements de sécurité pendant des opérations de service.  
  
 [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 Cet exemple montre comment un service peut utiliser les fournisseurs d'appartenances et de rôles [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour authentifier et autoriser des clients.  
  
 [Authorizing Access to Service Operations](../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 Cet exemple illustre comment utiliser l'[\<serviceAuthorization\>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l'utilisation de l'attribut <xref:System.Security.Permissions.PrincipalPermissionAttribute> et ainsi autoriser l'accès aux opérations de service.  
  
 [Emprunt de l'identité du client](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 Cet exemple montre comment emprunter l'identité de l'application de l'appelant au niveau du service afin que ce dernier puisse accéder aux ressources système pour le compte de l'appelant.