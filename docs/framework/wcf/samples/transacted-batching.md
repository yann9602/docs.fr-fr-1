---
title: Transacted Batching
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dbd11f3dad60463a5650d7aa6e53f9e8f3f5021e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="transacted-batching"></a><span data-ttu-id="38bef-102">Transacted Batching</span><span class="sxs-lookup"><span data-stu-id="38bef-102">Transacted Batching</span></span>
<span data-ttu-id="38bef-103">Cet exemple montre comment traiter les lectures transactionnelles à l'aide de Message Queuing (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="38bef-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="38bef-104">Le traitement transactionnel par lots est une fonctionnalité d'optimisation des performances pour les lectures transactionnelles dans les communications mises en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38bef-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="38bef-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="38bef-106">Dans le cadre d'une communication en file d'attente, le client communique avec le service à l'aide d'une file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="38bef-107">Cela signifie que le client envoie ses messages à cette file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="38bef-108">Le service reçoit des messages de la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-108">The service receives messages from the queue.</span></span> <span data-ttu-id="38bef-109">Par conséquent, dans le cadre d'une communication en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="38bef-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="38bef-110">Cet exemple illustre le traitement transactionnel par lots.</span><span class="sxs-lookup"><span data-stu-id="38bef-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="38bef-111">Le traitement transactionnel par lots est un comportement qui permet l'utilisation d'une transaction unique lors de la lecture de nombreux messages dans la file d'attente et leur traitement.</span><span class="sxs-lookup"><span data-stu-id="38bef-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38bef-112">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="38bef-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="38bef-113">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bef-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="38bef-114">Si le service est exécuté en premier, il vérifie que la file d'attente existe.</span><span class="sxs-lookup"><span data-stu-id="38bef-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="38bef-115">Si la file d'attente n'existe pas, le service en crée une.</span><span class="sxs-lookup"><span data-stu-id="38bef-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="38bef-116">Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="38bef-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="38bef-117">Procédez comme suit pour créer une file d'attente dans Windows 2008 :</span><span class="sxs-lookup"><span data-stu-id="38bef-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="38bef-118">Ouvrez le Gestionnaire de serveur dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="38bef-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="38bef-119">Développez le **fonctionnalités** onglet.</span><span class="sxs-lookup"><span data-stu-id="38bef-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="38bef-120">Avec le bouton droit **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.</span><span class="sxs-lookup"><span data-stu-id="38bef-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="38bef-121">Vérifiez le **transactionnel** boîte.</span><span class="sxs-lookup"><span data-stu-id="38bef-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="38bef-122">Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38bef-123">Dans cet exemple, le client envoie des centaines de messages dans le cadre du lot.</span><span class="sxs-lookup"><span data-stu-id="38bef-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="38bef-124">Le traitement de ces messages par l'application du service peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="38bef-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="38bef-125">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bef-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="38bef-126">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38bef-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="38bef-127">Pour exécuter l'exemple sur un ordinateur joint à un groupe de travail ou sans intégration Active Directory</span><span class="sxs-lookup"><span data-stu-id="38bef-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="38bef-128">Avec <xref:System.ServiceModel.NetMsmqBinding>, la sécurité du transport est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="38bef-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="38bef-129">Il existe deux propriétés pertinentes pour la sécurité de transport MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> et <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` par défaut, le mode d’authentification a la valeur `Windows` et le niveau de protection a la valeur `Sign`.</span><span class="sxs-lookup"><span data-stu-id="38bef-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="38bef-130">Pour que MSMQ fournisse la fonctionnalité d’authentification et de signature, il doit faire partie d’un domaine et l’option d’intégration d’Active Directory doit être installée pour MSMQ.</span><span class="sxs-lookup"><span data-stu-id="38bef-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="38bef-131">Si vous exécutez cet exemple sur un ordinateur qui ne satisfait pas ces critères vous recevez une erreur.</span><span class="sxs-lookup"><span data-stu-id="38bef-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="38bef-132">Si votre ordinateur ne fait pas partie d'un domaine ou ne dispose pas de l'intégration Active Directory, désactivez la sécurité de transport en affectant au mode d'authentification et niveau de protection la valeur `None` comme indiqué dans l'exemple de configuration suivant :</span><span class="sxs-lookup"><span data-stu-id="38bef-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="38bef-133">Assurez-vous de modifier la configuration sur le serveur et le client avant d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="38bef-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38bef-134">L'affectation de `security``mode` à `None` revient à affecter <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> à la sécurité <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, `Message` et `None`.</span><span class="sxs-lookup"><span data-stu-id="38bef-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="38bef-135">Pour exécuter la base de données sur un ordinateur distant, modifiez la chaîne de connexion pour qu'elle pointe vers l'ordinateur sur lequel se trouve la base de données.</span><span class="sxs-lookup"><span data-stu-id="38bef-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38bef-136">Spécifications</span><span class="sxs-lookup"><span data-stu-id="38bef-136">Requirements</span></span>  
 <span data-ttu-id="38bef-137">Pour exécuter cet exemple, MSMQ doit être installé et SQL ou SQL Express est requis.</span><span class="sxs-lookup"><span data-stu-id="38bef-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="38bef-138">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="38bef-138">Demonstrates</span></span>  
 <span data-ttu-id="38bef-139">L'exemple montre le comportement du traitement transactionnel par lots.</span><span class="sxs-lookup"><span data-stu-id="38bef-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="38bef-140">Le traitement transactionnel par lots est une fonctionnalité d'optimisation des performances fournie le transport de mise en file d'attente MSMQ.</span><span class="sxs-lookup"><span data-stu-id="38bef-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="38bef-141">Lorsque les transactions sont utilisées pour envoyer et recevoir des messages il y a en fait 2 transactions distinctes.</span><span class="sxs-lookup"><span data-stu-id="38bef-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="38bef-142">Lorsque le client envoie des messages dans l'étendue d'une transaction, la transaction est locale au client et au gestionnaire de files d'attente client.</span><span class="sxs-lookup"><span data-stu-id="38bef-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="38bef-143">Lorsque le service reçoit des messages dans l'étendue de la transaction, la transaction est locale au service et au gestionnaire de files d'attente de réception.</span><span class="sxs-lookup"><span data-stu-id="38bef-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="38bef-144">N'oubliez pas que le client et le service ne participent pas à la même transaction : ils utilisent des transactions différentes lorsqu'ils effectuent leurs opérations (comme l'envoi et la réception) avec la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="38bef-145">Dans cet exemple, nous utilisons une transaction unique pour l'exécution de plusieurs opérations de service.</span><span class="sxs-lookup"><span data-stu-id="38bef-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="38bef-146">Elle est utilisée uniquement en tant que fonctionnalité d’optimisation des performances et ne concerne pas la sémantique de l’application.</span><span class="sxs-lookup"><span data-stu-id="38bef-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="38bef-147">L’exemple est basé sur [transactionnel de liaison MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="38bef-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="38bef-148">Commentaires</span><span class="sxs-lookup"><span data-stu-id="38bef-148">Comments</span></span>  
 <span data-ttu-id="38bef-149">Dans cet exemple, le client envoie un lot de messages au service à partir de l'étendue d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="38bef-150">Pour afficher l'optimisation des performances, nous envoyons un grand nombre de messages ; dans ce cas, jusqu'à 2 500 messages.</span><span class="sxs-lookup"><span data-stu-id="38bef-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="38bef-151">Les messages envoyés à la file d'attente sont ensuite reçus par le service dans l'étendue de la transaction définie par le service.</span><span class="sxs-lookup"><span data-stu-id="38bef-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="38bef-152">Sans traitement par lots, cela provoque 2 500 transactions pour chaque appel de l'opération de service.</span><span class="sxs-lookup"><span data-stu-id="38bef-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="38bef-153">Ceci influe sur les performances du système.</span><span class="sxs-lookup"><span data-stu-id="38bef-153">This impacts performance of the system.</span></span> <span data-ttu-id="38bef-154">Étant donné que deux gestionnaires des ressources sont impliqués (la file d'attente MSMQ et la base de données `Orders`), chaque transaction est une transaction DTC.</span><span class="sxs-lookup"><span data-stu-id="38bef-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="38bef-155">Nous optimisons ceci par l'utilisation d'un nombre bien moins important de transactions en garantissant qu'un lot de messages et que les appels d'opération de service aient lieu dans la même transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="38bef-156">Pour utiliser la fonctionnalité de traitement par lots, il faut :</span><span class="sxs-lookup"><span data-stu-id="38bef-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="38bef-157">indiquer le comportement du traitement transactionnel par lots dans la configuration ;</span><span class="sxs-lookup"><span data-stu-id="38bef-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="38bef-158">indiquer la taille de lot en nombre de messages devant être lus au cours d'une transaction ;</span><span class="sxs-lookup"><span data-stu-id="38bef-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="38bef-159">indiquer le nombre maximal de lots simultanés à exécuter.</span><span class="sxs-lookup"><span data-stu-id="38bef-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="38bef-160">Dans cet exemple, nous affichons les gains de performance par la réduction du nombre de transactions en garantissant que 100 opérations de service sont appelées dans une même transaction avant de valider la transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="38bef-161">Le comportement de service définit un comportement d'opération avec la valeur `TransactionScopeRequired` affectée à `true`.</span><span class="sxs-lookup"><span data-stu-id="38bef-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="38bef-162">Ainsi, l'étendue de transaction qui est utilisée pour récupérer le message de la file d'attente est utilisée par tous les gestionnaires des ressources auxquels accède la méthode.</span><span class="sxs-lookup"><span data-stu-id="38bef-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="38bef-163">Dans cet exemple, nous utilisons une base de données classique pour stocker les informations de commande fournisseur contenues dans le message.</span><span class="sxs-lookup"><span data-stu-id="38bef-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="38bef-164">L'étendue de transaction garantie également que si la méthode lève une exception, le message est renvoyé dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="38bef-165">Sans définir ce comportement d'opération, un canal mis en file d'attente crée une transaction pour lire le message à partir de la file d'attente et le valide automatiquement avant qu'il soit distribué afin que si l'opération échoue, le message soit perdu.</span><span class="sxs-lookup"><span data-stu-id="38bef-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="38bef-166">Dans la plupart des cas, les opérations de service s'inscrivent dans la transaction utilisée pour lire le message à partir de la file d'attente, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38bef-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="38bef-167">Notez que `ReleaseServiceInstanceOnTransactionComplete` a la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="38bef-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="38bef-168">C'est une spécification importante pour le traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="38bef-168">This is an important requirement for batching.</span></span> <span data-ttu-id="38bef-169">La propriété `ReleaseServiceInstanceOnTransactionComplete` sur `ServiceBehaviorAttribute` indique que faire avec l'instance de service une fois la transaction terminée.</span><span class="sxs-lookup"><span data-stu-id="38bef-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="38bef-170">Par défaut, l'instance de service est diffusée lorsque la transaction est terminée.</span><span class="sxs-lookup"><span data-stu-id="38bef-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="38bef-171">La principale particularité du traitement par lots est l'utilisation d'une seule transaction pour lire et distribuer de nombreux messages dans la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="38bef-172">Par conséquent, la diffusion de l'instance de service provoque par conséquent la fin prématurée de la transaction, empêchant l'utilisation du traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="38bef-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="38bef-173">Si cette propriété a la valeur `true` et que le comportement du traitement transactionnel par lots est ajouté au point de terminaison, le comportement de la validation du traitement par lots lève une exception.</span><span class="sxs-lookup"><span data-stu-id="38bef-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  
  
```  
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```  
  
 <span data-ttu-id="38bef-174">La classe `Orders` encapsule le traitement de la commande.</span><span class="sxs-lookup"><span data-stu-id="38bef-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="38bef-175">Dans cet exemple, elle met à jour la base de données avec les informations du bon de commande.</span><span class="sxs-lookup"><span data-stu-id="38bef-175">In the sample, it updates the database with purchase order information.</span></span>  
  
```  
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```  
  
 <span data-ttu-id="38bef-176">Le comportement du traitement par lots et sa configuration sont spécifiés dans la configuration de l'application de service.</span><span class="sxs-lookup"><span data-stu-id="38bef-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="38bef-177">La taille de lot est une indication destinée au système.</span><span class="sxs-lookup"><span data-stu-id="38bef-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="38bef-178">Par exemple, si vous spécifiez une taille de lot de 20, alors 20 messages seront lus et distribués à l'aide d'une même transaction, puis cette dernière sera validée.</span><span class="sxs-lookup"><span data-stu-id="38bef-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="38bef-179">Mais il existe des cas où la transaction peut valider le lot avant que la taille de lot soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="38bef-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="38bef-180">Un délai d'attente est associé à chaque transaction ; il commence son cycle une fois la transaction créée.</span><span class="sxs-lookup"><span data-stu-id="38bef-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="38bef-181">Lorsque ce délai d'attente expire la transaction est abandonnée.</span><span class="sxs-lookup"><span data-stu-id="38bef-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="38bef-182">Ce délai d'attente peut toutefois expirer avant même que la taille de lot soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="38bef-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="38bef-183">Pour éviter de retraiter le lot à cause de l'abandon, `TransactedBatchingBehavior` vérifie le temps restant sur la transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="38bef-184">Si 80 % du délai d'attente de transaction sont utilisés, la transaction est validée.</span><span class="sxs-lookup"><span data-stu-id="38bef-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="38bef-185">S'il n'y a plus de messages dans la file d'attente, au lieu d'attendre que la taille de lot soit atteinte, la <xref:System.ServiceModel.Description.TransactedBatchingBehavior> valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="38bef-186">Le choix de la taille de lot dépend de votre application.</span><span class="sxs-lookup"><span data-stu-id="38bef-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="38bef-187">Si la taille de lot est trop petite, vous risquez de ne pas obtenir la performance désirée.</span><span class="sxs-lookup"><span data-stu-id="38bef-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="38bef-188">En revanche, si la taille de lot est trop grande, elle risque de diminuer les performances.</span><span class="sxs-lookup"><span data-stu-id="38bef-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="38bef-189">Par exemple, la transaction pourrait durer plus longtemps et verrouiller des enregistrements dans votre base de données ou la transaction pourrait se bloquer, ce qui entraînerait la restauration du lot et la nécessité de recommencer le travail.</span><span class="sxs-lookup"><span data-stu-id="38bef-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="38bef-190">Le client crée une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-190">The client creates a transaction scope.</span></span> <span data-ttu-id="38bef-191">La communication avec la file d'attente a lieu dans l'étendue de la transaction, entraînant son traitement en tant qu'une unité atomique dans laquelle tous les messages sont envoyés à la file d'attente ou aucun des messages n'est envoyé à la file d'attente.</span><span class="sxs-lookup"><span data-stu-id="38bef-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="38bef-192">La transaction est validée par l'appel de la méthode <xref:System.Transactions.TransactionScope.Complete%2A> sur l'étendue de la transaction.</span><span class="sxs-lookup"><span data-stu-id="38bef-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  
  
```  
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="38bef-193">Lorsque vous exécutez l'exemple, les activités du client et du service s'affichent dans leurs fenêtres de console respectives.</span><span class="sxs-lookup"><span data-stu-id="38bef-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="38bef-194">Vous pouvez voir le service recevoir des messages du client.</span><span class="sxs-lookup"><span data-stu-id="38bef-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="38bef-195">Appuyez sur ENTER dans chaque fenêtre de console pour arrêter le service et le client.</span><span class="sxs-lookup"><span data-stu-id="38bef-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="38bef-196">Notez qu'en raison de l'utilisation de la mise en file d'attente, il n'est pas nécessaire que le service et le client s'exécutent simultanément.</span><span class="sxs-lookup"><span data-stu-id="38bef-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="38bef-197">Vous pouvez exécuter le client, l'arrêter, puis démarrer le service et il recevra encore ses messages.</span><span class="sxs-lookup"><span data-stu-id="38bef-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="38bef-198">Vous pouvez voir une sortie en continu à mesure que les messages sont lus dans un lot et traités.</span><span class="sxs-lookup"><span data-stu-id="38bef-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="38bef-199">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38bef-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="38bef-200">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="38bef-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38bef-201">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="38bef-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38bef-202">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="38bef-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="38bef-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38bef-203">See Also</span></span>
