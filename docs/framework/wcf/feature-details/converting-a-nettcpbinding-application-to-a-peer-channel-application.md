---
title: "Conversion d&#39;une application NetTcpBinding en une application de canal homologue | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Conversion d&#39;une application NetTcpBinding en une application de canal homologue
Vous pouvez créer des connexions entre des clients à l'aide du [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] en utilisant des liaisons qui décrivent les paramètres de la connexion.  La conversion d'une application du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pour utiliser des connexions d'égal à égal requiert une liaison qui prend en charge cette technologie lors de l'établissement des connexions clientes.  Le canal homologue fournit une liaison nommée <xref:System.ServiceModel.NetPeerTcpBinding>, que vous pouvez utiliser de manière semblable à <xref:System.ServiceModel.NetTcpBinding>.  Les principales différences incluent la spécification d'un service de résolution et la définition de paramètres de sécurité.  
  
 Si une application utilise le programme de résolution et les paramètres de sécurité par défaut, la conversion d'une application normale client\-serveur pour utiliser le canal homologue implique la modification du nom de la liaison de « NetTcpBinding » en « NetPeerTcpBinding » dans le fichier de configuration de l'application ; il n'est pas nécessaire de modifier la base de code de l'application.  
  
## Voir aussi  
 [Création d'une application de canal homologue](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)   
 [Liaisons fournies par le système](../../../../docs/framework/wcf/system-provided-bindings.md)