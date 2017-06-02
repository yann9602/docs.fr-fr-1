---
title: "Formats de m&#233;tadonn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Formats de m&#233;tadonn&#233;es
Le tableau suivant répertorie les formats de métadonnées pris en charge par [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Spécification et utilisation des métadonnées  
  
|Protocole|Spécification et utilisation|  
|---------------|----------------------------------|  
|WSDL 1.1|[Langage WSDL \(Web Services Description Language\) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise WSDL \(Web Services Description Language\) pour décrire des services.|  
|Schéma XML|[Schéma XML, partie 2 : types de données, deuxième édition](http://go.microsoft.com/fwlink/?LinkId=94861) et [Schéma XML, partie 1 : structures, deuxième édition](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise le schéma XML pour décrire les types de données utilisés dans les messages.|  
|WS\-Policy|[Web Services Policy 1.2 \- Infrastructure \(WS\-Policy\)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Web Services Policy 1.5 \- Infrastructure](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise la spécification WS\-Policy 1.2 ou 1.5 avec des assertions spécifiques au domaine pour décrire les spécifications et les fonctions du service.|  
|Pièces jointes WS\-Policy|[Web Services Policy 1.2 \- Pièce jointe \(WS\-PolicyAttachment\)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente les pièces jointes WS\-Policy pour joindre des expressions de stratégie à différentes étendues dans WSDL.|  
|Échange de métadonnées WS|[Web Services Metadata Exchange \(WS\-MetadataExchange\) version 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente WS\-MetadataExchange pour récupérer XML Schema, WSDL et WS\-Policy.|  
|WS\-Addressing Binding pour WSDL|[Web Services Addressing 1.0 \- Liaison WSDL](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implémente WS\-Addressing Binding pour WSDL pour joindre des données d'adressage dans WSDL.|  
  
## Voir aussi  
 [Protocoles de services Web pris en charge par des liaisons d'interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)   
 [WSDL et stratégie](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)