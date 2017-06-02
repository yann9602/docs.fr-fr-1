---
title: "PNRP dans le d&#233;veloppement d’applications | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: 6
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 6
---
# PNRP dans le d&#233;veloppement d’applications
Dans Windows Vista, les applications de mise en réseau peuvent accéder à la composition de nom et la résolution de l'exécution via une interface de programmation simplifiée \(API\) de PNRP.  
  
## Implémenter le fournisseur homologue de résolution de noms  
 Avec l'API de PNRP simplifiée, les nuages ne sont pas spécifiés explicitement pour enregistrer le nom et l'adresse ; le composant de PNRP détermine automatiquement les nuages appropriés pour attacher et les adresses pour publier dans les nuages.  
  
 Pour la résolution de noms extrêmement simplifiée de PNRP dans Windows Vista, les noms de PNRP sont maintenant intégrés dans la fonction getaddrinfo\(\) Windows Sockets.  Pour utiliser PNRP pour résoudre un nom à une adresse IPv6, les applications peuvent utiliser la fonction getaddrinfo\(\) pour résoudre le nom de domaine complet \(FQDN\) name.prnp.  réseau, dans lequel le nom est nom homologue est résolu.  Le pnrp.  le champ .NET est un champ réservé dans Windows Vista pour la résolution de noms de PNRP.  
  
 Le passage de messages entre les applications PeerToPeer est toujours exécuté par les architectures sous\-jacentes telles que PeerChannel et WCF [Les données et diffusion en continu](http://go.microsoft.com/fwlink/?LinkID=179652).  
  
## Voir aussi  
 <xref:System.Net.PeerToPeer>