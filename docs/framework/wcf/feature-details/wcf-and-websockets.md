---
title: WCF et WebSockets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e84bf7a94a6a6fa980e223daf0a6c7aaf489bb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-websockets"></a>WCF et WebSockets
.NET Framework 4.5 introduit la prise en charge de WebSockets dans Windows Communication Foundation.  WebSockets est une technologie efficace basée sur des normes qui permet la communication bidirectionnelle sur les ports HTTP standard 80 et 443. L'utilisation des ports HTTP standard permet à WebSockets de communiquer sur le Web via des intermédiaires.  Deux nouvelles liaisons standard ont été ajoutées pour prendre en charge les communications via un transport WebSocket. Voir <xref:System.ServiceModel.NetHttpBinding> et <xref:System.ServiceModel.NetHttpsBinding>. Paramètres spécifiques à WebSockets peuvent être configurés sur le <xref:System.ServiceModel.Channels.HttpTransportBindingElement> en accédant à la <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> propriété.
  
## <a name="in-this-section"></a>Dans cette section  
 [Utilisation de NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Décrit <xref:System.ServiceModel.NetHttpBinding> et la façon de le configurer.  
  
 [Guide pratique pour créer un service WCF qui communique sur WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Décrit comment créer un service WCF qui communique sur WebSockets  
  
## <a name="reference"></a>Référence  
  
## <a name="related-sections"></a>Rubriques connexes
