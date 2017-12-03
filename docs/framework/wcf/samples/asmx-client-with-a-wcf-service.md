---
title: ASMX Client with a WCF Service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f4c89e6382b5edd0ca295fde8f498fe97bdb64d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="b8793-102">ASMX Client with a WCF Service</span><span class="sxs-lookup"><span data-stu-id="b8793-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="b8793-103">Cet exemple montre comment créer un service à l'aide de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] puis accéder au service depuis un client non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tel qu'un client ASMX.</span><span class="sxs-lookup"><span data-stu-id="b8793-103">This sample demonstrates how to create a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and then access the service from a non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8793-104">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b8793-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8793-105">Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="b8793-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b8793-106">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="b8793-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b8793-107">Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (`Add`, `Subtract`, `Multiply` et `Divide`).</span><span class="sxs-lookup"><span data-stu-id="b8793-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="b8793-108">Le client ASMX adresse des demandes synchrones à une opération mathématique et le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="b8793-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="b8793-109">Le service implémente un contrat `ICalculator` tel que défini dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8793-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="b8793-110">Le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Xml.Serialization.XmlSerializer> mappent des types CLR à une représentation XML.</span><span class="sxs-lookup"><span data-stu-id="b8793-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="b8793-111">Le <xref:System.Runtime.Serialization.DataContractSerializer> interprète des représentations XML différemment du XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="b8793-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="b8793-112">Les générateurs proxy non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tels que Wsdl.exe, génèrent une interface plus utilisable avec le XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="b8793-112">Non-[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="b8793-113">Le <xref:System.ServiceModel.XmlSerializerFormatAttribute> est appliqué à la `ICalculator` interface, pour garantir que le XmlSerializer est utilisé pour le mappage des types CLR en XML.</span><span class="sxs-lookup"><span data-stu-id="b8793-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="b8793-114">L'implémentation de service calcule et retourne le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="b8793-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="b8793-115">Le service expose un point de terminaison unique de communication avec le service, lequel est défini à l'aide du fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="b8793-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="b8793-116">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="b8793-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="b8793-117">Le service expose le point de terminaison à l'adresse de base fournie par l'hôte IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="b8793-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="b8793-118">L'attribut `binding` a la valeur basicHttpBinding, qui fournit des communications HTTP à l'aide de SOAP 1.1, qui est conforme à WS-BasicProfile 1.1, comme le montre l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="b8793-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="b8793-119">Le client ASMX communique avec le service [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] à l'aide d'un proxy typé généré par l'utilitaire WSDL (Web Services Description Language) Wsdl.exe.</span><span class="sxs-lookup"><span data-stu-id="b8793-119">The ASMX client communicates with the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="b8793-120">Le proxy typé est contenu dans le fichier generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="b8793-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="b8793-121">L'utilitaire WSDL récupère les métadonnées pour le service spécifié et génère un proxy typé qui sera utilisé par un client pour communiquer.</span><span class="sxs-lookup"><span data-stu-id="b8793-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="b8793-122">Par défaut, l'infrastructure n'expose pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b8793-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="b8793-123">Pour exposer les métadonnées nécessaires pour générer le proxy, vous devez ajouter un [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) et définir son `httpGetEnabled` attribut `True` comme indiqué dans la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="b8793-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="b8793-124">Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.</span><span class="sxs-lookup"><span data-stu-id="b8793-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="b8793-125">En utilisant le proxy typé généré, le client peut accéder à un point de terminaison de service donné en configurant l'adresse appropriée.</span><span class="sxs-lookup"><span data-stu-id="b8793-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="b8793-126">Le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="b8793-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="b8793-127">L'implémentation cliente génère une instance du proxy typé pour commencer à communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="b8793-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="b8793-128">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="b8793-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b8793-129">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="b8793-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8793-130">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b8793-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8793-131">Assurez-vous d’avoir effectué la [procédure d’installation d’à usage unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8793-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b8793-132">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8793-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b8793-133">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8793-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b8793-134">passage et le renvoi de données complexes types, consultez : [une liaison de données dans un Client Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [une liaison de données dans un Client Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), et [une liaison de données dans ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="b8793-134"> passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8793-135">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b8793-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8793-136">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b8793-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8793-137">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b8793-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8793-138">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b8793-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="b8793-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8793-139">See Also</span></span>
