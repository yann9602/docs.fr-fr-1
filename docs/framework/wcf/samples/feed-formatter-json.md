---
title: Feed Formatter (JSON)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a87ebbe9b7a6e03ac0510e537ff74065b95cf8d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="feed-formatter-json"></a><span data-ttu-id="cd6ab-102">Feed Formatter (JSON)</span><span class="sxs-lookup"><span data-stu-id="cd6ab-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="cd6ab-103">Cet exemple indique comment sérialiser une instance de classe <xref:System.ServiceModel.Syndication.SyndicationFeed> au format JSON (JavaScript Objet Notation) à l'aide d'un <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> personnalisé et d'un <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="cd6ab-104">Architecture de l'exemple</span><span class="sxs-lookup"><span data-stu-id="cd6ab-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="cd6ab-105">L'exemple implémente une classe nommée `JsonFeedFormatter` qui hérite de <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="cd6ab-106">La classe `JsonFeedFormatter` repose sur le <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> pour lire et écrire les données au format JSON.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="cd6ab-107">En interne, le formateur utilise un jeu personnalisé de types de contrat de données nommé `JsonSyndicationFeed` et `JsonSyndicationItem` pour contrôler le format des données JSON produites par le sérialiseur.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="cd6ab-108">Ces détails d'implémentation sont masqués par l'utilisateur final, ce qui permet d'effectuer des appels sur les classes standard <xref:System.ServiceModel.Syndication.SyndicationFeed> et <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="cd6ab-109">Écriture de flux JSON</span><span class="sxs-lookup"><span data-stu-id="cd6ab-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="cd6ab-110">Pour écrire un flux JSON, vous pouvez utiliser `JsonFeedFormatter` (implémenté dans cet exemple) avec <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="cd6ab-111">Lecture d'un flux JSON</span><span class="sxs-lookup"><span data-stu-id="cd6ab-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="cd6ab-112">Pour obtenir un <xref:System.ServiceModel.Syndication.SyndicationFeed> d'un flux de données au format JSON, vous pouvez utiliser le `JsonFeedFormatter` comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd6ab-113">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="cd6ab-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cd6ab-114">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd6ab-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cd6ab-115">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd6ab-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cd6ab-116">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cd6ab-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd6ab-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cd6ab-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd6ab-119">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="cd6ab-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd6ab-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="cd6ab-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="cd6ab-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd6ab-121">See Also</span></span>
