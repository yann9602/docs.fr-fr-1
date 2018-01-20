---
title: WS Dual Http
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7720194f68f941d4c59dc279ae2b86a98ed6a58
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="ws-dual-http"></a><span data-ttu-id="f28db-102">WS Dual Http</span><span class="sxs-lookup"><span data-stu-id="f28db-102">WS Dual Http</span></span>
<span data-ttu-id="f28db-103">Cet exemple montre comment configurer la liaison `WSDualHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f28db-103">The Dual Http sample demonstrates how to configure the `WSDualHttpBinding` binding.</span></span> <span data-ttu-id="f28db-104">Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="f28db-104">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="f28db-105">Le service implémente un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="f28db-105">The service implements a duplex contract.</span></span> <span data-ttu-id="f28db-106">Le contrat est défini par l'interface `ICalculatorDuplex`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="f28db-106">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="f28db-107">Dans cet exemple, l'interface `ICalculatorDuplex` permet au client d'effectuer des opérations mathématiques, et notamment de calculer le résultat sur la session.</span><span class="sxs-lookup"><span data-stu-id="f28db-107">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over the session.</span></span> <span data-ttu-id="f28db-108">Le service retourne indépendamment les résultats sur l'interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="f28db-108">Independently, the service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="f28db-109">Un contrat duplex requiert une session, car un contexte doit être établi pour mettre en correspondance l'ensemble des messages échangés entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="f28db-109">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between client and service.</span></span> <span data-ttu-id="f28db-110">La liaison `WSDualHttpBinding` prend en charge la communication duplex.</span><span class="sxs-lookup"><span data-stu-id="f28db-110">The `WSDualHttpBinding` binding supports duplex communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f28db-111">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="f28db-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f28db-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f28db-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f28db-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f28db-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f28db-114">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f28db-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f28db-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f28db-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 <span data-ttu-id="f28db-116">Pour configurer un point de terminaison de service avec `WSDualHttpBinding`, spécifiez la liaison dans la configuration de point de terminaison tel qu'indiqué.</span><span class="sxs-lookup"><span data-stu-id="f28db-116">To configure a service endpoint with the `WSDualHttpBinding`, specify the binding in the endpoint configuration as shown.</span></span>  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 <span data-ttu-id="f28db-117">Sur le client, vous devez configurer une adresse que le serveur peut utiliser afin de se connecter au client, tel qu'illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="f28db-117">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="f28db-118">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="f28db-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f28db-119">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="f28db-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 <span data-ttu-id="f28db-120">Lorsque vous exécutez l'exemple, vous pouvez consulter les messages retournés au client sur l'interface de rappel envoyée depuis le service.</span><span class="sxs-lookup"><span data-stu-id="f28db-120">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="f28db-121">Tous les résultats intermédiaires sont affichés, suivis de l'équation en entier une fois toutes les opérations terminées.</span><span class="sxs-lookup"><span data-stu-id="f28db-121">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="f28db-122">Appuyez sur ENTER pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="f28db-122">Press ENTER to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f28db-123">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f28db-123">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f28db-124">Installez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 à l'aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="f28db-124">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="f28db-125">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f28db-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="f28db-126">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f28db-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="f28db-127">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f28db-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f28db-128">Lorsque vous exécutez le client dans une configuration à plusieurs ordinateurs, veillez à remplacer localhost dans les deux le `address` attribut de la [point de terminaison](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) élément et la `clientBaseAddress` attribut de la [ \< liaison >](../../../../docs/framework/misc/binding.md) élément de la [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) élément portant le nom de l’ordinateur approprié, comme indiqué :</span><span class="sxs-lookup"><span data-stu-id="f28db-128">When running the client in a cross-machine configuration, be sure to replace localhost in both the `address` attribute of the [endpoint](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) element and the `clientBaseAddress` attribute of the [\<binding>](../../../../docs/framework/misc/binding.md) element of the [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown:</span></span>  
  
    ```xml  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f28db-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f28db-129">See Also</span></span>
