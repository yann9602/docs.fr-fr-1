---
title: Liaisons WS-MetadataExchange
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d305f3bf34b3b14da566fa792552e24e695ef33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ws-metadataexchange-bindings"></a>Liaisons WS-MetadataExchange
Cette rubrique décrit comment les liaisons d’échange de métadonnées par défaut sont construites pour les divers transports.  
  
## <a name="the-default-bindings"></a>Liaisons par défaut  
  
|Nom de la liaison par défaut|Construction de la liaison|  
|--------------------------|------------------------------------|  
|MexHttpBinding|<xref:System.ServiceModel.WSHttpBinding> avec la sécurité au niveau du transport désactivée.|  
|MexHttpsBinding|<xref:System.ServiceModel.WSHttpBinding> qui prend en charge la sécurité au niveau du transport.|  
|MexNamedPipeBinding|<xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> en utilisant les valeurs par défaut.|  
|MexTcpBinding|<xref:System.ServiceModel.Channels.CustomBinding> avec <xref:System.ServiceModel.Channels.TcpTransportBindingElement> en utilisant les valeurs par défaut.|
