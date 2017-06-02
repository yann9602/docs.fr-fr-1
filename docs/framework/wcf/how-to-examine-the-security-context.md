---
title: "Comment&#160;: examiner le contexte de s&#233;curit&#233; | Microsoft Docs"
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
  - "Claimset (classe)"
  - "ServiceSecurityContext (classe)"
  - "WCF, sécurité"
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# Comment&#160;: examiner le contexte de s&#233;curit&#233;
Lorsque vous programmez des services [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], le contexte de sécurité vous permet de déterminer les détails relatifs aux informations d'identification du client et les revendications utilisées pour authentifier avec le service.Pour ce faire, utilisez les propriétés de la classe <xref:System.ServiceModel.ServiceSecurityContext>.  
  
 Par exemple, vous pouvez récupérer l'identité du client actuel en utilisant la propriété <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.Pour déterminer si le client est ou non anonyme, utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.  
  
 Vous pouvez également déterminer les revendications effectuées pour le compte du client en effectuant une itération dans la collection de revendications de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
### Pour obtenir le contexte de sécurité actuel  
  
-   Accédez à la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> statique pour obtenir le contexte de sécurité actuel.Examinez chacune des propriétés du contexte actuel à partir de la référence.  
  
### Pour déterminer l'identité de l'appelant  
  
1.  Imprimez la valeur des propriétés <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.  
  
### Pour analyser les revendications d'un appelant  
  
1.  Retournez la classe actuelle <xref:System.IdentityModel.Policy.AuthorizationContext>.Utilisez la propriété <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pour retourner le contexte de sécurité des services actuel, puis retournez `AuthorizationContext` à l'aide de la propriété <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
2.  Analysez la collection d'objets <xref:System.IdentityModel.Claims.ClaimSet> retournés par la propriété <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> de la classe <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
## Exemple  
 L'exemple suivant imprime les valeurs des propriétés <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> et <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> du contexte de sécurité actuel ainsi que la propriété <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, la valeur de ressource de la revendication et la propriété <xref:System.IdentityModel.Claims.Claim.Right%2A> de chaque revendication du contexte de sécurité actuel.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## Compilation du code  
 Le code utilise les espaces de noms suivants :  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## Voir aussi  
 [Sécurisation de services](../../../docs/framework/wcf/securing-services.md)   
 [Identité du service et authentification](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)