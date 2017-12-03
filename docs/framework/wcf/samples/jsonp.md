---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9a9355c223d3d37811383d52d64f0ac6ddeeaea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="jsonp"></a><span data-ttu-id="92dc0-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="92dc0-102">JSONP</span></span>
<span data-ttu-id="92dc0-103">Cet exemple montre comment prendre en charge JSON with Padding (JSONP) dans les services WCF REST.</span><span class="sxs-lookup"><span data-stu-id="92dc0-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="92dc0-104">JSONP est une convention servant à appeler des scripts entre domaines en générant des balises de script dans le document actif.</span><span class="sxs-lookup"><span data-stu-id="92dc0-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="92dc0-105">Le résultat est retourné dans une fonction de rappel spécifiée.</span><span class="sxs-lookup"><span data-stu-id="92dc0-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="92dc0-106">JSONP repose sur le principe que les balises telles que \<script src = « http:/ /... » > peuvent évaluer des scripts à partir de n’importe quel domaine, et le script récupéré par ces balises est évalué dans une portée dans laquelle d’autres fonctions peuvent déjà être définies.</span><span class="sxs-lookup"><span data-stu-id="92dc0-106">JSONP is based on the idea that tags such as \<script src="http://..." > can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="92dc0-107">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="92dc0-107">Demonstrates</span></span>  
 <span data-ttu-id="92dc0-108">Script entre domaines avec JSONP.</span><span class="sxs-lookup"><span data-stu-id="92dc0-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="92dc0-109">Discussion</span><span class="sxs-lookup"><span data-stu-id="92dc0-109">Discussion</span></span>  
 <span data-ttu-id="92dc0-110">L'exemple inclut une page Web qui ajoute dynamiquement un bloc de script après que la page a été rendue dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="92dc0-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="92dc0-111">Ce bloc de script appelle un service WCF REST qui a une seule opération, `GetCustomer`.</span><span class="sxs-lookup"><span data-stu-id="92dc0-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="92dc0-112">Le service WCF REST retourne le nom et l'adresse d'un client encapsulés dans un nom de fonction de rappel.</span><span class="sxs-lookup"><span data-stu-id="92dc0-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="92dc0-113">Lorsque le service WCF REST répond, la fonction de rappel de la page Web est appelée avec les données client et la fonction de rappel affiche les données dans la page Web.</span><span class="sxs-lookup"><span data-stu-id="92dc0-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="92dc0-114">L'injection de la balise de script et l'exécution de la fonction de rappel sont gérées automatiquement par le contrôle ASP.NET AJAX ScriptManager.</span><span class="sxs-lookup"><span data-stu-id="92dc0-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="92dc0-115">Le modèle d'utilisation est le même qu'avec tous les proxys ASP.NET AJAX, mais comprend une ligne supplémentaire pour activer JSONP, comme le montre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="92dc0-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="92dc0-116">La page Web peut appeler le service WCF REST, car le service utilise le <xref:System.ServiceModel.Description.WebScriptEndpoint> avec `crossDomainScriptAccessEnabled` ayant la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="92dc0-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="92dc0-117">Ces deux configurations sont effectuent dans le fichier Web.config sous le \<system.serviceModel > élément.</span><span class="sxs-lookup"><span data-stu-id="92dc0-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="92dc0-118">ScriptManager gère l'interaction avec le service et cache la complexité de l'implémentation manuelle de l'accès JSONP.</span><span class="sxs-lookup"><span data-stu-id="92dc0-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="92dc0-119">Lorsque `crossDomainScriptAccessEnabled` a la valeur `true` et que le format de réponse d'une opération est JSON, l'infrastructure [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] recherche dans l'URI de la demande un paramètre de chaîne de requête de rappel et inclut la réponse JSON dans un wrapper avec la valeur du paramètre de chaîne de requête de rappel.</span><span class="sxs-lookup"><span data-stu-id="92dc0-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="92dc0-120">Dans l'exemple, la page Web appelle le service WCF REST avec l'URI suivant.</span><span class="sxs-lookup"><span data-stu-id="92dc0-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="92dc0-121">Étant donné que le paramètre de chaîne de requête de rappel a la valeur `JsonPCallback`, le service WCF retourne une réponse JSONP représentée dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="92dc0-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="92dc0-122">Cette réponse JSONP inclut les données client mises au format JSON et encapsulées avec le nom de la fonction de rappel que la page Web a demandée.</span><span class="sxs-lookup"><span data-stu-id="92dc0-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="92dc0-123">ScriptManager exécute ce rappel à l'aide d'une balise de script pour effectuer la demande entre domaines, puis passe le résultat au gestionnaire onSuccess qui a été passé à l'opération GetCustomer du proxy ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="92dc0-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="92dc0-124">L'exemple se compose de deux applications Web ASP.NET : l'une contient juste un service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ; l'autre contient la page Web .aspx qui appelle le service.</span><span class="sxs-lookup"><span data-stu-id="92dc0-124">The sample consists of two ASP.NET web applications: one contains just a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="92dc0-125">Lors de l'exécution de la solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] héberge les deux sites Web sur des ports différents, ce qui crée un environnement où le service et le client résident dans des domaines différents.</span><span class="sxs-lookup"><span data-stu-id="92dc0-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92dc0-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="92dc0-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="92dc0-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="92dc0-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92dc0-128">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="92dc0-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92dc0-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="92dc0-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="92dc0-130">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="92dc0-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="92dc0-131">Ouvrez la solution de l'exemple JSONP.</span><span class="sxs-lookup"><span data-stu-id="92dc0-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="92dc0-132">Appuyez sur F5 pour lancer le lien hypertexte « http://localhost:26648/JSONPClientPage.aspx » http://localhost:26648/JSONPClientPage.aspx dans le navigateur.</span><span class="sxs-lookup"><span data-stu-id="92dc0-132">Press F5 to launch  HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx in the browser.</span></span>  
  
3.  <span data-ttu-id="92dc0-133">Notez qu’après le chargement de la page, les entrées de texte pour le « Nom » et « Address » sont remplies par les valeurs.</span><span class="sxs-lookup"><span data-stu-id="92dc0-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="92dc0-134">Ces valeurs ont été fournies à partir d'un appel au service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] alors que le navigateur avait effectué le rendu de la page.</span><span class="sxs-lookup"><span data-stu-id="92dc0-134">These values were supplied from a call to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service after the browser finished rendering the page.</span></span>
