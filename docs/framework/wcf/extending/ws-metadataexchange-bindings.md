---
title: "Liaisons WS-MetadataExchange | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Liaisons WS-MetadataExchange
Cette rubrique décrit comment les liaisons d'échange de métadonnées par défaut sont construites pour les divers transports.  
  
## Liaisons par défaut  
  
|Nom de la liaison par défaut|Construction de la liaison|  
|----------------------------------|--------------------------------|  
|MexHttpBinding|<xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport désactivée.|  
|MexHttpsBinding|<xref:System.ServiceModel.WSHttpBinding> qui prend en charge la sécurité au niveau du transport.|  
|MexNamedPipeBinding|<xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> en utilisant les valeurs par défaut.|  
|MexTcpBinding|<xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.TcpTransportBindingElement> en utilisant les valeurs par défaut.|