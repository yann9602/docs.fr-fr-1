---
title: "Cr&#233;ation de revendications et valeurs de ressource | Microsoft Docs"
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
  - "revendications (WCF), création et valeurs de ressource"
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Cr&#233;ation de revendications et valeurs de ressource
La classe <xref:System.IdentityModel.Claims.Claim> fournit plusieurs méthodes de création d'instances de types de revendications intégrés.Parmi ces méthodes, les suivantes n'effectuent pas de vérification de format ou de sémantique sur la ressource fournie :  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> \(ne vérifie pas la longueur ou contenu du tableau d'octets\)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> \(ne vérifie pas la longueur ou contenu du tableau d'octets\)  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 Lorsque vous appelez les méthodes ci\-dessus, vous devez vous assurer que les valeurs de ressource passées sont au format approprié ou qu'elles contiennent le type d'informations correct \(ou les deux\).  
  
 Les méthodes suivantes prennent des types spécifiques :  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## Voir aussi  
 <xref:System.IdentityModel.Claims.Claim>   
 <xref:System.IdentityModel.Claims.ClaimSet>   
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)