---
title: "Comparaison des services Web ASP.NET et de WCF en fonction de l&#39;objectif et des normes utilis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d3890278-fa9b-4902-91ea-8da73b7143cc
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Comparaison des services Web ASP.NET et de WCF en fonction de l&#39;objectif et des normes utilis&#233;es
Les services Web ASP.NET ont été développés pour générer des applications qui envoient et reçoivent des messages à l'aide du protocole SOAP \(Simple Object Access Protocol\) sur HTTP.  La structure des messages peut être définie à l'aide d'un schéma XML et un outil est fourni pour faciliter la sérialisation des messages vers et à partir d'objets .NET Framework.  La technologie peut générer automatiquement des métadonnées afin de décrire des services Web dans le langage WSDL \(Web Services Description Language\) et un deuxième outil est fourni pour générer des clients pour les services Web à partir du WSDL.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permet aux applications .NET Framework d'échanger des messages avec d'autres entités logicielles.  SOAP est utilisé par défaut, mais les messages peuvent se présenter sous tout format et sont acheminés en utilisant tout protocole de transport.  La structure des messages peut être définie à l'aide d'un schéma XML et il existe plusieurs options de sérialisation des messages vers et à partir d'objets .NET Framework.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peut générer automatiquement des métadonnées afin de décrire les applications générées à l'aide de la technologie dans WSDL, et il fournit également un outil pour générer des clients pour ces applications à partir du WSDL.  
  
 Les normes prises en charge par les services web ASP.NET sont documentées dans la page [Services web XML créés à l'aide d'ASP.NET](http://go.microsoft.com/fwlink/?LinkId=94872).  La liste plus étendue de normes prises en charge par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] est répertoriée dans [Protocoles de services Web pris en charge par des liaisons d'interopérabilité fournies par le système](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md).  
  
## Voir aussi  
 [Comparaison des services Web ASP.NET et de WCF du point de vue du développement](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)