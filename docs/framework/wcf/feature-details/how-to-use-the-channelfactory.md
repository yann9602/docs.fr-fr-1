---
title: "Comment&#160;: utiliser la classe ChannelFactory | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Comment&#160;: utiliser la classe ChannelFactory
La classe <xref:System.ServiceModel.ChannelFactory%601> générique est utilisée dans les scénarios avancés qui requièrent la création d'une fabrication de canal pouvant être utilisée pour créer plusieurs canaux.  
  
### Pour créer et utiliser la classe ChannelFactory  
  
1.  Générez et exécutez un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Conception et implémentation de services](../../../../docs/framework/wcf/designing-and-implementing-services.md), [Configuration des services](../../../../docs/framework/wcf/configuring-services.md) et [Hébergement de services](../../../../docs/framework/wcf/hosting-services.md).  
  
2.  Utilisez [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le contrat \(interface\) pour le client.  
  
3.  Dans le code client, utilisez la classe <xref:System.ServiceModel.ChannelFactory%601> pour créer plusieurs écouteurs de point de terminaison.  
  
## Exemple  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]