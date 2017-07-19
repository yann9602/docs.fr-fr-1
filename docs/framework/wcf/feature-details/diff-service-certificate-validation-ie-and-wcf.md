---
title: "Diff&#233;rences entre la validation de certificat de service effectu&#233;e par Internet Explorer et celle effectu&#233;e par WCF | Microsoft Docs"
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
  - "certificats (WCF), validation de certificat de service"
  - "validation de certificat de service (WCF)"
ms.assetid: 9dffcab2-70a9-40f0-99fd-d3a0b296028f
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Diff&#233;rences entre la validation de certificat de service effectu&#233;e par Internet Explorer et celle effectu&#233;e par WCF
En raison de la différence entre la façon dont Internet Explorer et [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] valident des certificats de service lorsque le protocole HTTPS est utilisé, il est possible qu'Internet Explorer ne soit pas en mesure d'accéder à la page d'aide ou au langage WSDL \(Web Services Description Language\) d'un service bien qu'un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] soit en mesure d'envoyer avec succès des messages aux points de terminaison du service.Cela est dû au fait qu'Internet Explorer vérifie si le certificat de service a les identificateurs d'objet \(OID\) `ServerAuthentication` dans les indicateurs d'utilisation améliorés, alors que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] n'applique pas une telle contrainte.Si Internet Explorer ne peut pas accéder à la page d'aide du service ou au langage WSDL pour le service, utilisez l'[Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour accéder aux métadonnées du service.  
  
## Voir aussi  
 [Différences de validation des certificats entre HTTPS, SSL sur TCP et la sécurité SOAP](../../../../docs/framework/wcf/feature-details/cert-val-diff-https-ssl-over-tcp-and-soap.md)   
 [Comment : récupérer des métadonnées et implémenter un service conforme](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)