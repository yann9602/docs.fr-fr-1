---
title: "Comment : créer une identité d'principal de sécurité personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IPrincipal
- IAuthorizationPolicy
- PrincipalPermissionMode
- PrincipalPermissionAttribute
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 393bc7a33a522f483dc4daf1531c23afe421c261
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-custom-principal-identity"></a>Comment : créer une identité d'principal de sécurité personnalisée
Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constitue un moyen déclaratif de contrôler l'accès aux méthodes de service. Lors de l'utilisation de cet attribut, l'énumération <xref:System.ServiceModel.Description.PrincipalPermissionMode> spécifie le mode d'exécution des contrôles d'autorisation. Lorsque ce mode a la valeur <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom>, il permet à l'utilisateur de spécifier une classe <xref:System.Security.Principal.IPrincipal> personnalisée retournée par la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A>. Cette rubrique illustre le scénario lorsque <xref:System.ServiceModel.Description.PrincipalPermissionMode.Custom> est utilisé en association avec une stratégie d'autorisation personnalisée et une principal de sécurité personnalisée.  
  
 Pour plus d’informations sur l’utilisation de la <xref:System.Security.Permissions.PrincipalPermissionAttribute>, consultez [Comment : restreindre l’accès à la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Des références aux espaces de noms suivants sont exigées pour compiler le code :  
  
-   <xref:System>  
  
-   <xref:System.Collections.Generic>  
  
-   <xref:System.Security.Permissions>  
  
-   <xref:System.Security.Principal>  
  
-   <xref:System.Threading>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.ServiceModel.Description>  
  
-   <xref:System.IdentityModel.Claims>  
  
-   <xref:System.IdentityModel.Policy>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
 [Guide pratique pour utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
