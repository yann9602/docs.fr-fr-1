---
title: Stand-Alone Diagnostics Feed, exemple
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c95a2e1e1790633df77e7c4ecd6603e68321e478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="cd8b1-102">Stand-Alone Diagnostics Feed, exemple</span><span class="sxs-lookup"><span data-stu-id="cd8b1-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="cd8b1-103">Cet exemple illustre la création d'un flux RSS/Atom pour la syndication avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd8b1-103">This sample demonstrates how to create an RSS/Atom feed for syndication with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="cd8b1-104">Il s'agit d'un programme « Hello World » de base qui affiche l'essentiel du modèle objet et indique comment l'installer sur un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cd8b1-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span>  
  
 <span data-ttu-id="cd8b1-105">Les modèles de syndication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonctionnent comme des opérations de service qui renvoient un type de données spécifique (<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>).</span><span class="sxs-lookup"><span data-stu-id="cd8b1-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="cd8b1-106">Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="cd8b1-107">L'exemple de code suivant illustre le contrat utilisé.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-107">The following sample code shows the contract used.</span></span>  
  
```  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="cd8b1-108">L'opération `GetProcesses` est annotée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>, qui permet de contrôler la façon dont [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] distribue les demandes HTTP GET pour effectuer les opérations et spécifier le format des messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="cd8b1-109">Comme pour tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les flux de syndication peuvent être auto-hébergés dans toute application managée.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-109">Like any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="cd8b1-110">Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="cd8b1-111">La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="cd8b1-112">Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).</span><span class="sxs-lookup"><span data-stu-id="cd8b1-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="cd8b1-113">Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="cd8b1-114">Par exemple, vous pouvez consulter la sortie de ce service en naviguant jusqu'à http://localhost:8000/diagnostics/feed/?format=atom ou http://localhost:8000/diagnostics/feed/?format=rss dans un navigateur RSS tel qu'Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="cd8b1-115">Vous pouvez également utiliser le [comment le WCF Syndication objet modèle est mappé à Atom et RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire des données syndiquées et traiter à l’aide du code impératif.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd8b1-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="cd8b1-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cd8b1-117">Assurez-vous d’avoir l’autorisation de l’inscription de bonne adresse pour HTTP et HTTPS sur l’ordinateur comme expliqué dans l’ensemble des instructions de [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd8b1-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cd8b1-118">Générez la solution.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="cd8b1-119">Exécutez l'application console.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="cd8b1-120">Au cours de l'exécution de l'application console, naviguez jusqu'à http://localhost:8000/diagnostics/feed/?format=atom ou http://localhost:8000/diagnostics/feed/?format=rss à l'aide d'un navigateur RSS.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd8b1-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cd8b1-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd8b1-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cd8b1-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd8b1-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="cd8b1-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="cd8b1-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd8b1-125">See Also</span></span>  
 [<span data-ttu-id="cd8b1-126">Modèle de programmation HTTP Web WCF</span><span class="sxs-lookup"><span data-stu-id="cd8b1-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="cd8b1-127">Syndication WCF</span><span class="sxs-lookup"><span data-stu-id="cd8b1-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
