---
title: "Recherche de revendications dans une classe ClaimSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "revendications (WCF)"
  - "revendications (WCF), recherche dans un claimset"
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Recherche de revendications dans une classe ClaimSet
L'examen du contenu d'une classe <xref:System.IdentityModel.Claims.ClaimSet> dans le but de rechercher des types particuliers de revendications est une tâche courante dans le cadre de l'utilisation de l'autorisation basée sur revendication.Pour examiner une classe <xref:System.IdentityModel.Claims.ClaimSet> afin de rechercher des revendications particulières, utilisez la méthode <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A>.Cette méthode est plus performante que l'itération directe au sein de <xref:System.IdentityModel.Claims.ClaimSet>.L'exemple suivant illustre cette utilisation.Notez que les paramètres `claimType` et `claimRight` peuvent avoir la valeur `null`.Dans ce cas, les paramètres rechercheront tous les types de revendications et tous les droits de revendication.  
  
## Exemple  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## Voir aussi  
 [Gestion des revendications et autorisation avec le modèle d'identité](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)