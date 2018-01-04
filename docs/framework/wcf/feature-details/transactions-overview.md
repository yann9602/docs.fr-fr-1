---
title: Vue d'ensemble des transactions Windows Communication Foundation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fb90d0f93e9bdf7dd9779ffd5d4b1288ba56e7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a><span data-ttu-id="29fa6-102">Vue d’ensemble des transactions Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="29fa6-102">Windows Communication Foundation Transactions Overview</span></span>
<span data-ttu-id="29fa6-103">Les transactions permettent de regrouper un ensemble d’actions ou d’opérations dans une unité d’exécution unique et indivisible.</span><span class="sxs-lookup"><span data-stu-id="29fa6-103">Transactions provide a way to group a set of actions or operations into a single indivisible unit of execution.</span></span> <span data-ttu-id="29fa6-104">Une transaction est une collection d'opérations avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="29fa6-104">A transaction is a collection of operations with the following properties:</span></span>  
  
-   <span data-ttu-id="29fa6-105">Atomicité.</span><span class="sxs-lookup"><span data-stu-id="29fa6-105">Atomicity.</span></span> <span data-ttu-id="29fa6-106">Cela garantit que toutes les mises à jour effectuées sous une transaction spécifique sont validées et rendues durable ou qu'elles sont toutes interrompues et rétablies à leur état précédent.</span><span class="sxs-lookup"><span data-stu-id="29fa6-106">This ensures that either all of the updates completed under a specific transaction are committed and made durable or they are all aborted and rolled back to their previous state.</span></span>  
  
-   <span data-ttu-id="29fa6-107">Cohérence.</span><span class="sxs-lookup"><span data-stu-id="29fa6-107">Consistency.</span></span> <span data-ttu-id="29fa6-108">Cela garantit que les modifications effectuées sous une transaction représentent une transformation d'un état cohérent à un autre.</span><span class="sxs-lookup"><span data-stu-id="29fa6-108">This guarantees that the changes made under a transaction represent a transformation from one consistent state to another.</span></span> <span data-ttu-id="29fa6-109">Par exemple, une transaction qui transfère de l'argent d'un compte chèques à un compte épargne ne modifie pas la somme d'argent dans le compte bancaire global.</span><span class="sxs-lookup"><span data-stu-id="29fa6-109">For example, a transaction that transfers money from a checking account to a savings account does not change the amount of money in the overall bank account.</span></span>  
  
-   <span data-ttu-id="29fa6-110">Isolement</span><span class="sxs-lookup"><span data-stu-id="29fa6-110">Isolation.</span></span> <span data-ttu-id="29fa6-111">Cela empêche une transaction d'observer des modifications non validées appartenant à d'autres transactions simultanées.</span><span class="sxs-lookup"><span data-stu-id="29fa6-111">This prevents a transaction from observing uncommitted changes belonging to other concurrent transactions.</span></span> <span data-ttu-id="29fa6-112">L'isolation fournit une abstraction de l'accès concurrentiel tout en garantissant qu'une transaction ne peut pas avoir d'impact inattendu sur l'exécution d'une autre transaction.</span><span class="sxs-lookup"><span data-stu-id="29fa6-112">Isolation provides an abstraction of concurrency while ensuring one transaction cannot have an unexpected impact on the execution of another transaction.</span></span>  
  
-   <span data-ttu-id="29fa6-113">Durabilité.</span><span class="sxs-lookup"><span data-stu-id="29fa6-113">Durability.</span></span> <span data-ttu-id="29fa6-114">Cela signifie qu'une fois validées, les mises à jour des ressources managées (telles qu'un enregistrement de base de données) seront persistantes en cas de défaillance.</span><span class="sxs-lookup"><span data-stu-id="29fa6-114">This means that once committed, updates to managed resources (such as a database record) will be persistent in the face of failures.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="29fa6-115"> fournit un riche ensemble de fonctionnalités qui vous permettent de créer des transactions distribuées dans votre application de service Web.</span><span class="sxs-lookup"><span data-stu-id="29fa6-115"> provides a rich set of features that enable you to create distributed transactions in your Web service application.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="29fa6-116"> implémente la prise en charge du protocole WS-AtomicTransaction (WS-AT) qui permet aux applications [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] de transférer des transactions aux applications interopérables, telles que les services Web interopérables générés à l'aide d'une technologie tierce.</span><span class="sxs-lookup"><span data-stu-id="29fa6-116"> implements support for the WS-AtomicTransaction (WS-AT) protocol that enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to flow transactions to interoperable applications, such as interoperable Web services built using third-party technology.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="29fa6-117"> implémente également la prise en charge du protocole OLE Transactions, qui peut être utilisé dans des scénarios où vous n'avez pas besoin de fonctionnalités d'interopérabilité pour activer le flux de transaction.</span><span class="sxs-lookup"><span data-stu-id="29fa6-117"> also implements support for the OLE Transactions protocol, which can be used in scenarios where you do not need interop functionality to enable transaction flow.</span></span>  
  
 <span data-ttu-id="29fa6-118">Vous pouvez utiliser un fichier de configuration d'application pour configurer des liaisons afin d'activer ou de désactiver le flux de transaction, ainsi que pour définir le protocole de transaction souhaité sur une liaison.</span><span class="sxs-lookup"><span data-stu-id="29fa6-118">You can use an application configuration file to configure bindings to enable or disable transaction flow, as well as set the desired transaction protocol on a binding.</span></span> <span data-ttu-id="29fa6-119">De plus, vous pouvez définir des délais d’expiration de transaction au niveau du service à l’aide du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="29fa6-119">In addition, you can set transaction time-outs at the service level using the configuration file.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="29fa6-120">[Activation du flux de Transaction](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="29fa6-120"> [Enabling Transaction Flow](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
 <span data-ttu-id="29fa6-121">Les attributs de transaction dans l'espace de noms <xref:System.ServiceModel> vous permettent d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="29fa6-121">Transaction attributes in the <xref:System.ServiceModel> namespace allow you to do the following:</span></span>  
  
-   <span data-ttu-id="29fa6-122">configurer des délais d'expiration de transaction et un filtrage de niveau isolation à l'aide de l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> ;</span><span class="sxs-lookup"><span data-stu-id="29fa6-122">Configure transaction time-outs and isolation-level filtering using the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="29fa6-123">activer la fonctionnalité de transactions et configurer le comportement de fin de transaction à l'aide de l'attribut <xref:System.ServiceModel.OperationBehaviorAttribute> ;</span><span class="sxs-lookup"><span data-stu-id="29fa6-123">Enable transactions functionality and configure transaction completion behavior using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span>  
  
-   <span data-ttu-id="29fa6-124">utiliser les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> sur une méthode de contrat pour exiger, autoriser ou refuser le flux de transaction.</span><span class="sxs-lookup"><span data-stu-id="29fa6-124">Use the <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> attributes on a contract method to require, allow or deny transaction flow.</span></span>  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="29fa6-125">[Attributs de Transaction ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="29fa6-125"> [ServiceModel Transaction Attributes](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29fa6-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29fa6-126">See Also</span></span>  
 [<span data-ttu-id="29fa6-127">Attributs de transaction ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29fa6-127">ServiceModel Transaction Attributes</span></span>](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [<span data-ttu-id="29fa6-128">Activation du flux de transaction</span><span class="sxs-lookup"><span data-stu-id="29fa6-128">Enabling Transaction Flow</span></span>](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
