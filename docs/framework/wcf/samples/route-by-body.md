---
title: Route by Body
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: efbf38d562b120308abc6fc4514a9d17ef608b51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="route-by-body"></a><span data-ttu-id="28628-102">Route by Body</span><span class="sxs-lookup"><span data-stu-id="28628-102">Route by Body</span></span>
<span data-ttu-id="28628-103">Cet exemple montre comment implémenter un service qui accepte des objets de message avec toute action SOAP.</span><span class="sxs-lookup"><span data-stu-id="28628-103">This sample demonstrates how to implement a service that accepts message objects with any SOAP action.</span></span> <span data-ttu-id="28628-104">Cet exemple est basé sur le [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="28628-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="28628-105">Le service implémente une opération `Calculate` unique qui accepte un paramètre de demande <xref:System.ServiceModel.Channels.Message> et retourne une réponse <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="28628-105">The service implements a single `Calculate` operation that accepts a <xref:System.ServiceModel.Channels.Message> request parameter and returns a <xref:System.ServiceModel.Channels.Message> response.</span></span>  
  
 <span data-ttu-id="28628-106">Dans cet exemple, le client est une application console (.exe) et le service est hébergé dans IIS.</span><span class="sxs-lookup"><span data-stu-id="28628-106">In this sample, the client is a console application (.exe) and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28628-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="28628-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="28628-108">L'exemple illustre la distribution des messages selon le contenu du corps.</span><span class="sxs-lookup"><span data-stu-id="28628-108">The sample demonstrates message dispatch based on the body content.</span></span> <span data-ttu-id="28628-109">Le modèle de service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] intégré de distribution des messages est basé sur les actions de message.</span><span class="sxs-lookup"><span data-stu-id="28628-109">The built-in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service model message dispatch mechanism is based on message Actions.</span></span> <span data-ttu-id="28628-110">Toutefois, il existe de nombreux services Web qui définissent toutes leurs opérations avec l'action="".</span><span class="sxs-lookup"><span data-stu-id="28628-110">However, there are many existing Web services that define all of their operations with Action="".</span></span> <span data-ttu-id="28628-111">Il est impossible de générer un service reposant sur WSDL qui continue à distribuer des messages de demande selon les informations d'action.</span><span class="sxs-lookup"><span data-stu-id="28628-111">It is impossible to build a service based on WSDL that keeps dispatching request messages based on Action information.</span></span> <span data-ttu-id="28628-112">Cet exemple montre un contrat de service basé sur WSDL (WSDL est contenu dans Service.wsdl, lui-même inclus dans l'exemple).</span><span class="sxs-lookup"><span data-stu-id="28628-112">This sample demonstrates a service contract that is based on WSDL (the WSDL is contained in Service.wsdl that is included with the sample).</span></span> <span data-ttu-id="28628-113">Le contrat de service est la Calculatrice, similaire à celui utilisé dans [mise en route](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="28628-113">The service contract is Calculator, similar to the one used in [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="28628-114">Toutefois, le `[OperationContract]` spécifie `Action=""` pour toutes les opérations.</span><span class="sxs-lookup"><span data-stu-id="28628-114">However the `[OperationContract]` specifies `Action=""` for all operations.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 <span data-ttu-id="28628-115">Selon le contrat, le service requiert le comportement de distribution personnalisé `DispatchByBodyBehavior` pour autoriser les messages à être distribués entre des opérations.</span><span class="sxs-lookup"><span data-stu-id="28628-115">Given a contract, a service requires custom dispatch behavior `DispatchByBodyBehavior` to allow messages to be dispatched between operations.</span></span> <span data-ttu-id="28628-116">Ce comportement de distribution initialise le `DispatchByBodyElementOperationSelector` sélecteur d’opération personnalisé avec un tableau des noms d’opération indexés par le QName des éléments wrapper respectifs.</span><span class="sxs-lookup"><span data-stu-id="28628-116">This dispatch behavior initializes the `DispatchByBodyElementOperationSelector` custom operation selector with a table of the operation names keyed by QName of respective wrapper elements.</span></span> <span data-ttu-id="28628-117">`DispatchByBodyElementOperationSelector` examine la balise de début du premier enfant du corps et sélectionne l'opération à l'aide du tableau mentionné précédemment.</span><span class="sxs-lookup"><span data-stu-id="28628-117">`DispatchByBodyElementOperationSelector` looks at the start tag of the first child of the Body and selects the operation using the table previously mentioned.</span></span>  
  
 <span data-ttu-id="28628-118">Le client utilise un proxy généré automatiquement à partir du WSDL exporté par le service à l’aide de [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="28628-118">The client uses a proxy auto-generated from the WSDL exported by the service using [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 <span data-ttu-id="28628-119">Le fait que les actions de toutes les opérations soient vides n'a aucun impact sur le code client, à l'exception des paramètres d'action du proxy généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="28628-119">The fact that actions of all operations are empty has no impact on the client code, except for the Action parameters in the auto-generated proxy.</span></span>  
  
 <span data-ttu-id="28628-120">Le code client effectue plusieurs calculs.</span><span class="sxs-lookup"><span data-stu-id="28628-120">The client code performs several calculations.</span></span> <span data-ttu-id="28628-121">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="28628-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="28628-122">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="28628-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="28628-123">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="28628-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="28628-124">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28628-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="28628-125">Pour générer la solution, suivez les instructions de [génération des exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28628-125">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="28628-126">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="28628-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="28628-127">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="28628-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="28628-128">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="28628-128">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="28628-129">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="28628-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="28628-130">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="28628-130">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a><span data-ttu-id="28628-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28628-131">See Also</span></span>
