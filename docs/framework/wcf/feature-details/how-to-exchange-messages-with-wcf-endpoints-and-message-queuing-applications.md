---
title: "Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing"
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
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa6f9d0b9631420013593cb44903b5451549e8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="c6501-102">Comment : échanger des messages avec des points de terminaison WCF et des applications Message Queuing</span><span class="sxs-lookup"><span data-stu-id="c6501-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="c6501-103">Vous pouvez intégrer des applications Message Queuing (MSMQ) existantes aux applications [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] en utilisant la liaison d'intégration MSMQ qui convertit les messages MSMQ en messages [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et vice versa.</span><span class="sxs-lookup"><span data-stu-id="c6501-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="c6501-104">Cela vous permet d'appeler des applications réceptrices MSMQ depuis des clients [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ainsi que d'appeler les services [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] depuis des applications expéditrices MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6501-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="c6501-105">De cette section, nous vous expliquons comment utiliser <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> pour les communications mises en file d'attente entre (1) un client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et un service d'application MSMQ écrit à l'aide de System.Messaging et (2) un client d'application MSMQ et un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6501-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="c6501-106">Pour un exemple complet qui montre comment appeler une application de récepteur MSMQ à partir un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, consultez le [Windows Communication Foundation à Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="c6501-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="c6501-107">Pour un exemple complet qui montre comment appeler un [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de service à partir d’un client MSMQ, consultez le [Message Queuing pour Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="c6501-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="c6501-108">Pour créer un service WCF qui reçoit des messages depuis un client MSMQ</span><span class="sxs-lookup"><span data-stu-id="c6501-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="c6501-109">Configurez une interface qui définit le contrat de service pour le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui reçoit les messages mis en file d'attente depuis une application expéditrice MSMQ, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c6501-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="c6501-110">Implémentez l'interface et appliquez l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> à la classe, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c6501-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="c6501-111">Créez un fichier de configuration qui spécifie la liaison <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="c6501-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="c6501-112">Instanciez un objet <xref:System.ServiceModel.ServiceHost> qui utilise la liaison configurée.</span><span class="sxs-lookup"><span data-stu-id="c6501-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="c6501-113">Pour créer un client WCF qui envoie des messages à une application réceptrice MSMQ</span><span class="sxs-lookup"><span data-stu-id="c6501-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="c6501-114">Configurez une interface qui définit le contrat de service pour le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui envoie les messages mis en file d'attente au récepteur MSMQ, comme le montre l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c6501-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="c6501-115">Définissez une classe de client que le client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] utilise pour appeler le récepteur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="c6501-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="c6501-116">Créez une configuration qui spécifie l’utilisation de la liaison MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="c6501-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="c6501-117">Créez une instance de la classe de client et appelez la méthode définie par le service qui reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="c6501-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c6501-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6501-118">See Also</span></span>  
 [<span data-ttu-id="c6501-119">Vue d’ensemble des files d’attente</span><span class="sxs-lookup"><span data-stu-id="c6501-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="c6501-120">Guide pratique pour échanger des messages en file d’attente avec des points de terminaison WCF</span><span class="sxs-lookup"><span data-stu-id="c6501-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="c6501-121">Windows Communication Foundation vers Message Queuing</span><span class="sxs-lookup"><span data-stu-id="c6501-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="c6501-122">Installation de Message Queuing (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="c6501-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="c6501-123">Message Queuing vers Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c6501-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="c6501-124">Sécurité du message sur Message Queuing</span><span class="sxs-lookup"><span data-stu-id="c6501-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
