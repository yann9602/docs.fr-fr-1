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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89de6bcbb44ca70592697ccf891099446b230ce6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a>Stand-Alone Diagnostics Feed, exemple
Cet exemple illustre la création d'un flux RSS/Atom pour la syndication avec [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Il s'agit d'un programme « Hello World » de base qui affiche l'essentiel du modèle objet et indique comment l'installer sur un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
 Les modèles de syndication [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fonctionnent comme des opérations de service qui renvoient un type de données spécifique (<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>). Les instances de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> peuvent sérialiser un flux aux formats RSS 2.0 et Atom 1.0. L'exemple de code suivant illustre le contrat utilisé.  
  
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
  
 L'opération `GetProcesses` est annotée avec l'attribut <xref:System.ServiceModel.Web.WebGetAttribute>, qui permet de contrôler la façon dont [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] distribue les demandes HTTP GET pour effectuer les opérations et spécifier le format des messages envoyés.  
  
 Comme pour tout service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les flux de syndication peuvent être auto-hébergés dans toute application managée. Les services de syndication nécessitent une liaison spécifique (<xref:System.ServiceModel.WebHttpBinding>) et un comportement de point de terminaison spécifique (<xref:System.ServiceModel.Description.WebHttpBehavior>) afin de fonctionner correctement. La nouvelle classe <xref:System.ServiceModel.Web.WebServiceHost> fournit une API pratique pour créer ces points de terminaison sans configuration spécifique.  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 Vous pouvez aussi utiliser <xref:System.ServiceModel.Activation.WebServiceHostFactory> à partir d'un fichier .svc hébergé dans IIS pour fournir des fonctionnalités équivalentes (cette technique n'est pas démontrée dans cet exemple de code).  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 Ce service reçoit des demandes à l'aide d'une demande HTTP GET standard ; par conséquent, vous pouvez utiliser tout client RSS ou ATOM pour accéder au service. Par exemple, vous pouvez consulter la sortie de ce service en naviguant jusqu'à http://localhost:8000/diagnostics/feed/?format=atom ou http://localhost:8000/diagnostics/feed/?format=rss dans un navigateur RSS tel qu'Internet Explorer 7.  
  
 Vous pouvez également utiliser le [comment le WCF Syndication objet modèle est mappé à Atom et RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pour lire des données syndiquées et traiter à l’aide du code impératif.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez-vous d’avoir l’autorisation de l’inscription de bonne adresse pour HTTP et HTTPS sur l’ordinateur comme expliqué dans l’ensemble des instructions de [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Générez la solution.  
  
3.  Exécutez l'application console.  
  
4.  Au cours de l'exécution de l'application console, naviguez jusqu'à http://localhost:8000/diagnostics/feed/?format=atom ou http://localhost:8000/diagnostics/feed/?format=rss à l'aide d'un navigateur RSS.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de programmation HTTP Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Syndication WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
