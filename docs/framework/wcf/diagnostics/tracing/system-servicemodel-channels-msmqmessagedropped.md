---
title: System.ServiceModel.Channels.MsmqMessageDropped
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b6e644d-fa68-4be7-abe9-3659671a37c1
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 55b489bcad85eff5adba16f6f40493c88e476505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelsmsmqmessagedropped"></a>System.ServiceModel.Channels.MsmqMessageDropped
MSMQ a supprimé le message.  
  
## <a name="description"></a>Description  
 Cette trace indique qu'un message MSMQ a été supprimé. Les messages MSMQ peuvent être supprimés lorsque [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (utilisé avec le NetMsmqBinding ou MsmqIntegrationBinding) ne peut pas les traiter. Ces messages sont appelés des messages incohérents.  
  
 Un message incohérent est supprimé lorsque la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding a la valeur `Drop`. Ce message est supprimé de la file d’attente et ne peut plus être récupéré.  
  
 Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Le suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour dépanner votre Application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Gestion de messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546)
