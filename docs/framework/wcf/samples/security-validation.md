---
title: Security Validation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 4e8e8ff9a99c362fb5e2a6f5ef1161f48df86ceb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-validation"></a><span data-ttu-id="c041a-102">Security Validation</span><span class="sxs-lookup"><span data-stu-id="c041a-102">Security Validation</span></span>
<span data-ttu-id="c041a-103">Cet exemple montre comment utiliser un comportement personnalisé pour valider des services sur un ordinateur afin de garantir qu'ils répondent à des critères spécifiques.</span><span class="sxs-lookup"><span data-stu-id="c041a-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="c041a-104">Dans cet exemple, les services sont validés par le comportement personnalisé en analysant chaque point de terminaison sur le service et en vérifiant s’ils contiennent des éléments de liaison sécurisés.</span><span class="sxs-lookup"><span data-stu-id="c041a-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="c041a-105">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c041a-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c041a-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c041a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="c041a-107">Comportement personnalisé de validation de point de terminaison</span><span class="sxs-lookup"><span data-stu-id="c041a-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="c041a-108">En ajoutant le code utilisateur à la méthode `Validate` contenue dans l'interface <xref:System.ServiceModel.Description.IServiceBehavior>, le comportement personnalisé peut être attribué à un service ou un point de terminaison pour effectuer des actions définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c041a-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="c041a-109">Le code suivant est utilisé pour parcourir chaque point de terminaison contenu dans un service et rechercher des liaisons sécurisées dans leurs collections de liaisons.</span><span class="sxs-lookup"><span data-stu-id="c041a-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="c041a-110">L'ajout du code suivant au fichier Web.config ajoute l'extension de comportement `serviceValidate` au service à reconnaître.</span><span class="sxs-lookup"><span data-stu-id="c041a-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="c041a-111">Une fois l'extension de comportement ajoutée au service, il est possible d'ajouter le comportement `endpointValidate` à la liste de comportements dans le fichier Web.config et donc, au service.</span><span class="sxs-lookup"><span data-stu-id="c041a-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c041a-112">Les comportements et leurs extensions ajoutés au fichier Web.config appliquent le comportement aux services individuels, tandis qu'en cas d'ajout au fichier Machine.config, ils appliquent le comportement à chaque service actif sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c041a-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c041a-113">Lors de l'ajout du comportement à tous les services, il est recommandé de sauvegarder le fichier Machine.config avant d'apporter toute modification.</span><span class="sxs-lookup"><span data-stu-id="c041a-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="c041a-114">Exécutez maintenant le client fourni dans le répertoire client\bin de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c041a-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="c041a-115">Une exception se produit avec le message suivant : « Le service demandé, "http://localhost/servicemodelsamples/service.svc" n'a pas pu être activé. »</span><span class="sxs-lookup"><span data-stu-id="c041a-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="c041a-116">Cette exception est attendue parce qu'un point de terminaison est considéré comme non sécurisé par le comportement de validation de point de terminaison et empêche le démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="c041a-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="c041a-117">Le comportement lève également une exception interne qui décrit quel point de terminaison n'est pas sécurisé et écrit un message à l'observateur d'événements du système sous la source « System.ServiceModel 4.0.0.0 » et la catégorie « WebHost ».</span><span class="sxs-lookup"><span data-stu-id="c041a-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="c041a-118">Il est également possible d'activer le suivi sur le service dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c041a-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="c041a-119">Cela permet à l'utilisateur de consulter les exceptions levées par le comportement de validation de point de terminaison en ouvrant les suivis du service à l'aide de l'outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="c041a-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="c041a-120">Pour consulter les messages d’exception de validation non réussie d’un point de terminaison dans l’observateur d’événements</span><span class="sxs-lookup"><span data-stu-id="c041a-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="c041a-121">Cliquez sur le **Démarrer** menu et sélectionnez **exécuter...** .</span><span class="sxs-lookup"><span data-stu-id="c041a-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="c041a-122">Type `eventvwr` et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c041a-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="c041a-123">Dans la fenêtre de l’Observateur d’événements, cliquez sur **Application**.</span><span class="sxs-lookup"><span data-stu-id="c041a-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="c041a-124">Double-cliquez sur l’événement « System.ServiceModel 4.0.0.0 » ajouté récemment sous la catégorie « WebHost » dans le **Application** fenêtre pour afficher les messages de point de terminaison non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="c041a-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c041a-125">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c041a-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c041a-126">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c041a-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c041a-127">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c041a-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c041a-128">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c041a-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c041a-129">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c041a-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c041a-130">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c041a-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c041a-131">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c041a-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c041a-132">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c041a-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="c041a-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c041a-133">See Also</span></span>  
 [<span data-ttu-id="c041a-134">Exemples d’analyse AppFabric</span><span class="sxs-lookup"><span data-stu-id="c041a-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
