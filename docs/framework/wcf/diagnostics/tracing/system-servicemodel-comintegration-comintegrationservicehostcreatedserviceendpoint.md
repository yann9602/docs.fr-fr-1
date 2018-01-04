---
title: System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d75d39da-7502-4a6a-91b9-eaa05b8e24d5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 87eac8f0e3949ac47c7bb2915a87043bdc205b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelsmsmqmoveordeleteattemptfailed"></a>System.ServiceModel.Channels.MsmqMoveOrDeleteAttemptFailed
Impossible de déplacer ou de supprimer le message.  
  
## <a name="description"></a>Description  
 Le suivi indique qu'un échec a eu lieu lors de la tentative de déplacement, d'élimination ou de rejet d'un message MSMQ.  
  
 Les messages MSMQ sont employés par [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] (lorsque utilisé avec NetMsmqBinding ou MsmqIntegrationBinding). Ce suivi concerne la valeur choisie pour la propriété `ReceiveErrorHandling` sur NetMsmqBinding ou MsmqIntegrationBinding.  
  
 Ce suivi n'indique pas une défaillance générale du système. Toutefois, il indique que la disposition de message incohérent choisie a échoué pour un message. Consultez [des messages incohérents](http://go.microsoft.com/fwlink/?LinkID=99546) pour plus d’informations sur le moment où les messages deviennent incohérents et comment configurer votre service pour gérer de façon appropriée.  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Utilisation du suivi pour résoudre les problèmes posés par votre application](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administration et diagnostics](../../../../../docs/framework/wcf/diagnostics/index.md)
