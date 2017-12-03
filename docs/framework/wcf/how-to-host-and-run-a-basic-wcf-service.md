---
title: "Comment : héberger et exécuter un service Windows Communication Foundation de base"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 92aa512a12911913c1d4d7ca1587bb04df0a501d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="5e069-102">Comment : héberger et exécuter un service Windows Communication Foundation de base</span><span class="sxs-lookup"><span data-stu-id="5e069-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="5e069-103">Il s'agit de la troisième des six tâches requises pour créer une application [!INCLUDE[indigo1](../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e069-103">This is the third of six tasks required to create a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="5e069-104">Pour une vue d’ensemble des six tâches, consultez la [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="5e069-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="5e069-105">Cette rubrique explique comment héberger un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] dans une application console.</span><span class="sxs-lookup"><span data-stu-id="5e069-105">This topic describes how to host a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service in a console application.</span></span> <span data-ttu-id="5e069-106">Cette procédure se compose des étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="5e069-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="5e069-107">Créez un projet d'application console pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="5e069-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="5e069-108">Créer un hôte de service pour le service.</span><span class="sxs-lookup"><span data-stu-id="5e069-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="5e069-109">Activer l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5e069-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="5e069-110">Ouvrir l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="5e069-110">Open the service host.</span></span>  
  
 <span data-ttu-id="5e069-111">La liste complète du code écrit dans cette tâche est fournie dans l'exemple qui suit la procédure.</span><span class="sxs-lookup"><span data-stu-id="5e069-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="5e069-112">Pour créer une nouvelle application console pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="5e069-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="5e069-113">Créer un nouveau projet d’Application Console en cliquant sur la solution de mise en route, sélectionnez **ajouter**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="5e069-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="5e069-114">Dans le **ajouter un nouveau projet** boîte de dialogue sur le côté gauche de la boîte de dialogue, sélectionnez **Windows** sous **c#** ou **VB**.</span><span class="sxs-lookup"><span data-stu-id="5e069-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="5e069-115">Dans la section centrale de la boîte de dialogue Sélectionnez **Application Console**.</span><span class="sxs-lookup"><span data-stu-id="5e069-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="5e069-116">Nom du projet GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="5e069-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="5e069-117">Définir le framework cible du projet GettingStartedHost à .NET Framework 4.5 en cliquant avec le bouton droit sur **GettingStartedHost** dans l’Explorateur de solutions et en sélectionnant **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5e069-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="5e069-118">Dans la zone de liste déroulante **Framework cible** sélectionnez **.NET Framework 4.5**.</span><span class="sxs-lookup"><span data-stu-id="5e069-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="5e069-119">Paramètre du framework cible pour un projet VB est un peu différent, dans la boîte de dialogue Propriétés du projet GettingStartedHost, cliquez sur le **compiler** onglet sur le côté gauche de l’écran, puis cliquez sur le **avancées de compilation Options** bouton dans le coin inférieur gauche de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5e069-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="5e069-120">Puis sélectionnez **.NET Framework 4.5** dans la zone de liste déroulante **Framework cible**.</span><span class="sxs-lookup"><span data-stu-id="5e069-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="5e069-121">Paramètre provoque le framework cible [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] pour recharger la solution, appuyez sur **OK** lorsque vous y êtes invité.</span><span class="sxs-lookup"><span data-stu-id="5e069-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="5e069-122">Ajouter une référence au projet GettingStartedLib dans le projet GettingStartedHost en cliquant avec le bouton droit sur le **références** dossier sous le projet GettingStartedHost dans l’Explorateur de solutions et sélectionnez **ajouter une référence** .</span><span class="sxs-lookup"><span data-stu-id="5e069-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="5e069-123">Dans le **ajouter une référence** boîte de dialogue, sélectionnez **Solution** sur le côté gauche de la boîte de dialogue et sélectionnez GettingStartedLib dans la section centrale de la boîte de dialogue et cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="5e069-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="5e069-124">Cela rend les types définis dans GettingStartedLib disponibles au projet GettingStartedHost.</span><span class="sxs-lookup"><span data-stu-id="5e069-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="5e069-125">Ajouter une référence à System.ServiceModel dans le projet GettingStartedHost en cliquant sur le **référence** dossier sous le projet GettingStartedHost dans l’Explorateur de solutions, puis sélectionnez **ajouter** Référence.</span><span class="sxs-lookup"><span data-stu-id="5e069-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="5e069-126">Dans le **ajouter une référence** boîte de dialogue Sélectionnez **Framework** sur le côté gauche de la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5e069-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="5e069-127">Dans la zone de texte Rechercher des assemblys, tapez `System.ServiceModel`.</span><span class="sxs-lookup"><span data-stu-id="5e069-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="5e069-128">Dans la section centrale de la boîte de dialogue Sélectionnez **System.ServiceModel**, cliquez sur le **ajouter** , puis cliquez sur le **fermer** bouton.</span><span class="sxs-lookup"><span data-stu-id="5e069-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="5e069-129">Enregistrez la solution en cliquant sur le bouton Enregistrer tout dans le menu principal.</span><span class="sxs-lookup"><span data-stu-id="5e069-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="5e069-130">Pour héberger le service</span><span class="sxs-lookup"><span data-stu-id="5e069-130">To host the service</span></span>  
  
-   <span data-ttu-id="5e069-131">Ouvrez le fichier Program.cs ou Module.vb et entrez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="5e069-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
    namespace GettingStartedHost  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                // Step 1 Create a URI to serve as the base address.  
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");  
  
                // Step 2 Create a ServiceHost instance  
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
                try  
                {  
                    // Step 3 Add a service endpoint.  
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                    // Step 4 Enable metadata exchange.  
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                    smb.HttpGetEnabled = true;  
                    selfHost.Description.Behaviors.Add(smb);  
  
                    // Step 5 Start the service.  
                    selfHost.Open();  
                    Console.WriteLine("The service is ready.");  
                    Console.WriteLine("Press <ENTER> to terminate service.");  
                    Console.WriteLine();  
                    Console.ReadLine();  
  
                    // Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close();  
                }  
                catch (CommunicationException ce)  
                {  
                    Console.WriteLine("An exception occurred: {0}", ce.Message);  
                    selfHost.Abort();  
                }  
            }  
        }  
    }  
    ```  
  
    ```vb
    'Module1.vb  
    Imports System  
    Imports System.ServiceModel  
    Imports System.ServiceModel.Description  
    Imports GettingStartedLibVB.GettingStartedLib  
  
    Module Service  
  
        Class Program  
            Shared Sub Main()  
                ' Step 1 Create a URI to serve as the base address  
                Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
                ' Step 2 Create a ServiceHost instance  
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
                Try  
  
                    ' Step 3 Add a service endpoint  
                    ' Add a service endpoint  
                    selfHost.AddServiceEndpoint( _  
                        GetType(ICalculator), _  
                        New WSHttpBinding(), _  
                        "CalculatorService")  
  
                    ' Step 4 Enable metadata exchange.  
                    Dim smb As New ServiceMetadataBehavior()  
                    smb.HttpGetEnabled = True  
                    selfHost.Description.Behaviors.Add(smb)  
  
                    ' Step 5 Start the service  
                    selfHost.Open()  
                    Console.WriteLine("The service is ready.")  
                    Console.WriteLine("Press <ENTER> to terminate service.")  
                    Console.WriteLine()  
                    Console.ReadLine()  
  
                    ' Close the ServiceHostBase to shutdown the service.  
                    selfHost.Close()  
                Catch ce As CommunicationException  
                    Console.WriteLine("An exception occurred: {0}", ce.Message)  
                    selfHost.Abort()  
                End Try  
            End Sub  
        End Class  
  
    End Module  
    ```  
  
    1.  <span data-ttu-id="5e069-132">Étape 1 - Crée une instance de la classe URI pour contenir l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="5e069-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="5e069-133">Les services sont identifiés par une URL, qui contient une adresse de base et un URI facultatif.</span><span class="sxs-lookup"><span data-stu-id="5e069-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="5e069-134">L’adresse de base est formatée comme suit : [transport]  :// [nom de l’ordinateur ou domaine] [ : option # port] / [segment d’URI facultatif] l’adresse de base pour le service de calculatrice utilise le transport HTTP, localhost, le port 8000 et l’URI « GettingStarted » du segment</span><span class="sxs-lookup"><span data-stu-id="5e069-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="5e069-135">Étape 2 – Crée une instance de la classe <xref:System.ServiceModel.ServiceHost> pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="5e069-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="5e069-136">Le constructeur prend deux paramètres, le type de la classe qui implémente le contrat de service et l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="5e069-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="5e069-137">Étape 3-crée un <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span><span class="sxs-lookup"><span data-stu-id="5e069-137">Step 3 – Creates a <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span></span> <span data-ttu-id="5e069-138">Un point de terminaison de service est composé d’une adresse, d’une liaison et d’un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="5e069-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="5e069-139">Le <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` constructeur prend donc le type interface de contrat de service, une liaison et une adresse.</span><span class="sxs-lookup"><span data-stu-id="5e069-139">The <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`  constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="5e069-140">Le contrat de service est `ICalculator`, que vous définissez et implémentez dans le type de service.</span><span class="sxs-lookup"><span data-stu-id="5e069-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="5e069-141">La liaison utilisée dans cet exemple est <xref:System.ServiceModel.WSHttpBinding>, qui est une liaison intégrée utilisée pour se connecter aux points de terminaison qui sont conformes aux spécifications WS-*.</span><span class="sxs-lookup"><span data-stu-id="5e069-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-* specifications.</span></span> <span data-ttu-id="5e069-142">Pour plus d’informations sur les liaisons WCF, consultez [vue d’ensemble des liaisons WCF](../../../docs/framework/wcf/bindings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="5e069-143">L'adresse est ajoutée à l'adresse de base pour identifier le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="5e069-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="5e069-144">L’adresse spécifiée dans ce code est « CalculatorService », par conséquent, l’adresse complète du point de terminaison est `"http://localhost:8000/GettingStarted/CalculatorService"` Ajout d’un point de terminaison de service est facultatif lors de l’utilisation de .NET Framework 4.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5e069-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"` Adding a service endpoint is optional when using .NET Framework 4.0 or later.</span></span> <span data-ttu-id="5e069-145">Dans ces versions, si aucun point de terminaison n'est ajouté dans le code ou dans la configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d'adresse de base et de contrat implémentée par le service.</span><span class="sxs-lookup"><span data-stu-id="5e069-145">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="5e069-146">Pour plus d’informations sur la valeur par défaut les points de terminaison consultez [spécification d’une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-146">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5e069-147"> les points de terminaison, les liaisons et les comportements par défaut, consultez [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) et [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-147"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="5e069-148">L'ajout d'un point de terminaison de service est facultatif lorsque vous utilisez .NET Framework 4 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="5e069-148">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="5e069-149">Dans ces versions, si aucun point de terminaison n'est ajouté dans le code ou dans la configuration, WCF ajoute un point de terminaison par défaut pour chaque combinaison d'adresse de base et de contrat implémentée par le service.</span><span class="sxs-lookup"><span data-stu-id="5e069-149">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="5e069-150">Pour plus d’informations sur la valeur par défaut les points de terminaison consultez [spécification d’une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-150">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5e069-151"> les points de terminaison, les liaisons et les comportements par défaut, consultez [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) et [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-151"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="5e069-152">Étape 4 – Activer l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="5e069-152">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="5e069-153">Les clients utilisent l'échange de métadonnées pour générer des proxys qui seront utilisés pour appeler les opérations de service.</span><span class="sxs-lookup"><span data-stu-id="5e069-153">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="5e069-154">Pour activer l’échange de métadonnées, créez un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> d’une instance, affectez-lui la de <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriété `true`et ajoutez le comportement à la <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  --> `System.ServiceModel.ServiceHost.Behaviors%2A` collection de la <xref:System.ServiceModel.ServiceHost> instance.</span><span class="sxs-lookup"><span data-stu-id="5e069-154">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="5e069-155">Étape 5 - Ouvrir <xref:System.ServiceModel.ServiceHost> pour écouter les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="5e069-155">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="5e069-156">Notez que le code attend que l'utilisateur appuie sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="5e069-156">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="5e069-157">Si vous n'effectuez pas cette opération, l'application se ferme immédiatement et le service s'arrête. Notez également le bloc try/catch utilisé.</span><span class="sxs-lookup"><span data-stu-id="5e069-157">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="5e069-158">Une fois que <xref:System.ServiceModel.ServiceHost> a été instancié, le reste du code est placé dans un bloc try/catch.</span><span class="sxs-lookup"><span data-stu-id="5e069-158">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="5e069-159">Pour plus d’informations sur l’interception d’exceptions levées par en toute sécurité <xref:System.ServiceModel.ServiceHost>, consultez [en évitant les problèmes avec l’instruction Using](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5e069-159">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="5e069-160">Pour vérifier que le service fonctionne</span><span class="sxs-lookup"><span data-stu-id="5e069-160">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="5e069-161">Exécutez l'application console GettingStartedHost à partir de [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5e069-161">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="5e069-162">Lors de l'exécution sur [!INCLUDE[wv](../../../includes/wv-md.md)] et les systèmes d'exploitation ultérieurs, le service doit être exécuté avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="5e069-162">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="5e069-163">Parce que [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] a été exécuté avec les privilèges d'administrateur, GettingStartedHost est également exécuté avec ces mêmes privilèges.</span><span class="sxs-lookup"><span data-stu-id="5e069-163">Because [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="5e069-164">Vous pouvez aussi démarrer une nouvelle invite de commandes qui l'exécute avec les privilèges d'administrateur et y exécuter service.exe.</span><span class="sxs-lookup"><span data-stu-id="5e069-164">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="5e069-165">Ouvrez Internet Explorer et accédez à la page de débogage du service à l'adresse `http://localhost:8000/GettingStarted/CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="5e069-165">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e069-166">Exemple</span><span class="sxs-lookup"><span data-stu-id="5e069-166">Example</span></span>  
 <span data-ttu-id="5e069-167">L'exemple suivant inclut le contrat de service et l'implémentation d'étapes précédentes dans le didacticiel et héberge le service dans une application console.</span><span class="sxs-lookup"><span data-stu-id="5e069-167">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="5e069-168">Pour compiler avec un compilateur de ligne de commande, compilez IService1.cs et Service1.cs dans une bibliothèque de classes référençant `System.ServiceModel.dll`.</span><span class="sxs-lookup"><span data-stu-id="5e069-168">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="5e069-169">Et compilez le fichier Program.cs dans une application console.</span><span class="sxs-lookup"><span data-stu-id="5e069-169">And compile Program.cs to a console application.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
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
}  
```  
  
```csharp
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
namespace GettingStartedLib  
{  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            double result = n1 + n2;  
            Console.WriteLine("Received Add({0},{1})", n1, n2);  
            // Code added to write output to the console window.  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            double result = n1 - n2;  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            double result = n1 * n2;  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            double result = n1 / n2;  
            Console.WriteLine("Received Divide({0},{1})", n1, n2);  
            Console.WriteLine("Return: {0}", result);  
            return result;  
        }  
    }  
}  
```  
  
```csharp
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
namespace GettingStartedHost  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");  
  
            // Step 2 of the hosting procedure: Create ServiceHost  
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);  
  
            try  
            {  
                // Step 3 of the hosting procedure: Add a service endpoint.  
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");  
  
                // Step 4 of the hosting procedure: Enable metadata exchange.  
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();  
                smb.HttpGetEnabled = true;  
                selfHost.Description.Behaviors.Add(smb);  
  
                // Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open();  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                selfHost.Close();  
            }  
            catch (CommunicationException ce)  
            {  
                Console.WriteLine("An exception occurred: {0}", ce.Message);  
                selfHost.Abort();  
            }  
        }  
    }  
}  
```  
  
```vb
'IService1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
    Public Interface ICalculator  
  
        <OperationContract()> _  
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
        <OperationContract()> _  
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
    End Interface  
End Namespace  
```  
  
```vb
'Service1.vb  
Imports System  
Imports System.ServiceModel  
  
Namespace GettingStartedLib  
  
    Public Class CalculatorService  
        Implements ICalculator  
  
        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add  
            Dim result As Double = n1 + n2  
            ' Code added to write output to the console window.  
            Console.WriteLine("Received Add({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
        End Function  
  
        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract  
            Dim result As Double = n1 - n2  
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply  
            Dim result As Double = n1 * n2  
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
  
        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide  
            Dim result As Double = n1 / n2  
            Console.WriteLine("Received Divide({0},{1})", n1, n2)  
            Console.WriteLine("Return: {0}", result)  
            Return result  
  
        End Function  
    End Class  
End Namespace  
```  
  
```vb
'Module1.vb  
Imports System  
Imports System.ServiceModel  
Imports System.ServiceModel.Description  
Imports GettingStartedLibVB.GettingStartedLib  
  
Module Service  
  
    Class Program  
        Shared Sub Main()  
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.  
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")  
  
            ' Step 2 of the hosting procedure: Create ServiceHost  
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)  
            Try  
  
                ' Step 3 of the hosting procedure: Add a service endpoint.  
                ' Add a service endpoint  
                selfHost.AddServiceEndpoint( _  
                    GetType(ICalculator), _  
                    New WSHttpBinding(), _  
                    "CalculatorService")  
  
                ' Step 4 of the hosting procedure: Enable metadata exchange.  
                ' Enable metadata exchange  
                Dim smb As New ServiceMetadataBehavior()  
                smb.HttpGetEnabled = True  
                selfHost.Description.Behaviors.Add(smb)  
  
                ' Step 5 of the hosting procedure: Start (and then stop) the service.  
                selfHost.Open()  
                Console.WriteLine("The service is ready.")  
                Console.WriteLine("Press <ENTER> to terminate service.")  
                Console.WriteLine()  
                Console.ReadLine()  
  
                ' Close the ServiceHostBase to shutdown the service.  
                selfHost.Close()  
            Catch ce As CommunicationException  
                Console.WriteLine("An exception occurred: {0}", ce.Message)  
                selfHost.Abort()  
            End Try  
        End Sub  
    End Class  
  
End Module  
```  
  
> [!NOTE]
>  <span data-ttu-id="5e069-170">Les services tels que celui-ci requièrent que l'autorisation enregistre des adresses HTTP sur l'ordinateur pour écouter.</span><span class="sxs-lookup"><span data-stu-id="5e069-170">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="5e069-171">Les comptes Administrateur possèdent cette autorisation, mais l'autorisation pour les espaces de noms HTTP doit être accordée aux comptes qui ne sont pas administrateur.</span><span class="sxs-lookup"><span data-stu-id="5e069-171">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="5e069-172">comment configurer des réservations d’espace de noms, consultez [configuration de HTTP et HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-172"> how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="5e069-173">Lors de l'exécution sous [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], service.exe doit être exécuté avec les privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="5e069-173">When running under [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="5e069-174">Le service est en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="5e069-174">Now the service is running.</span></span> <span data-ttu-id="5e069-175">Passez à [Comment : créer un Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-175">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="5e069-176">Pour des informations de dépannage, consultez [dépannage Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5e069-176">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e069-177">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e069-177">See Also</span></span>  
 [<span data-ttu-id="5e069-178">Prise en main</span><span class="sxs-lookup"><span data-stu-id="5e069-178">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="5e069-179">L’auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="5e069-179">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
