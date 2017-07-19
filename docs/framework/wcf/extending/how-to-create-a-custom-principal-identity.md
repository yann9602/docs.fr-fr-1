---
title: "Comment&#160;: cr&#233;er une identit&#233; d&#39;principal de s&#233;curit&#233; personnalis&#233;e | Microsoft Docs"
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
  - "IAuthorizationPolicy"
  - "IPrincipal"
  - "PrincipalPermissionAttribute"
  - "PrincipalPermissionMode"
ms.assetid: c4845fca-0ed9-4adf-bbdc-10812be69b61
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Comment&#160;: cr&#233;er une identit&#233; d&#39;principal de s&#233;curit&#233; personnalis&#233;e
Le <xref:System.Security.Permissions.PrincipalPermissionAttribute> constitue un moyen déclaratif de contrôler l'accès aux méthodes de service.  Lors de l'utilisation de cet attribut, l'énumération <xref:System.ServiceModel.Description.PrincipalPermissionMode> spécifie le mode d'exécution des contrôles d'autorisation.  Lorsque ce mode a la valeur <xref:System.ServiceModel.Description.PrincipalPermissionMode>, il permet à l'utilisateur de spécifier une classe <xref:System.Security.Principal.IPrincipal> personnalisée retournée par la propriété <xref:System.Threading.Thread.CurrentPrincipal%2A>.  Cette rubrique illustre le scénario lorsque <xref:System.ServiceModel.Description.PrincipalPermissionMode> est utilisé en association avec une stratégie d'autorisation personnalisée et une principal de sécurité personnalisée.  
  
 Pour plus d'informations sur l'utilisation du <xref:System.Security.Permissions.PrincipalPermissionAttribute>, consultez [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).  
  
## Exemple  
 [!code-csharp[PrincipalPermissionMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/principalpermissionmode/cs/source.cs#8)]
 [!code-vb[PrincipalPermissionMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/principalpermissionmode/vb/source.vb#8)]  
  
## Compilation du code  
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
  
## Voir aussi  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>   
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>   
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>   
 [Comment : utiliser le fournisseur de rôle ASP.NET avec un service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)   
 [Comment : restreindre l'accès à l'aide de la classe PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)