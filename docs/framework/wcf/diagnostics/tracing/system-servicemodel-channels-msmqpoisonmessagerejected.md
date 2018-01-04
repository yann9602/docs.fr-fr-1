---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28924f04dc83387f49c2369c2598c028f9b8d4bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a>System.ServiceModel.Channels.MsmqPoisonMessageRejected
Message poison rejeté.  
  
## <a name="description"></a>Description  
 Le suivi indique qu'un message poison a été rencontré et rejeté par la suite. Cela se produit seulement lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Reject`. Un message rejeté est remis à l’expéditeur [file d’attente de lettres mortes](http://go.microsoft.com/fwlink/?LinkId=99544).  
  
 Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkId=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée. Consultez [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548) pour plus d’informations sur ce que signifie un message rejeté dans MSMQ.  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Gestion de messages incohérents](http://go.microsoft.com/fwlink/?LinkId=99546)  
 [MQMarkMessageRejected](http://go.microsoft.com/fwlink/?LinkId=99548)
