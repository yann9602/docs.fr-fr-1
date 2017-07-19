---
title: "Feed Formatter (JSON) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# Feed Formatter (JSON)
Cet exemple indique comment sérialiser une instance de classe <xref:System.ServiceModel.Syndication.SyndicationFeed> au format JSON \(JavaScript Objet Notation\) à l'aide d'un <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> personnalisé et d'un <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## Architecture de l'exemple  
 L'exemple implémente une classe nommée `JsonFeedFormatter` qui hérite de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.  La classe `JsonFeedFormatter` repose sur le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pour lire et écrire les données au format JSON.  En interne, le formateur utilise un jeu personnalisé de types de contrat de données nommé `JsonSyndicationFeed` et `JsonSyndicationItem` pour contrôler le format des données JSON produites par le sérialiseur.  Ces détails d'implémentation sont masqués par l'utilisateur final, ce qui permet d'effectuer des appels sur les classes standard <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem>.  
  
## Écriture de flux JSON  
 Pour écrire un flux JSON, vous pouvez utiliser `JsonFeedFormatter` \(implémenté dans cet exemple\) avec <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> comme illustré dans l'exemple de code suivant.  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
  
```  
  
## Lecture d'un flux JSON  
 Pour obtenir un <xref:System.ServiceModel.Syndication.SyndicationFeed> d'un flux de données au format JSON, vous pouvez utiliser le `JsonFeedFormatter` comme illustré dans le code suivant.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Assurez\-vous d'avoir effectué la procédure indiquée à la section [Procédure d'installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pour générer l'édition C\# ou Visual Basic .NET de la solution, conformez\-vous aux instructions figurant dans [Génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, conformez\-vous aux instructions figurant dans [Exécution des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur.  Recherchez le répertoire \(par défaut\) suivant avant de continuer.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n'existe pas, accédez à la page des [exemples Windows Communication Foundation \(WCF\) et Windows Workflow Foundation \(WF\) pour .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].  Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<LecteurInstall>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## Voir aussi