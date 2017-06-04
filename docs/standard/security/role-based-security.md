---
title: "S&#233;curit&#233; bas&#233;e sur les r&#244;les | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "authentification (.NET Framework), principaux"
  - "autorisations (.NET Framework), principaux"
  - "principaux (.NET Framework)"
  - "sécurité basée sur les rôles, à propos de la sécurité basée sur les rôles"
  - "sécurité basée sur les rôles, principaux"
  - "sécurité (.NET Framework), basée sur les rôles"
  - "authentification utilisateur, principaux"
ms.assetid: 578cc32b-5654-4d8b-9d8c-ebcbc5c75390
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# S&#233;curit&#233; bas&#233;e sur les r&#244;les
Les rôles sont souvent utilisés dans les applications financières ou d'entreprise pour appliquer la stratégie.  Ainsi, une application peut restreindre la taille de la transaction en cours, selon que l'utilisateur qui effectue la demande est membre d'un rôle spécifié.  Par exemple, un employé est autorisé à exécuter les transactions se situant en deçà d'un seuil spécifié, tandis que le seuil applicable à un superviseur est plus élevé, et celui d'un vice\-président plus élevé encore \(ou inexistant\).  La sécurité basée sur les rôles peut également être utilisée quand l'application nécessite plusieurs approbations pour effectuer une action.  C'est par exemple le cas d'un système d'achat dans lequel n'importe quel employé peut générer une demande d'achat, mais où seul un responsable des achats est habilité à convertir cette demande en bon de commande pour le transmettre à un fournisseur.  
  
 La sécurité basée sur les rôles de .NET Framework prend en charge les autorisations en transmettant au thread actuel des informations sur le principal créé à partir d'une identité connexe.  L'identité \(et le principal qu'elle permet de définir\) peut être basée sur un compte Windows ou être une identité personnalisée indépendante de tout compte Windows.  Les applications .NET Framework peuvent accorder des autorisations en fonction de l'identité du principal, de son appartenance à un rôle, ou de ces deux éléments à la fois.  Un rôle est un ensemble nommé de principaux qui disposent des mêmes privilèges en matière de sécurité \(par exemple un caissier ou un responsable\).  Un principal peut être membre de plusieurs rôles.  Ainsi, les applications peuvent utiliser l'appartenance d'un principal à un rôle pour déterminer si ce principal est autorisé à exécuter l'action demandée.  
  
 Pour une plus grande convivialité et pour améliorer la cohérence avec la sécurité d'accès du code, la sécurité basée sur les rôles de .NET Framework utilise des objets <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName> qui permettent au Common Language Runtime d'octroyer des autorisations similaires à celles accordées dans le cadre de contrôles de sécurité d'accès du code.  La classe <xref:System.Security.Permissions.PrincipalPermission> représente l'identité ou le rôle que le principal doit avoir, et est à la fois compatible avec des contrôles de sécurité déclaratifs et impératifs.  Vous pouvez également accéder directement aux informations se rapportant à l'identité du principal et effectuer des vérifications de rôle et d'identité dans votre code, si nécessaire.  
  
 Le .NET Framework offre une prise en charge de la sécurité basée sur les rôles suffisamment flexible et extensible pour répondre aux exigences d'une vaste gamme d'applications.  Vous pouvez choisir d'interagir avec des infrastructures d'authentification existantes, telles que les services COM\+ 1.0, ou de créer un système d'authentification personnalisé.  La sécurité basée sur les rôles convient particulièrement aux applications web ASP.NET qui sont principalement traitées sur le serveur.  Toutefois, la sécurité basée sur les rôles de .NET Framework s'utilise aussi bien sur le client que sur le serveur.  
  
 Avant de lire cette section, assurez\-vous que vous comprenez les informations contenues dans [Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md).  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Objets Principal et Identity](../../../docs/standard/security/principal-and-identity-objects.md)|Explique comment configurer et gérer des principaux et des identités génériques et Windows.|  
|[Concepts fondamentaux sur la sécurité](../../../docs/standard/security/key-security-concepts.md)|Présente les concepts fondamentaux que vous devez comprendre avant d'utiliser la sécurité du .NET Framework.|  
  
## Reference  
 <xref:System.Security.Permissions.PrincipalPermission?displayProperty=fullName>