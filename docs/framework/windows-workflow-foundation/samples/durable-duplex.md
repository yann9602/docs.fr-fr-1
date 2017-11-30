---
title: Durable Duplex
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5426272f574619f8d7cf163d13e9b37cb23bf31f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="durable-duplex"></a><span data-ttu-id="609e2-102">Durable Duplex</span><span class="sxs-lookup"><span data-stu-id="609e2-102">Durable Duplex</span></span>
<span data-ttu-id="609e2-103">Cet exemple montre comment installer et configurer un échange de messages duplex durable à l'aide des activités de messagerie dans [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609e2-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="609e2-104">Un échange de messages duplex durable est un échange de messages bidirectionnel qui a lieu sur une longue période de temps.</span><span class="sxs-lookup"><span data-stu-id="609e2-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="609e2-105">La durée de vie de l'échange de messages peut être plus longue que la durée de vie du canal de communication et la durée de vie en mémoire des instances de service.</span><span class="sxs-lookup"><span data-stu-id="609e2-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="609e2-106">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="609e2-106">Sample Details</span></span>  
 <span data-ttu-id="609e2-107">Dans cet exemple, deux services [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] implémentés à l'aide de [!INCLUDE[wf2](../../../../includes/wf2-md.md)] sont configurés pour avoir un échange de messages duplex durable.</span><span class="sxs-lookup"><span data-stu-id="609e2-107">In this sample, two [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services implemented using [!INCLUDE[wf2](../../../../includes/wf2-md.md)] are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="609e2-108">L’échange de messages duplex durable est composé de deux messages unidirectionnels envoyés sur MSMQ et corrélés à l’aide [échange de contextes .NET](http://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="609e2-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](http://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="609e2-109">Les messages sont envoyés à l'aide des activités de messagerie <xref:System.ServiceModel.Activities.Send> et <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="609e2-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="609e2-110">L'échange de contextes .NET est utilisé pour spécifier l'adresse de rappel sur les messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="609e2-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="609e2-111">Les deux services sont hébergés à l'aide des services d'activation des processus Windows (WAS, Windows Process Activation Services) et sont configurés pour activer la persistance des instances de service.</span><span class="sxs-lookup"><span data-stu-id="609e2-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="609e2-112">Le premier service (Service1.xamlx) envoie une demande au service d'envoi (Service2.xamlx) pour qu'il effectue un travail.</span><span class="sxs-lookup"><span data-stu-id="609e2-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="609e2-113">Une fois le travail terminé, Service2.xamlx renvoie une notification à Service1.xamlx pour indiquer que le travail a été effectué.</span><span class="sxs-lookup"><span data-stu-id="609e2-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="609e2-114">Une application console de workflow configure les files d'attente sur lesquelles les services effectuent une écoute et envoie le message de démarrage initial pour activer Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="609e2-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="609e2-115">Une fois que Service1.xamlx reçoit de Service2.xamlx la notification indiquant que le travail demandé a été effectué, il enregistre le résultat dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="609e2-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="609e2-116">En attendant le message de rappel, Service1.xamlx rend l'état de son instance persistant à l'aide du <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> par défaut.</span><span class="sxs-lookup"><span data-stu-id="609e2-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="609e2-117">Service2.xamlx rend l'état de son instance persistant dans le cadre de l'exécution du travail demandé par Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="609e2-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="609e2-118">Pour configurer les services afin d'utiliser l'échange de contextes .NET sur MSMQ, les deux services sont configurés pour utiliser une liaison personnalisée composée de <xref:System.ServiceModel.Channels.ContextBindingElement> et de <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="609e2-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="609e2-119">Une adresse de rappel, spécifiée avec <xref:System.ServiceModel.Channels.ContextBindingElement>, est incluse dans un en-tête de contexte de rappel avec tous les messages envoyés à l'aide d'une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="609e2-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="609e2-120">L'exemple de code suivant définit la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="609e2-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="609e2-121">La liaison utilisée par cet exemple n'est pas sécurisée.</span><span class="sxs-lookup"><span data-stu-id="609e2-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="609e2-122">Lors du déploiement de votre application, vous devez configurer votre liaison en fonction des spécifications de sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="609e2-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="609e2-123">Les files d’attente utilisées dans cet exemple ne sont pas transactionnelles.</span><span class="sxs-lookup"><span data-stu-id="609e2-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="609e2-124">Pour obtenir un exemple qui montre comment configurer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l’aide de files d’attente de transaction des échanges de messages, consultez le [d’Activation MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) exemple.</span><span class="sxs-lookup"><span data-stu-id="609e2-124">For a sample that shows how to set up [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="609e2-125">L’envoi du message de Service1.xamlx à Service2.xamlx s’effectue à l’aide d’un point de terminaison client configuré avec l’adresse de Service2.xamlx et la liaison personnalisée définie précédemment.</span><span class="sxs-lookup"><span data-stu-id="609e2-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="609e2-126">Le rappel de Service2.xamlx à Service1.xamlx est envoyé à l'aide d'un point de terminaison client sans adresse explicitement configurée car l'adresse provient du contexte de rappel envoyé par Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="609e2-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="609e2-127">L'exemple de code suivant définit les points de terminaison clients.</span><span class="sxs-lookup"><span data-stu-id="609e2-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="609e2-128">L'exemple de code suivant expose les points de terminaison à l'aide de cette liaison personnalisée en modifiant le mappage de protocole par défaut pour les adresses de base net.msmq afin d'utiliser cette liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="609e2-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="609e2-129">L'exemple de code suivant active la persistance pour les deux services en ajoutant le comportement <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> aux deux services et en spécifiant la chaîne de connexion pour la base de données de persistance.</span><span class="sxs-lookup"><span data-stu-id="609e2-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="609e2-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="609e2-130">System Requirements</span></span>  
 <span data-ttu-id="609e2-131">Cet exemple requiert les composants suivants.</span><span class="sxs-lookup"><span data-stu-id="609e2-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="609e2-132">Services Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="609e2-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="609e2-133">Services Internet (IIS) -> Compatibilité avec la gestion IIS 6 -> Compatibilité avec la métabase IIS et la configuration IIS 6.</span><span class="sxs-lookup"><span data-stu-id="609e2-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="609e2-134">Services World Wide Web -> Fonctionnalités de développement d'applications -> ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="609e2-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="609e2-135">Serveur de mise en file d'attente Microsoft (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="609e2-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="609e2-136">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="609e2-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="609e2-137">Configurez la base de données de persistance et le répertoire de résultats.</span><span class="sxs-lookup"><span data-stu-id="609e2-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="609e2-138">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609e2-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="609e2-139">Accédez au dossier de cet exemple et exécutez Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="609e2-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="609e2-140">Configurez l'application virtuelle.</span><span class="sxs-lookup"><span data-stu-id="609e2-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="609e2-141">À partir d'une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], inscrivez ASP.NET en exécutant la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="609e2-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="609e2-142">Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] avec des autorisations d’administrateur en cliquant sur [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="609e2-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="609e2-143">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier DurableDuplex.sln.</span><span class="sxs-lookup"><span data-stu-id="609e2-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="609e2-144">Configurez les files d'attente de service.</span><span class="sxs-lookup"><span data-stu-id="609e2-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="609e2-145">Pour exécuter le client DurableDuplex, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="609e2-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="609e2-146">Ouvrez le **gestion de l’ordinateur** console en exécutant `Compmgmt.msc` à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="609e2-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="609e2-147">Développez **services et Applications**, **Message Queuing**.</span><span class="sxs-lookup"><span data-stu-id="609e2-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="609e2-148">**Files d’attente privées**.</span><span class="sxs-lookup"><span data-stu-id="609e2-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="609e2-149">Les files d’attente durableduplex/Service1.xamlx et durableduplex/service2.xamlx d’avec le bouton droit et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="609e2-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="609e2-150">Sélectionnez le **sécurité** onglet et autoriser **recevoir un Message**, **lire le Message** et **envoyer un Message** autorisations pour les deux files d’attente.</span><span class="sxs-lookup"><span data-stu-id="609e2-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="609e2-151">Ouvrez le Gestionnaire des services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="609e2-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="609e2-152">Accédez à **Server**, **Sites**, **site Web par défaut**, **privé**, **Durable Duplex** et sélectionnez **Des Options avancées**.</span><span class="sxs-lookup"><span data-stu-id="609e2-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="609e2-153">Modifier la **protocoles activés** à **HTTP, NET.MSMQ**.</span><span class="sxs-lookup"><span data-stu-id="609e2-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="609e2-154">Exécutez l'exemple.</span><span class="sxs-lookup"><span data-stu-id="609e2-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="609e2-155">Accédez à http://localhost/private/durableduplex/service1.xamlx et http://localhost/private/durableduplex/service2.xamlx pour vérifier que les deux services sont en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="609e2-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="609e2-156">Appuyez sur F5 pour exécuter DurableDuplexClient.</span><span class="sxs-lookup"><span data-stu-id="609e2-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="609e2-157">Lorsque l'échange de messages duplex durable se termine, un fichier result.xml, qui contient le résultat de l'échange de messages, est enregistré dans le dossier C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="609e2-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="609e2-158">Pour effectuer un nettoyage (facultatif)</span><span class="sxs-lookup"><span data-stu-id="609e2-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="609e2-159">Exécutez Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="609e2-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="609e2-160">Ouvrez une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609e2-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="609e2-161">Accédez au dossier de cet exemple et exécutez Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="609e2-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="609e2-162">Supprimez l'application virtuelle pour les services.</span><span class="sxs-lookup"><span data-stu-id="609e2-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="609e2-163">Ouvrez le Gestionnaire Internet Information Services (IIS) en exécutant `Inetmgr.exe` à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="609e2-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="609e2-164">Accédez au site Web par défaut et supprimez le **privé** répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="609e2-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="609e2-165">Supprimez les files d'attente configurées pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="609e2-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="609e2-166">Ouvrez la console de gestion de l’ordinateur en exécutant `Compmgmt.msc` à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="609e2-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="609e2-167">Développez **services et Applications**, **Message Queuing**, **files d’attente privées**.</span><span class="sxs-lookup"><span data-stu-id="609e2-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="609e2-168">Supprimez les files d'attente durableduplex/service1.xamlx et durableduplex/service2.xamlx.</span><span class="sxs-lookup"><span data-stu-id="609e2-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="609e2-169">Supprimez le répertoire C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="609e2-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="609e2-170">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="609e2-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="609e2-171">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="609e2-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="609e2-172">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="609e2-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="609e2-173">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="609e2-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`  
  
## <a name="see-also"></a><span data-ttu-id="609e2-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="609e2-174">See Also</span></span>
