---
title: Utilisation de WS-AtomicTransaction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 124c5dc0f6db94ae459fe140bd7a4290aa56e04a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="74823-102">Utilisation de WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="74823-102">Using WS-AtomicTransaction</span></span>
<span data-ttu-id="74823-103">WS-AtomicTransaction (WS-AT) est un protocole de transaction interopérable.</span><span class="sxs-lookup"><span data-stu-id="74823-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="74823-104">Ce protocole vous permet de transférer des transactions distribuées à l’aide de messages de service Web et d’assurer la coordination d’infrastructures de transaction hétérogènes de manière interopérable.</span><span class="sxs-lookup"><span data-stu-id="74823-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="74823-105">WS-AT utilise un protocole de validation en deux phases pour un résultat atomique entre les applications distribuées, les gestionnaires de transactions et les gestionnaires de ressources.</span><span class="sxs-lookup"><span data-stu-id="74823-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="74823-106">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], pour permettre l'implémentation du protocole WS-AT, intègre un service de protocole au gestionnaire de transactions Microsoft Distributed Transaction Coordinator (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="74823-106">The WS-AT implementation [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="74823-107">Grâce au protocole WS-AT, les applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] peuvent transférer des transactions vers d'autres applications, notamment vers des services Web interopérables construits à l'aide de technologies tierces.</span><span class="sxs-lookup"><span data-stu-id="74823-107">Using WS-AT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="74823-108">Lorsqu’une transaction est transférée entre une application cliente et une application serveur, le protocole utilisé dépend de la liaison exposée par le serveur sur le point de terminaison sélectionné par le client.</span><span class="sxs-lookup"><span data-stu-id="74823-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="74823-109">Certaines liaisons définies par le système [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spécifient par défaut le protocole `OleTransactions` comme format de propagation de transaction, tandis que d'autres choisissent par défaut le protocole WS-AT.</span><span class="sxs-lookup"><span data-stu-id="74823-109">Some [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="74823-110">Vous pouvez également modifier le protocole de transaction utilisé par les liaisons en programmant le protocole de votre choix.</span><span class="sxs-lookup"><span data-stu-id="74823-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="74823-111">Le choix du protocole a des conséquences sur :</span><span class="sxs-lookup"><span data-stu-id="74823-111">The choice of protocol influences:</span></span>  
  
-   <span data-ttu-id="74823-112">Le format des en-têtes de message utilisé pour transférer la transaction du client au serveur.</span><span class="sxs-lookup"><span data-stu-id="74823-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
-   <span data-ttu-id="74823-113">Le protocole réseau utilisé pour exécuter le protocole de validation en deux phases entre le gestionnaire de transactions du client et la transaction du serveur et ainsi déterminer le résultat final de la transaction.</span><span class="sxs-lookup"><span data-stu-id="74823-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="74823-114">Si le serveur et le client ont été créés à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vous n'avez pas besoin d'utiliser le protocole WS-AT.</span><span class="sxs-lookup"><span data-stu-id="74823-114">If the server and client are written using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you do not need to use WS-AT.</span></span> <span data-ttu-id="74823-115">Il vous suffit en effet d'utiliser les paramètres par défaut de `NetTcpBinding` et d'activer l'attribut `TransactionFlow` pour que le protocole `OleTransactions` soit utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="74823-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="74823-116">[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="74823-116"> [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="74823-117">En revanche, si vous transférez des transactions vers des services Web construits à l’aide de technologies tierces, vous devez utiliser le protocole WS-AT.</span><span class="sxs-lookup"><span data-stu-id="74823-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74823-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74823-118">See Also</span></span>  
 [<span data-ttu-id="74823-119">Configuration de la prise en charge WS-Atomic Transaction</span><span class="sxs-lookup"><span data-stu-id="74823-119">Configuring WS-Atomic Transaction Support</span></span>](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
