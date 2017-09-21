---
title: "PNRP dans le développement d’applications"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
caps.latest.revision: 6
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f20dd62b5b872b932639a10df1e1636798ba963
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="pnrp-in-application-development"></a>PNRP dans le développement d’applications
Dans Windows Vista, les applications réseau peuvent accéder aux fonctions de résolution et de publication des noms via une API PNRP simplifiée.  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implémentation du protocole PNRP  
 Avec l’API PNRP simplifiée, les clouds ne sont pas explicitement spécifiés pour inscrire des noms et des adresses. Le composant PNRP détermine automatiquement les clouds qu’il est possible de rejoindre, ainsi que les adresses à publier dans les clouds.  
  
 Pour une résolution beaucoup plus simple des noms PNRP dans Windows Vista, ceux-ci sont désormais intégrés dans la fonction getaddrinfo() de Windows Sockets. Pour utiliser PNRP afin de résoudre un nom en une adresse IPv6, les applications peuvent utiliser la fonction getaddrinfo() pour résoudre le nom de domaine complet (FQDN) « nom.prnp.net », où « nom » correspond au nom de pair en cours de résolution. Le domaine pnrp.net est un domaine réservé dans Windows Vista pour la résolution de noms PNRP.  
  
 La transmission de messages entre applications PeerToPeer est toujours gérée par des architectures sous-jacentes telles que PeerChannel et WCF. [Données volumineuses et streaming](http://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Net.PeerToPeer>

