---
title: Utilisation de NetHttpBinding
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe134acf-ceca-49de-84a9-05a37e3841f1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ca19446d286395a744496fa300ad1a72e504e738
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-nethttpbinding"></a><span data-ttu-id="56955-102">Utilisation de NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="56955-102">Using the NetHttpBinding</span></span>
<span data-ttu-id="56955-103"><xref:System.ServiceModel.NetHttpBinding> est une liaison conçue pour consommer des services HTTP ou WebSocket et utilise l'encodage binaire par défaut.</span><span class="sxs-lookup"><span data-stu-id="56955-103"><xref:System.ServiceModel.NetHttpBinding> is a binding designed for consuming HTTP or WebSocket services and uses binary encoding by default.</span></span> <span data-ttu-id="56955-104"><xref:System.ServiceModel.NetHttpBinding> détecte si elle est utilisée avec un contrat demande-réponse ou un contrat duplex et modifie son comportement pour le faire correspondre - elle utilise HTTP pour les contrats de demande-réponse et WebSockets pour les contrats duplex.</span><span class="sxs-lookup"><span data-stu-id="56955-104"><xref:System.ServiceModel.NetHttpBinding> will detect whether it is used with a request-reply contract or duplex contract and change its behavior to match - it will use HTTP for request-reply contracts and WebSockets for duplex contracts.</span></span> <span data-ttu-id="56955-105">Ce comportement peut être substitué à l’aide de la <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` paramètre :</span><span class="sxs-lookup"><span data-stu-id="56955-105">This behavior can be overridden using the <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A> --> `WebSocketTransportUsage` setting:</span></span>  
  
1.  <span data-ttu-id="56955-106">Toujours - Force l'utilisation de WebSockets même pour les contrats de demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="56955-106">Always - This forces WebSockets to be used even for request-reply contracts.</span></span>  
  
2.  <span data-ttu-id="56955-107">Jamais - Empêche l'utilisation de WebSockets.</span><span class="sxs-lookup"><span data-stu-id="56955-107">Never - This prevents WebSockets from being used.</span></span> <span data-ttu-id="56955-108">Toute tentative d'utiliser un contrat duplex avec ce paramètre entraîne une exception.</span><span class="sxs-lookup"><span data-stu-id="56955-108">Attempting to use a duplex contract with this setting will result in an exception.</span></span>  
  
3.  <span data-ttu-id="56955-109">WhenDuplex - Il s'agit de la valeur par défaut et elle se comporte de la façon décrite ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="56955-109">WhenDuplex - This is the default value and behaves as described above.</span></span>  
  
 <span data-ttu-id="56955-110"><xref:System.ServiceModel.NetHttpBinding> prend en charge les sessions fiables en mode HTTP et en mode WebSocket.</span><span class="sxs-lookup"><span data-stu-id="56955-110"><xref:System.ServiceModel.NetHttpBinding> supports reliable sessions in both HTTP mode and WebSocket mode.</span></span> <span data-ttu-id="56955-111">Les sessions en mode WebSocket sont fournies par le transport.</span><span class="sxs-lookup"><span data-stu-id="56955-111">In WebSocket mode sessions are provided by the transport.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="56955-112">Si vous utilisez <xref:System.ServiceModel.NetHttpBinding> et le TransferMode de la liaison a la valeur TransferMode.Streamed, les grands flux peuvent provoquer un interblocage et le dépassement du délai d'attente de l'appel.</span><span class="sxs-lookup"><span data-stu-id="56955-112">When using the <xref:System.ServiceModel.NetHttpBinding> and the binding’s TransferMode is set to TransferMode.Streamed, large streams may cause a deadlock and the call will timeout.</span></span> <span data-ttu-id="56955-113">Pour contourner ce problème, envoyez de plus petits messages ou utilisez TransferMode.Buffered.</span><span class="sxs-lookup"><span data-stu-id="56955-113">To work around this issue send smaller messages or use TransferMode.Buffered.</span></span>  
  
## <a name="configuring-a-service-to-use-nethttpbinding"></a><span data-ttu-id="56955-114">Configuration d'un service de façon à utiliser NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="56955-114">Configuring a Service to use NetHttpBinding</span></span>  
 <span data-ttu-id="56955-115"><xref:System.ServiceModel.NetHttpBinding> peut être configuré de la même façon que toute autre liaison.</span><span class="sxs-lookup"><span data-stu-id="56955-115">The <xref:System.ServiceModel.NetHttpBinding> can be configured the same as any other binding.</span></span> <span data-ttu-id="56955-116">L'extrait de code suivant de configuration montre comment configurer un service WCF avec <xref:System.ServiceModel.NetHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="56955-116">The following configuration snippet illustrates how to configure a WCF service with <xref:System.ServiceModel.NetHttpBinding>.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="WcfService1.Service1">  
        <endpoint address=""  
                  binding="netHttpBinding"  
                  contract="WcfService1.IService1"/>  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
    <bindings>  
      <netHttpBinding>  
        <binding name="My_NetHttpBindingConfig">  
          <webSocketSettings transportUsage="WhenDuplex"/>  
        </binding>  
      </netHttpBinding>  
    </bindings>  
    <!- ... -->   
  </system.serviceModel>  
```  
  
 <span data-ttu-id="56955-117">L'extrait de code suivant montre comment ajouter <xref:System.ServiceModel.NetHttpBinding> dans le code.</span><span class="sxs-lookup"><span data-stu-id="56955-117">The following code snippet shows how to add the <xref:System.ServiceModel.NetHttpBinding> in code.</span></span>  
  
```csharp  
ServiceHost svchost = new ServiceHost(typeof(Service1), baseAddress);  
            NetHttpBinding binding = new NetHttpBinding();  
            svchost.AddServiceEndpoint(typeof(IService1), binding, address);   
        }  
```  
  
## <a name="see-also"></a><span data-ttu-id="56955-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56955-118">See Also</span></span>  
 [<span data-ttu-id="56955-119">Configuration de liaisons pour les services</span><span class="sxs-lookup"><span data-stu-id="56955-119">Configuring Bindings for Services</span></span>](../../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="56955-120">Liaisons</span><span class="sxs-lookup"><span data-stu-id="56955-120">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [<span data-ttu-id="56955-121">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="56955-121">System-Provided Bindings</span></span>](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [<span data-ttu-id="56955-122">Services duplex</span><span class="sxs-lookup"><span data-stu-id="56955-122">Duplex Services</span></span>](../../../../docs/framework/wcf/feature-details/duplex-services.md)
