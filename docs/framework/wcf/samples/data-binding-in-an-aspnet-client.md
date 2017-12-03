---
title: Data Binding in an ASP.NET Client
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18d133b8eb5bef9e6e9152ef856265c1cbe18b51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="2ca05-102">Data Binding in an ASP.NET Client</span><span class="sxs-lookup"><span data-stu-id="2ca05-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="2ca05-103">Cet exemple indique comment lier des données retournées par un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] standard dans une application Web Forms.</span><span class="sxs-lookup"><span data-stu-id="2ca05-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ca05-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2ca05-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2ca05-105">Cet exemple contient un service qui implémente un contrat définissant un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="2ca05-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2ca05-106">Il se compose d'une application Web Forms cliente accessible à partir d'un navigateur, et d'un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hébergé par les services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="2ca05-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="2ca05-107">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="2ca05-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="2ca05-108">Le contrat est défini par l'interface `IWeatherService`, laquelle expose une opération nommée `GetWeatherData`.</span><span class="sxs-lookup"><span data-stu-id="2ca05-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="2ca05-109">Cette opération accepte un tableau de villes et retourne un tableau d'objets `WeatherData` qui représente les prévisions de températures maximales et minimales d'une ville.</span><span class="sxs-lookup"><span data-stu-id="2ca05-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="2ca05-110">Sur la page .aspx du client [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], un contrôle Web DataGrid est défini et contient la représentation graphique des données retournées par le service.</span><span class="sxs-lookup"><span data-stu-id="2ca05-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="2ca05-111">Le code sur la page .aspx appelle le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et retourne les données météorologiques dans un tableau d'objets `WeatherData`.</span><span class="sxs-lookup"><span data-stu-id="2ca05-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="2ca05-112">DataGrid indique où obtenir ses données en affectant ce tableau à sa propriété `DataSource`.</span><span class="sxs-lookup"><span data-stu-id="2ca05-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="2ca05-113">La liaison de données se produit avec un appel à la méthode `DataBind` de DataGrid.</span><span class="sxs-lookup"><span data-stu-id="2ca05-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="2ca05-114">Tout ce code est contenu dans le.`aspx`</span><span class="sxs-lookup"><span data-stu-id="2ca05-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="2ca05-115">la page `Page_Load` méthode chaque fois que l’utilisateur actualise la page du navigateur, les données est mise à jour dans la grille de données.</span><span class="sxs-lookup"><span data-stu-id="2ca05-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2ca05-116">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="2ca05-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2ca05-117">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ca05-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="2ca05-118">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2ca05-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2ca05-119">Le client de cet exemple est un site Web qui s’exécute sous un serveur web de développement.</span><span class="sxs-lookup"><span data-stu-id="2ca05-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="2ca05-120">Pour lancer le serveur Web de développement, tapez la commande suivante à l’invite de commande : «`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span><span class="sxs-lookup"><span data-stu-id="2ca05-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="2ca05-121">Puis accédez à http://localhost:8000/client.</span><span class="sxs-lookup"><span data-stu-id="2ca05-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="2ca05-122">Pour exécuter cet exemple sur plusieurs ordinateurs, remplacez toutes les références à `localhost` dans le fichier Web.config du client par le nom d'ordinateur du serveur.</span><span class="sxs-lookup"><span data-stu-id="2ca05-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2ca05-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2ca05-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2ca05-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="2ca05-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2ca05-125">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="2ca05-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2ca05-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="2ca05-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="2ca05-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ca05-127">See Also</span></span>
