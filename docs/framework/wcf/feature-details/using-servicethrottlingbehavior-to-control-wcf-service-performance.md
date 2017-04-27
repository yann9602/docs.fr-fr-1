---
title: "Utilisation de ServiceThrottlingBehavior pour contr&#244;ler les performances du service WCF | Microsoft Docs"
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
  - "comportement (WCF), les performances du service"
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Utilisation de ServiceThrottlingBehavior pour contr&#244;ler les performances du service WCF
Le <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> classe expose des propriétés que vous pouvez utiliser pour limiter le nombre d’instances ou de sessions créées au niveau de l’application. À l'aide de ce comportement, vous pouvez ajuster avec précision les performances de votre application [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>Contrôle des instances de service et des appels simultanés  
 Utilisez le <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> pour spécifier le nombre maximal de messages de traitement actif sur un <xref:System.ServiceModel.ServiceHost> (classe) et le <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> pour spécifier le nombre maximal de <xref:System.ServiceModel.InstanceContext> objets dans le service.  
  
 Parce que la détermination des paramètres pour ces propriétés généralement a lieu après exécution de l’application par rapport à l’expérience réelle se charge, les paramètres de la <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> propriétés est généralement spécifié dans un fichier de configuration application à l’aide du [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md) élément.  
  
 L’exemple de code suivant illustre l’utilisation de la <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> classe à partir d’un fichier de configuration qui définit les <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>, <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, et <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> propriétés 1 en guise d’exemple. L'expérience détermine les paramètres optimaux pour toute application particulière.  
  
 <!-- TODO: review snippet reference [!code-csharp[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  -->  
  
 Le comportement d’exécution exact dépend des valeurs de la <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> et <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> propriétés qui contrôlent le nombre de messages pouvant s’exécuter à l’intérieur d’une opération à la fois et les durées de vie du service <xref:System.ServiceModel.InstanceContext> relatif entrant des sessions de canal, respectivement.  
  
 Pour plus d’informations, consultez <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>, et <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>   
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>