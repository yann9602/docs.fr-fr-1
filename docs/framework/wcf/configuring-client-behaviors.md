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
ms.workload: dotnet
ms.openlocfilehash: ee79900b52ae0fa58e8fb9a5cbbf50f5a882c295
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-client-behaviors"></a><span data-ttu-id="e99f2-102">Configuration des comportements clients</span><span class="sxs-lookup"><span data-stu-id="e99f2-102">Configuring Client Behaviors</span></span>
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]<span data-ttu-id="e99f2-103"> configure les comportements de deux manières : en faisant référence aux configurations de comportement, qui sont définies dans la section `<behavior>` du fichier de configuration d'une application cliente, ou par programme dans l'application appelante.</span><span class="sxs-lookup"><span data-stu-id="e99f2-103"> configures behaviors in two ways: either by referring to behavior configurations -- which are defined in the `<behavior>` section of a client application configuration file – or programmatically in the calling application.</span></span> <span data-ttu-id="e99f2-104">Cette rubrique décrit ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="e99f2-104">This topic describes both approaches.</span></span>  
  
 <span data-ttu-id="e99f2-105">Lors de l'utilisation d'un fichier de configuration, la configuration du comportement est une collection nommée de paramètres de configuration.</span><span class="sxs-lookup"><span data-stu-id="e99f2-105">When using a configuration file, behavior configuration is a named collection of configuration settings.</span></span> <span data-ttu-id="e99f2-106">Le nom de chaque configuration de comportement doit être unique.</span><span class="sxs-lookup"><span data-stu-id="e99f2-106">The name of each behavior configuration must be unique.</span></span> <span data-ttu-id="e99f2-107">Cette chaîne est utilisée dans l'attribut `behaviorConfiguration` d'une configuration de point de terminaison pour lier le point de terminaison au comportement.</span><span class="sxs-lookup"><span data-stu-id="e99f2-107">This string is used in the `behaviorConfiguration` attribute of an endpoint configuration to link the endpoint to the behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99f2-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="e99f2-108">Example</span></span>  
 <span data-ttu-id="e99f2-109">Le code de configuration suivant définit un comportement appelé `myBehavior`.</span><span class="sxs-lookup"><span data-stu-id="e99f2-109">The following configuration code defines a behavior called `myBehavior`.</span></span> <span data-ttu-id="e99f2-110">Le point de terminaison de client référence ce comportement dans l'attribut `behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e99f2-110">The client endpoint references this behavior in the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="using-behaviors-programmatically"></a><span data-ttu-id="e99f2-111">Utilisation de comportements par programme</span><span class="sxs-lookup"><span data-stu-id="e99f2-111">Using Behaviors Programmatically</span></span>  
 <span data-ttu-id="e99f2-112">Vous pouvez également configurer ou insérer par programme des comportements en localisant la propriété `Behaviors` appropriée sur l'objet client [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] ou l'objet de fabrication de canaux client avant d'ouvrir le client.</span><span class="sxs-lookup"><span data-stu-id="e99f2-112">You can also configure or insert behaviors programmatically by locating the appropriate `Behaviors` property on the [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] client object or on the client channel factory object prior to opening the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99f2-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="e99f2-113">Example</span></span>  
 <span data-ttu-id="e99f2-114">L'exemple de code suivant indique comment insérer par programme un comportement en accédant à la propriété <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> sur <xref:System.ServiceModel.Description.ServiceEndpoint> retournée à partir de la propriété <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> avant la création de l'objet de canal.</span><span class="sxs-lookup"><span data-stu-id="e99f2-114">The following code example shows how to programmatically insert a behavior by accessing the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property on the <xref:System.ServiceModel.Description.ServiceEndpoint> returned from the <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> property prior to the creation of the channel object.</span></span>  
  
 [!code-csharp[ChannelFactoryBehaviors#10](../../../samples/snippets/csharp/VS_Snippets_CFX/channelfactorybehaviors/cs/client.cs#10)]
 [!code-vb[ChannelFactoryBehaviors#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelfactorybehaviors/vb/client.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e99f2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e99f2-115">See Also</span></span>  
 [<span data-ttu-id="e99f2-116">\<comportements ></span><span class="sxs-lookup"><span data-stu-id="e99f2-116">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
