---
title: Address Headers
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a7291ce13221e85b49c6ef97c6b375b8b71014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="address-headers"></a><span data-ttu-id="0a772-102">Address Headers</span><span class="sxs-lookup"><span data-stu-id="0a772-102">Address Headers</span></span>
<span data-ttu-id="0a772-103">Cet exemple illustre comment les clients peuvent passer des paramètres de référence à un service à l'aide de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0a772-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a772-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0a772-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0a772-105">La spécification WS-Addressing définit la référence de point de terminaison permettant de s'adresser à un point de terminaison de service Web particulier.</span><span class="sxs-lookup"><span data-stu-id="0a772-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="0a772-106">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les références de point de terminaison sont modélisées à l'aide de la classe `EndpointAddress`, `EndpointAddress` correspondant au type du champ d'adresse de la classe `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="0a772-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="0a772-107">Chaque référence dans le modèle de référence de point de terminaison peut contenir des paramètres ajoutant des informations d'identification supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="0a772-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="0a772-108">Dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], ces paramètres de référence sont modélisés sous forme d'instances de la classe `AddressHeader`.</span><span class="sxs-lookup"><span data-stu-id="0a772-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="0a772-109">Dans cet exemple, le client ajoute un paramètre de référence à l'adresse `EndpointAddress` de point de terminaison du client.</span><span class="sxs-lookup"><span data-stu-id="0a772-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="0a772-110">Le service recherche ce paramètre et utilise sa valeur dans la logique de son opération « Hello ».</span><span class="sxs-lookup"><span data-stu-id="0a772-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="0a772-111">Client</span><span class="sxs-lookup"><span data-stu-id="0a772-111">Client</span></span>  
 <span data-ttu-id="0a772-112">Pour que le client envoie un paramètre de référence, il doit ajouter un en-tête `AddressHeader` à l'adresse `EndpointAddress` du `ServiceEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="0a772-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="0a772-113">La classe `EndpointAddress` étant immuable, le changement d'une adresse de point de terminaison doit être effectué à l'aide de la classe `EndpointAddressBuilder`.</span><span class="sxs-lookup"><span data-stu-id="0a772-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="0a772-114">Le code suivant initialise le client pour envoyer un paramètre de référence dans le cadre de son message.</span><span class="sxs-lookup"><span data-stu-id="0a772-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="0a772-115">Le code crée un `EndpointAddressBuilder` en utilisant comme valeur initiale l'adresse `EndpointAddress` d'origine.</span><span class="sxs-lookup"><span data-stu-id="0a772-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="0a772-116">Il ajoute alors l'en-tête d'adresse récemment créé. L'appel de `CreateAddressHeadercreates` crée un en-tête avec une valeur, un nom et un espace de noms particuliers.</span><span class="sxs-lookup"><span data-stu-id="0a772-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="0a772-117">Dans cet exemple, la valeur est « John ».</span><span class="sxs-lookup"><span data-stu-id="0a772-117">Here the value is "John".</span></span> <span data-ttu-id="0a772-118">Une fois l'en-tête ajouté au générateur, la méthode `ToEndpointAddress()` reconvertit le générateur (altérable) en une adresse de point de terminaison (immuable) assignée de nouveau au champ d'adresse de point de terminaison du client.</span><span class="sxs-lookup"><span data-stu-id="0a772-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="0a772-119">À présent, lorsque le client appelle la méthode `Console.WriteLine(client.Hello());`, le service peut obtenir la valeur de ce paramètre d'adresse, comme en témoigne le résultat obtenu par le client.</span><span class="sxs-lookup"><span data-stu-id="0a772-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="0a772-120">Serveur</span><span class="sxs-lookup"><span data-stu-id="0a772-120">Server</span></span>  
 <span data-ttu-id="0a772-121">L'implémentation de l'opération de service `Hello()` utilise le contexte `OperationContext` actuel pour inspecter la valeur des en-têtes figurant dans le message entrant.</span><span class="sxs-lookup"><span data-stu-id="0a772-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="0a772-122">Le code recherche les en-têtes correspondant à des paramètres de référence contenant le nom défini en parcourant tous les en-têtes figurant dans le message entrant.</span><span class="sxs-lookup"><span data-stu-id="0a772-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="0a772-123">Lorsqu'il trouve un tel paramètre, il lit sa valeur, puis la stocke dans la variable « id ».</span><span class="sxs-lookup"><span data-stu-id="0a772-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0a772-124">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0a772-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0a772-125">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a772-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0a772-126">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a772-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0a772-127">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0a772-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0a772-128">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0a772-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0a772-129">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="0a772-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0a772-130">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0a772-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0a772-131">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="0a772-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="0a772-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a772-132">See Also</span></span>
