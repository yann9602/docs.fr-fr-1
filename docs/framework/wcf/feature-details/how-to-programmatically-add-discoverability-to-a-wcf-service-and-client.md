---
title: "Procédure : ajouter la détectabilité par programme à un service et un client WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a0a59788544a32b78e75ac25e787dcbae478451e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="52aae-102">Procédure : ajouter la détectabilité par programme à un service et un client WCF</span><span class="sxs-lookup"><span data-stu-id="52aae-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="52aae-103">Cette rubrique explique comment rendre un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] détectable.</span><span class="sxs-lookup"><span data-stu-id="52aae-103">This topic explains how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span> <span data-ttu-id="52aae-104">Il est basé sur le [auto-hébergement](http://go.microsoft.com/fwlink/?LinkId=145523) exemple.</span><span class="sxs-lookup"><span data-stu-id="52aae-104">It is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="52aae-105">Pour configurer l'exemple existant de service Self-Host pour la découverte</span><span class="sxs-lookup"><span data-stu-id="52aae-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="52aae-106">Ouvrez la solution Self-Host dans [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52aae-106">Open the Self-Host solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="52aae-107">L'exemple se trouve dans le répertoire TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="52aae-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="52aae-108">Ajoutez au projet du service une référence à `System.ServiceModel.Discovery.dll`.</span><span class="sxs-lookup"><span data-stu-id="52aae-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="52aae-109">Vous pouvez voir un message d’erreur indiquant « System.</span><span class="sxs-lookup"><span data-stu-id="52aae-109">You may see an error message saying "System.</span></span> <span data-ttu-id="52aae-110">ServiceModel.Discovery.dll ou une de ses dépendances requiert une version ultérieure de la [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] à celle spécifiée dans le projet... »</span><span class="sxs-lookup"><span data-stu-id="52aae-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …"</span></span> <span data-ttu-id="52aae-111">Si vous voyez ce message, cliquez sur le projet dans l’Explorateur de solutions et choisissez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="52aae-111">If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="52aae-112">Dans le **propriétés du projet** fenêtre, assurez-vous que le **Framework cible** est [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="52aae-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="52aae-113">Ouvrez le fichier Service.cs et ajoutez l'instruction `using` suivante.</span><span class="sxs-lookup"><span data-stu-id="52aae-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="52aae-114">Dans la méthode `Main()`, à l'intérieur de l'instruction `using`, ajoutez une instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> à l'hôte du service.</span><span class="sxs-lookup"><span data-stu-id="52aae-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
  
            // ...  
        }  
    }  
    ```  
  
     <span data-ttu-id="52aae-115">L'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> spécifie que le service auquel elle s'applique est détectable.</span><span class="sxs-lookup"><span data-stu-id="52aae-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="52aae-116">Ajoutez un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> à l'hôte du service, juste après le code qui ajoute l'instance <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="52aae-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="52aae-117">Ce code spécifie que les messages de découverte doivent être envoyés au point de terminaison de découverte UDP standard.</span><span class="sxs-lookup"><span data-stu-id="52aae-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="52aae-118">Pour créer une application cliente utilisant la découverte pour appeler le service</span><span class="sxs-lookup"><span data-stu-id="52aae-118">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="52aae-119">Ajoutez à la solution une nouvelle application console nommée `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="52aae-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="52aae-120">Ajoutez une référence à `System.ServiceModel.dll` et à `System.ServiceModel.Discovery.dll`.</span><span class="sxs-lookup"><span data-stu-id="52aae-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="52aae-121">Copiez les fichiers GeneratedClient.cs et App.config du projet client existant dans le nouveau projet DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="52aae-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="52aae-122">Pour ce faire, cliquez sur les fichiers dans le **l’Explorateur de solutions**, sélectionnez **copie**, puis sélectionnez le **DiscoveryClientApp** de projet, avec le bouton droit et sélectionnez **Coller**.</span><span class="sxs-lookup"><span data-stu-id="52aae-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="52aae-123">Ouvrez Program.cs.</span><span class="sxs-lookup"><span data-stu-id="52aae-123">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="52aae-124">Ajoutez les instructions `using` suivantes.</span><span class="sxs-lookup"><span data-stu-id="52aae-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="52aae-125">Ajoutez une méthode statique nommée `FindCalculatorServiceAddress()` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="52aae-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="52aae-126">Cette méthode utilise la découverte pour rechercher le service `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="52aae-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="52aae-127">À l'intérieur de la méthode `FindCalculatorServiceAddress`, créez une instance <xref:System.ServiceModel.Discovery.DiscoveryClient>, en transmettant un objet <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> au constructeur.</span><span class="sxs-lookup"><span data-stu-id="52aae-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="52aae-128">Cela indique à [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que la classe <xref:System.ServiceModel.Discovery.DiscoveryClient> doit utiliser le point de terminaison de découverte UDP standard pour envoyer et recevoir des messages de découverte.</span><span class="sxs-lookup"><span data-stu-id="52aae-128">This tells [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="52aae-129">Sur la ligne suivante, appelez la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> et spécifiez une instance <xref:System.ServiceModel.Discovery.FindCriteria> qui contient le contrat de service que vous souhaitez rechercher.</span><span class="sxs-lookup"><span data-stu-id="52aae-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="52aae-130">Le contrat à spécifier dans le cas présent est `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="52aae-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="52aae-131">Après l'appel à la méthode <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, vérifiez s'il existe au moins un service correspondant et retournez l'objet <xref:System.ServiceModel.EndpointAddress> du premier service correspondant.</span><span class="sxs-lookup"><span data-stu-id="52aae-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="52aae-132">Autrement, retournez une valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="52aae-132">Otherwise return `null`.</span></span>  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. <span data-ttu-id="52aae-133">Ajoutez une méthode statique nommée `InvokeCalculatorService` à la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="52aae-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="52aae-134">Cette méthode utilise l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress` pour appeler le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="52aae-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="52aae-135">À l'intérieur de la méthode `InvokeCalculatorService`, créez une instance de la classe `CalculatorServiceClient`.</span><span class="sxs-lookup"><span data-stu-id="52aae-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="52aae-136">Cette classe est définie par le [auto-hébergement](http://go.microsoft.com/fwlink/?LinkId=145523) exemple.</span><span class="sxs-lookup"><span data-stu-id="52aae-136">This class is defined by the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="52aae-137">Elle a été générée à l'aide de Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="52aae-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="52aae-138">Sur la ligne suivante, définissez l'adresse du point de terminaison du client sur l'adresse du point de terminaison retournée par l'objet `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="52aae-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="52aae-139">Immédiatement après le code de l'étape précédente, appelez les méthodes exposées par le service de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="52aae-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. <span data-ttu-id="52aae-140">Ajoutez un code à la méthode `Main()` dans la classe `Program` pour appeler `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="52aae-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="52aae-141">Sur la ligne suivante, appelez `InvokeCalculatorService()` et passez l'adresse du point de terminaison retournée par `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="52aae-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="52aae-142">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="52aae-142">To test the application</span></span>  
  
1.  <span data-ttu-id="52aae-143">Ouvrez une invite de commandes avec élévation de privilèges et exécutez Service.exe.</span><span class="sxs-lookup"><span data-stu-id="52aae-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="52aae-144">Ouvrez une invite de commandes et exécutez Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="52aae-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="52aae-145">La sortie de service.exe doit ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="52aae-145">The output from service.exe should look like the following output.</span></span>  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  <span data-ttu-id="52aae-146">La sortie de Discoveryclientapp.exe doit ressembler à la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="52aae-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="52aae-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="52aae-147">Example</span></span>  
 <span data-ttu-id="52aae-148">L'intégralité du code utilisé dans cet exemple est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="52aae-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="52aae-149">Étant donné que ce code est basé sur le [auto-hébergement](http://go.microsoft.com/fwlink/?LinkId=145523) exemple, uniquement les fichiers modifiés sont répertoriés.</span><span class="sxs-lookup"><span data-stu-id="52aae-149">Because this code is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="52aae-150">l’exemple d’auto-hébergement, consultez [Instructions d’installation](http://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="52aae-150"> the Self-Host sample, see [Setup Instructions](http://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints              
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="52aae-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52aae-151">See Also</span></span>  
 [<span data-ttu-id="52aae-152">Vue d’ensemble de la découverte WCF</span><span class="sxs-lookup"><span data-stu-id="52aae-152">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="52aae-153">Modèle objet de découverte WCF</span><span class="sxs-lookup"><span data-stu-id="52aae-153">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
