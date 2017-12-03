---
title: "Filtres avancés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 988c41bb691d27e819710bbc2cd48bc1c844e7c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-filters"></a><span data-ttu-id="a965f-102">Filtres avancés</span><span class="sxs-lookup"><span data-stu-id="a965f-102">Advanced Filters</span></span>
<span data-ttu-id="a965f-103">Cet exemple illustre un service de routage [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a965f-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="a965f-104">Le service de routage est un composant [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] qui facilite l'inclusion d'un routeur basé sur le contenu dans votre application.</span><span class="sxs-lookup"><span data-stu-id="a965f-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="a965f-105">Cet exemple adapte l'exemple [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator standard pour communiquer à l'aide du service de routage.</span><span class="sxs-lookup"><span data-stu-id="a965f-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="a965f-106">Il montre comment définir une logique de routage basé sur le contenu via l'utilisation de filtres de messages et de tables de filtres de messages.</span><span class="sxs-lookup"><span data-stu-id="a965f-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a965f-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a965f-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a965f-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a965f-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a965f-109">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a965f-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a965f-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a965f-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="a965f-111">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="a965f-111">Sample Details</span></span>  
 <span data-ttu-id="a965f-112">Le tableau suivant présente les filtres de messages qui sont ajoutés à la table de filtres de messages du service de routage.</span><span class="sxs-lookup"><span data-stu-id="a965f-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="a965f-113">Filtre</span><span class="sxs-lookup"><span data-stu-id="a965f-113">Filter</span></span>|<span data-ttu-id="a965f-114">Règle</span><span class="sxs-lookup"><span data-stu-id="a965f-114">Rule</span></span>|<span data-ttu-id="a965f-115">Priorité</span><span class="sxs-lookup"><span data-stu-id="a965f-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="a965f-116">If (has header) [contient un en-tête]</span><span class="sxs-lookup"><span data-stu-id="a965f-116">If (has header)</span></span>|<span data-ttu-id="a965f-117">Arrondi</span><span class="sxs-lookup"><span data-stu-id="a965f-117">Rounding</span></span>|<span data-ttu-id="a965f-118">2</span><span class="sxs-lookup"><span data-stu-id="a965f-118">2</span></span>|  
|<span data-ttu-id="a965f-119">If (showed up on Ep2) [apparu sur Ep2]</span><span class="sxs-lookup"><span data-stu-id="a965f-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="a965f-120">Normale</span><span class="sxs-lookup"><span data-stu-id="a965f-120">Regular</span></span>|<span data-ttu-id="a965f-121">1</span><span class="sxs-lookup"><span data-stu-id="a965f-121">1</span></span>|  
|<span data-ttu-id="a965f-122">If (showed up with Address2) [apparu avec Address2]</span><span class="sxs-lookup"><span data-stu-id="a965f-122">If (showed up with Address2)</span></span>|<span data-ttu-id="a965f-123">Arrondi</span><span class="sxs-lookup"><span data-stu-id="a965f-123">Rounding</span></span>|<span data-ttu-id="a965f-124">1</span><span class="sxs-lookup"><span data-stu-id="a965f-124">1</span></span>|  
|<span data-ttu-id="a965f-125">If (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="a965f-125">If (RoundRobin1)</span></span>|<span data-ttu-id="a965f-126">Normale</span><span class="sxs-lookup"><span data-stu-id="a965f-126">Regular</span></span>|<span data-ttu-id="a965f-127">0</span><span class="sxs-lookup"><span data-stu-id="a965f-127">0</span></span>|  
|<span data-ttu-id="a965f-128">If (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="a965f-128">If (RoundRobin2)</span></span>|<span data-ttu-id="a965f-129">Arrondi</span><span class="sxs-lookup"><span data-stu-id="a965f-129">Rounding</span></span>|<span data-ttu-id="a965f-130">0</span><span class="sxs-lookup"><span data-stu-id="a965f-130">0</span></span>|  
  
 <span data-ttu-id="a965f-131">Les filtres de messages et tables de filtres de messages peuvent être créés et configurés au moyen d'un code ou dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="a965f-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="a965f-132">Pour cet exemple, vous trouverez les filtres de messages et tables de filtres de messages définis au moyen d'un code dans le fichier RoutingService\routing.cs ou définis dans le fichier de configuration de l'application dans le fichier RoutingService\App.config.</span><span class="sxs-lookup"><span data-stu-id="a965f-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="a965f-133">Les paragraphes suivants expliquent comment les filtres de messages et tables de filtres de messages sont créés pour cet exemple au moyen d'un code.</span><span class="sxs-lookup"><span data-stu-id="a965f-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="a965f-134">En premier lieu, un <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> recherche l'en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="a965f-135">Notez que <xref:System.ServiceModel.WSHttpBinding> aboutit à une version d'enveloppe utilisant SOAP 1.2, de sorte que l'instruction XPath est définie pour utiliser l'espace de noms SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="a965f-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="a965f-136">Le gestionnaire d'espaces de noms par défaut pour les filtres <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> définit déjà un préfixe pour l'espace de noms SOAP 1.2, /s12, qui peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="a965f-137">Toutefois, le gestionnaire d'espaces de noms par défaut ne possède pas l'espace de noms personnalisé que le client utilise pour définir la valeur d'en-tête réelle, aussi le préfixe doit-il être défini.</span><span class="sxs-lookup"><span data-stu-id="a965f-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="a965f-138">Tout message qui apparaît avec cet en-tête constitue une correspondance pour ce filtre.</span><span class="sxs-lookup"><span data-stu-id="a965f-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="a965f-139">Le deuxième filtre est un <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, qui accepte comme correspondance tout message ayant été reçu sur le `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="a965f-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="a965f-140">Le nom du point de terminaison est défini au moment de la création d'un objet de point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="a965f-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="a965f-141">Le troisième filtre est un <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="a965f-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="a965f-142">Il accepte comme correspondance tout message apparu sur un point de terminaison avec une adresse qui correspond au préfixe (ou première partie) d'adresse fourni.</span><span class="sxs-lookup"><span data-stu-id="a965f-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="a965f-143">Dans cet exemple, le préfixe d'adresse défini est "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="a965f-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="a965f-144">Cela signifie que ce filtre établit une correspondance avec tous les messages entrants adressés à "http://localhost/routingservice/router/rounding/*".</span><span class="sxs-lookup"><span data-stu-id="a965f-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/*" are matched by this filter.</span></span> <span data-ttu-id="a965f-145">Dans ce cas, il s'agit des messages qui apparaissent sur le point de terminaison Rounding Calculator, dont l'adresse est "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="a965f-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="a965f-146">Les deux derniers filtres de messages sont <xref:System.ServiceModel.Dispatcher.MessageFilter> personnalisés.</span><span class="sxs-lookup"><span data-stu-id="a965f-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="a965f-147">Dans cet exemple, un filtre de messages « RoundRobin » est utilisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="a965f-148">Ce filtre de messages est créé dans le fichier RoutingService\RoundRobinMessageFilter.cs fourni.</span><span class="sxs-lookup"><span data-stu-id="a965f-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="a965f-149">Ces filtres, lorsqu'ils sont définis sur le même groupe, signalent alternativement qu'ils acceptent et n'acceptent pas le message comme une correspondance, de sorte qu'un seul d'entre eux à la fois répond `true`.</span><span class="sxs-lookup"><span data-stu-id="a965f-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="a965f-150">Ensuite, tous ces messages sont ajoutés à un <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="a965f-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="a965f-151">Pour cela, des priorités sont établies afin d'influencer l'ordre dans lequel la table de filtres de messages exécute les filtres.</span><span class="sxs-lookup"><span data-stu-id="a965f-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="a965f-152">Plus la priorité est élevée, plus le filtre est exécuté tôt ; plus la priorité est faible, plus le filtre est exécuté tard.</span><span class="sxs-lookup"><span data-stu-id="a965f-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="a965f-153">Un filtre de priorité 2 s'exécute donc avant un filtre de priorité 1.</span><span class="sxs-lookup"><span data-stu-id="a965f-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="a965f-154">Si aucun niveau de priorité n'est spécifié, le niveau par défaut, 0, est appliqué.</span><span class="sxs-lookup"><span data-stu-id="a965f-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="a965f-155">Une table de filtres de messages exécute tous les filtres d'un niveau de priorité donné avant de traiter le niveau de priorité inférieur suivant.</span><span class="sxs-lookup"><span data-stu-id="a965f-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="a965f-156">Si une correspondance est trouvée à une priorité particulière, la table de filtres de messages cesse de rechercher des correspondances au niveau de priorité inférieur.</span><span class="sxs-lookup"><span data-stu-id="a965f-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a965f-157">Si cet exemple indique comment utiliser des priorités de filtres de messages, il est généralement plus efficace et conforme aux bonnes pratiques de conception de concevoir et configurer vos filtres de sorte qu'ils ne nécessitent pas de priorités pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="a965f-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="a965f-158">Le premier filtre à ajouter est XPath, avec une priorité 2.</span><span class="sxs-lookup"><span data-stu-id="a965f-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="a965f-159">C'est le premier filtre de messages qui s'exécute.</span><span class="sxs-lookup"><span data-stu-id="a965f-159">This is the first message filter that executes.</span></span> <span data-ttu-id="a965f-160">S'il trouve l'en-tête personnalisé, quels que soient les résultats que produiraient les autres filtres, le message est routé vers le point de terminaison Rounding Calculator.</span><span class="sxs-lookup"><span data-stu-id="a965f-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="a965f-161">Au niveau de priorité 1, deux filtres sont ajoutés.</span><span class="sxs-lookup"><span data-stu-id="a965f-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="a965f-162">Là encore, ceux-ci ne s'exécutent que si le filtre XPath de priorité 2 ne trouve pas de message correspondant.</span><span class="sxs-lookup"><span data-stu-id="a965f-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="a965f-163">Ces deux filtres montrent deux façons différentes de déterminer où le message a été adressé lorsqu'il est apparu.</span><span class="sxs-lookup"><span data-stu-id="a965f-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="a965f-164">Étant donné que ces deux filtres vérifient en réalité si le message est arrivé à l'un des deux points de terminaison, ils peuvent être exécutés au même niveau de priorité, car ils ne retournent pas la valeur `true` tous les deux en même temps.</span><span class="sxs-lookup"><span data-stu-id="a965f-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="a965f-165">Enfin, au niveau de priorité 0 (priorité la plus faible), exécutez les filtres de messages RoundRobin.</span><span class="sxs-lookup"><span data-stu-id="a965f-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="a965f-166">Étant donné que les filtres sont configurés avec le même nom de groupe, un seul d'entre eux à la fois recherche des correspondances.</span><span class="sxs-lookup"><span data-stu-id="a965f-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="a965f-167">Comme tous les messages avec l'en-tête personnalisé ont été routés et adressés aux points de terminaison virtualisés spécifiques, les messages gérés par les filtres de messages RoundRobin sont uniquement ceux qui ont été adressés au point de terminaison de routeur par défaut (Default Router), sans l'en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="a965f-168">Étant donné que ces messages déclenchent un message pour chaque appel, la moitié des opérations va au point de terminaison Regular Calculator et l'autre moitié au point de terminaison Rounding Calculator.</span><span class="sxs-lookup"><span data-stu-id="a965f-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a965f-169">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="a965f-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="a965f-170">À l'aide de [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], ouvrez AdvancedFilters.sln.</span><span class="sxs-lookup"><span data-stu-id="a965f-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="a965f-171">Pour ouvrir **l’Explorateur de solutions**, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="a965f-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="a965f-172">Appuyez sur F5 ou CTRL+MAJ+B dans [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a965f-172">Press F5 or CTRL+SHIFT+B in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="a965f-173">Si vous souhaitez lancer automatiquement les projets nécessaires lorsque vous appuyez sur F5, cliquez sur la solution et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a965f-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="a965f-174">Sélectionnez le **projet de démarrage** nœud sous **propriétés communes** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="a965f-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="a965f-175">Sélectionnez le **plusieurs projets de démarrage** case d’option et tous les projets d’avoir défini la **Démarrer** action.</span><span class="sxs-lookup"><span data-stu-id="a965f-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="a965f-176">Si vous générez le projet avec CTRL+MAJ+B, vous devez démarrer les applications suivantes :</span><span class="sxs-lookup"><span data-stu-id="a965f-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="a965f-177">Client Calculator (./CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="a965f-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="a965f-178">Service Calculator (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a965f-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="a965f-179">Service Rounding Calculator (./RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a965f-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="a965f-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="a965f-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="a965f-181">Dans la fenêtre de console du client Calculator, appuyez sur ENTRÉE pour démarrer le client.</span><span class="sxs-lookup"><span data-stu-id="a965f-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="a965f-182">Le client retourne la liste des points de terminaison de destination possibles.</span><span class="sxs-lookup"><span data-stu-id="a965f-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="a965f-183">Choisissez un point de terminaison de destination en tapant la lettre qui lui est associée et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="a965f-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="a965f-184">Ensuite, le client vous demande si vous souhaitez ajouter un en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="a965f-185">Appuyez sur Y pour Oui ou N pour Non, puis sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="a965f-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="a965f-186">La sortie visible dépend des sélections que vous avez effectuées.</span><span class="sxs-lookup"><span data-stu-id="a965f-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="a965f-187">Voici la sortie retournée si vous avez ajouté un en-tête personnalisé aux messages.</span><span class="sxs-lookup"><span data-stu-id="a965f-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="a965f-188">Voici la sortie retournée si vous avez choisi le point de terminaison Rounding Calculator sans en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="a965f-189">Voici la sortie retournée si vous avez choisi le point de terminaison Regular Calculator sans en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="a965f-190">Voici la sortie retournée si vous avez choisi le point de terminaison Default Router sans en-tête personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a965f-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="a965f-191">Le service Calculator et le service Rounding Calculator génèrent également un journal des opérations appelé dans leur fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="a965f-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="a965f-192">Dans la fenêtre de console client, tapez `quit` et appuyez sur ENTRÉE pour quitter.</span><span class="sxs-lookup"><span data-stu-id="a965f-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="a965f-193">Appuyez sur ENTRÉE dans les fenêtres de console des services pour les arrêter.</span><span class="sxs-lookup"><span data-stu-id="a965f-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="a965f-194">Configurable au moyen d'un code ou d'un fichier App.config</span><span class="sxs-lookup"><span data-stu-id="a965f-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="a965f-195">L'exemple est fourni en étant configuré de façon à utiliser un fichier App.config pour définir le comportement du routeur.</span><span class="sxs-lookup"><span data-stu-id="a965f-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="a965f-196">Vous pouvez également renommer le fichier RoutingService\App.config afin qu'il ne soit pas reconnu et supprimer les marques de commentaire de l'appel de méthode à `ConfigureRouterViaCode()` dans RoutingService\routing.cs.</span><span class="sxs-lookup"><span data-stu-id="a965f-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="a965f-197">Quelle que soit la méthode employée, le comportement de routeur obtenu est le même.</span><span class="sxs-lookup"><span data-stu-id="a965f-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="a965f-198">Scénario</span><span class="sxs-lookup"><span data-stu-id="a965f-198">Scenario</span></span>  
 <span data-ttu-id="a965f-199">Cet exemple illustre l'utilisation du routeur en tant que routeur basé sur le contenu qui autorise l'exposition via un même point de terminaison de plusieurs types ou implémentations de services.</span><span class="sxs-lookup"><span data-stu-id="a965f-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="a965f-200">Scénario réel</span><span class="sxs-lookup"><span data-stu-id="a965f-200">Real World Scenario</span></span>  
 <span data-ttu-id="a965f-201">Contoso souhaite virtualiser tous ses services afin de n'exposer publiquement qu'un seul point de terminaison via lequel donner accès à différents types de services.</span><span class="sxs-lookup"><span data-stu-id="a965f-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="a965f-202">Dans ce cas, la société utilise les fonctions de routage basé sur le contenu du service de routage afin de déterminer l'endroit où doivent être envoyées les demandes entrantes.</span><span class="sxs-lookup"><span data-stu-id="a965f-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a965f-203">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a965f-203">See Also</span></span>  
 [<span data-ttu-id="a965f-204">Hébergement de AppFabric et exemples de persistance</span><span class="sxs-lookup"><span data-stu-id="a965f-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
