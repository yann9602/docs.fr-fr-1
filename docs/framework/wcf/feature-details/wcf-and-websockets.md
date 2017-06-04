---
title: "WCF et WebSockets | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# WCF et WebSockets
.NET Framework 4.5 introduit la prise en charge de WebSockets dans Windows Communication Foundation.WebSockets est une technologie efficace basée sur des normes qui permet la communication bidirectionnelle sur les ports HTTP standard 80 et 443.L'utilisation des ports HTTP standard permet à WebSockets de communiquer sur le Web via des intermédiaires.Deux nouvelles liaisons standard ont été ajoutées pour prendre en charge les communications via un transport WebSocket.<xref:System.ServiceModel.NetHttpBinding> et <xref:System.ServiceModel.NetHttpsBinding>.Les paramètres spécifiques à WebSockets peuvent être configurés dans l'élément <xref:> System.ServiceModel.Channels.HttpTransportBinding?qualifyHint=False&autoUpgrade=True en accédant à la propriété <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A>.  
  
## Dans cette section  
 [Utilisation de NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Décrit <xref:System.ServiceModel.NetHttpBinding> et la façon de le configurer.  
  
 [Procédure pour créer un service WCF qui communique sur WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Décrit comment créer un service WCF qui communique sur WebSockets  
  
## Référence  
  
## Rubriques connexes