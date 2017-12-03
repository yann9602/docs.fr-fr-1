---
title: Configuration des comportements clients
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: df5b32fa-e73b-4e8e-b66f-357c748e0173
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c63a91683817311b8d644eb4285101e32eaea7f1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-client-behaviors"></a>Configuration des comportements clients
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] configure les comportements de deux manières : en faisant référence aux configurations de comportement, qui sont définies dans la section `<behavior>` du fichier de configuration d'une application cliente, ou par programme dans l'application appelante. Cette rubrique décrit ces deux approches.  
  
 Lors de l'utilisation d'un fichier de configuration, la configuration du comportement est une collection nommée de paramètres de configuration. Le nom de chaque configuration de comportement doit être unique. Cette chaîne est utilisée dans l'attribut `behaviorConfiguration` d'une configuration de point de terminaison pour lier le point de terminaison au comportement.  
  
## <a name="example"></a>Exemple  
 Le code de configuration suivant définit un comportement appelé `myBehavior`. Le point de terminaison de client référence ce comportement dans l'attribut `behaviorConfiguration`.  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="myBehavior">  
                    <clientVia />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
        <bindings>  
            <basicHttpBinding>  
                <binding name="myBinding" maxReceivedMessageSize="10000" />  
            </basicHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="myAddress" binding="basicHttpBinding" bindingConfiguration="myBinding" behaviorConfiguration="myBehavior" contract="myContract" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-behaviors-programmatically"></a>Utilisation de comportements par programme  
 Vous pouvez également configurer ou insérer par programme des comportements en localisant la propriété `Behaviors` appropriée sur l'objet client [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] ou l'objet de fabrication de canaux client avant d'ouvrir le client.  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant indique comment insérer par programme un comportement en accédant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> sur <xref:System.ServiceModel.Description.ServiceEndpoint> retournée à partir de la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> avant la création de l'objet de canal.  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a>Voir aussi  
 [\<comportements >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
