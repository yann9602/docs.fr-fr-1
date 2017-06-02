---
title: "Extensibilit&#233; des liaisons | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Extensibilit&#233; des liaisons
Cette section contient des exemples qui illustrent la liaison personnalisée dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## Dans cette section  
 <xref:System.ServiceModel.NetHttpBinding>  
 Montre comment implémenter une liaison qui empile <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou le <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> au\-dessus du <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.  
  
 <xref:System.ServiceModel.WSStreamedHttpBinding>  
 Montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.