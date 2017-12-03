---
title: "Formats de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8ee7376f87fd0e4ce15d192dd53f872e84187acc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="metadata-formats"></a>Formats de métadonnées
Le tableau suivant répertorie les formats de métadonnées pris en charge par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="metadata-specifications-and-usage"></a>Spécification et utilisation des métadonnées  
  
|Protocole|Spécification et utilisation|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise WSDL (Web Services Description Language) pour décrire des services.|  
|Schéma XML|[XML Schema Part 2 : Datatypes Second Edition](http://go.microsoft.com/fwlink/?LinkId=94861) et [XML Schema Part 1 : Structures, deuxième édition](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise le schéma XML pour décrire les types de données utilisés dans les messages.|  
|WS-Policy|[Stratégie de Services Web 1.2 - infrastructure (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Web Services Policy 1.5 - infrastructure](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la spécification WS-Policy 1.2 ou 1.5 avec des assertions spécifiques au domaine pour décrire les spécifications et les fonctions du service.|  
|Pièces jointes WS-Policy|[Stratégie de Services Web 1.2 - pièce jointe (WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente les pièces jointes WS-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.|  
|Échange de métadonnées WS|[Échange de métadonnées de Services Web (WS-MetadataExchange) version 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente WS-MetadataExchange pour récupérer XML Schema, WSDL et WS-Policy.|  
|WS-Addressing Binding pour WSDL|[Web Services Addressing 1.0 - liaison WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente WS-Addressing Binding pour WSDL pour joindre des données d'adressage dans WSDL.|  
  
## <a name="see-also"></a>Voir aussi  
 [Protocoles pris en charge par les liaisons d’interopérabilité fournies par le système des Services Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL et stratégie](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
