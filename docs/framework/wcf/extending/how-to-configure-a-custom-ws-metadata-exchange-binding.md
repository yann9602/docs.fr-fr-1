---
title: "Comment : configurer une liaison WS-Metadata Exchange personnalisée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-Metadata Exchange [WCF]
- WS-Metadata Exchange [WCF], configuring a custom binding
ms.assetid: cdba4d73-da64-4805-bc56-9822becfd1e4
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4202c0471c681257fa1ab1153d363e59615e10c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-custom-ws-metadata-exchange-binding"></a><span data-ttu-id="af42a-102">Comment : configurer une liaison WS-Metadata Exchange personnalisée</span><span class="sxs-lookup"><span data-stu-id="af42a-102">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>
<span data-ttu-id="af42a-103">Cette rubrique explique comment configurer une liaison d’échange WS-Metadata personnalisée.</span><span class="sxs-lookup"><span data-stu-id="af42a-103">This topic will explain how to configure a custom WS-Metadata exchange binding.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="af42a-104"> inclut quatre liaisons de métadonnées définies par le système, mais vous pouvez publier des métadonnées à l'aide de la liaison de votre choix.</span><span class="sxs-lookup"><span data-stu-id="af42a-104"> includes four system-defined metadata bindings, but you can publish metadata using any binding you want.</span></span> <span data-ttu-id="af42a-105">Cette rubrique indique comment publier des métadonnées à l'aide du `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="af42a-105">This topic will show you how to publish metadata using the `wsHttpBinding`.</span></span> <span data-ttu-id="af42a-106">Cette liaison vous donne la possibilité d’exposer des métadonnées de manière sécurisée.</span><span class="sxs-lookup"><span data-stu-id="af42a-106">This binding gives you the option of exposing metadata in a secure way.</span></span> <span data-ttu-id="af42a-107">Le code dans cet article est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="af42a-107">The code in this article is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
### <a name="using-a-configuration-file"></a><span data-ttu-id="af42a-108">Utilisation d'un fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="af42a-108">Using a configuration file</span></span>  
  
1.  <span data-ttu-id="af42a-109">Dans le fichier de configuration du service, ajoutez un comportement de service qui contient la balise `serviceMetadata` :</span><span class="sxs-lookup"><span data-stu-id="af42a-109">In the service's configuration file, add a service behavior that contains the `serviceMetadata` tag:</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
           <serviceMetadata httpGetEnabled="True"/>  
         </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="af42a-110">Ajoutez un attribut `behaviorConfiguration` à la balise de service qui référence ce nouveau comportement :</span><span class="sxs-lookup"><span data-stu-id="af42a-110">Add a `behaviorConfiguration` attribute to the service tag that references this new behavior:</span></span>  
  
    ```xml  
    <service        name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">   
    ```  
  
3.  <span data-ttu-id="af42a-111">Ajoutez un point de terminaison de métadonnées qui spécifie mex comme adresse, `wsHttpBinding` comme liaison et <xref:System.ServiceModel.Description.IMetadataExchange> comme contrat :</span><span class="sxs-lookup"><span data-stu-id="af42a-111">Add a metadata endpoint specifying mex as the address, `wsHttpBinding` as the binding, and <xref:System.ServiceModel.Description.IMetadataExchange> as the contract:</span></span>  
  
    ```xml  
    <endpoint address="mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange" />  
    ```  
  
4.  <span data-ttu-id="af42a-112">Pour vérifier que le point de terminaison d'échange de métadonnées fonctionne correctement, ajoutez une balise de point de terminaison dans le fichier de configuration de client :</span><span class="sxs-lookup"><span data-stu-id="af42a-112">To verify the metadata exchange endpoint is working correctly add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
5.  <span data-ttu-id="af42a-113">Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à sa propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :</span><span class="sxs-lookup"><span data-stu-id="af42a-113">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set its <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
### <a name="configuring-by-code"></a><span data-ttu-id="af42a-114">Configuration par code</span><span class="sxs-lookup"><span data-stu-id="af42a-114">Configuring by code</span></span>  
  
1.  <span data-ttu-id="af42a-115">Créer un <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> instance de liaison :</span><span class="sxs-lookup"><span data-stu-id="af42a-115">Create a <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> binding instance:</span></span>  
  
    ```  
    WSHttpBinding binding = new WSHttpBinding();  
    ```  
  
2.  <span data-ttu-id="af42a-116">Créez une instance <xref:System.ServiceModel.ServiceHost> :</span><span class="sxs-lookup"><span data-stu-id="af42a-116">Create a <xref:System.ServiceModel.ServiceHost> instance:</span></span>  
  
    ```  
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
    ```  
  
3.  <span data-ttu-id="af42a-117">Ajoutez un point de terminaison de service et ajoutez une instance <xref:System.ServiceModel.Description.ServiceMetadataBehavior> :</span><span class="sxs-lookup"><span data-stu-id="af42a-117">Add a service endpoint and add a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(ICalculator), binding, baseAddress);  
    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
    smb.HttpGetEnabled = true;  
    serviceHost.Description.Behaviors.Add(smb);  
    ```  
  
4.  <span data-ttu-id="af42a-118">Ajouter un point de terminaison d’échange de métadonnées, en spécifiant le <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> créé précédemment :</span><span class="sxs-lookup"><span data-stu-id="af42a-118">Add a metadata exchange endpoint, specifying the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> created earlier:</span></span>  
  
    ```  
    serviceHost.AddServiceEndpoint(typeof(IMetadataExchange), binding, mexAddress);  
    ```  
  
5.  <span data-ttu-id="af42a-119">Pour vérifier que le point de terminaison d’échange de métadonnées fonctionne correctement, ajoutez une étiquette de point de terminaison dans le fichier de configuration de client :</span><span class="sxs-lookup"><span data-stu-id="af42a-119">To verify that the metadata exchange endpoint is working correctly, add an endpoint tag in the client configuration file:</span></span>  
  
    ```xml  
    <endpoint name="MyMexEndpoint"               address="http://localhost:8000/servicemodelsamples/service/mex"  
              binding="wsHttpBinding"  
              contract="IMetadataExchange"/>  
    ```  
  
6.  <span data-ttu-id="af42a-120">Dans la méthode Main() du client, créez une instance <xref:System.ServiceModel.Description.MetadataExchangeClient>, affectez à la propriété <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> la valeur `true`, appelez <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A>, puis effectuez une itération au sein de la collection de métadonnées retournée :</span><span class="sxs-lookup"><span data-stu-id="af42a-120">In the client's Main() method, create a new <xref:System.ServiceModel.Description.MetadataExchangeClient> instance, set the <xref:System.ServiceModel.Description.MetadataExchangeClient.ResolveMetadataReferences%2A> property to `true`, call <xref:System.ServiceModel.Description.MetadataExchangeClient.GetMetadata%2A> and then iterate through the collection of metadata returned:</span></span>  
  
    ```  
    string mexAddress = "http://localhost:8000/servicemodelsamples/service/mex";  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("MyMexEndpoint");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mdSet = mexClient.GetMetadata(new EndpointAddress(mexAddress));  
    foreach (MetadataSection section in mdSet.MetadataSections)  
    Console.WriteLine("Metadata section: " + section.Dialect.ToString());  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="af42a-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af42a-121">See Also</span></span>  
 [<span data-ttu-id="af42a-122">Comportement de publication des métadonnées</span><span class="sxs-lookup"><span data-stu-id="af42a-122">Metadata Publishing Behavior</span></span>](../../../../docs/framework/wcf/samples/metadata-publishing-behavior.md)  
 [<span data-ttu-id="af42a-123">Récupérer des métadonnées</span><span class="sxs-lookup"><span data-stu-id="af42a-123">Retrieve Metadata</span></span>](../../../../docs/framework/wcf/samples/retrieve-metadata.md)  
 [<span data-ttu-id="af42a-124">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="af42a-124">Metadata</span></span>](../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="af42a-125">Publication des métadonnées</span><span class="sxs-lookup"><span data-stu-id="af42a-125">Publishing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)  
 [<span data-ttu-id="af42a-126">Publication de points de terminaison de métadonnées</span><span class="sxs-lookup"><span data-stu-id="af42a-126">Publishing Metadata Endpoints</span></span>](../../../../docs/framework/wcf/publishing-metadata-endpoints.md)
