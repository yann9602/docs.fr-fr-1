---
title: "Sécurité des comportements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19710ae3-f197-4d28-ba9d-52e465006819
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: a125aa0968abbd69580cab46f3231a6536eff9c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="behavior-security"></a>Sécurité des comportements
Cette section contient des exemples qui indiquent comment configurer la sécurité des comportements de service.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Comportement de l’audit de service](../../../../docs/framework/wcf/samples/service-auditing-behavior.md)  
 Cet exemple montre comment utiliser <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> pour activer l'audit des événements de sécurité pendant des opérations de service.  
  
 [Fournisseur d’appartenances et de rôles](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 Cet exemple montre comment un service peut utiliser les fournisseurs d'appartenances et de rôles [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] pour authentifier et autoriser des clients.  
  
 [Autorisation de l’accès aux opérations de service](../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 Cet exemple montre comment utiliser le [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) pour permettre l’utilisation de la <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribut pour autoriser l’accès aux opérations de service.  
  
 [Emprunt de l’identité du client](../../../../docs/framework/wcf/samples/impersonating-the-client.md)  
 Cet exemple montre comment emprunter l'identité de l'application de l'appelant au niveau du service afin que ce dernier puisse accéder aux ressources système pour le compte de l'appelant.
