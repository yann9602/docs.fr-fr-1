---
title: "Comment : héberger un service WCF dans une application managée"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 5eb29db0-b6dc-4e77-8c68-0a62f79d743b
caps.latest.revision: "42"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ca834c097f7e8cea14337fece651b2b3059d06b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-host-a-wcf-service-in-a-managed-application"></a><span data-ttu-id="e0f57-102">Comment : héberger un service WCF dans une application managée</span><span class="sxs-lookup"><span data-stu-id="e0f57-102">How to: Host a WCF Service in a Managed Application</span></span>
<span data-ttu-id="e0f57-103">Pour héberger un service à l'intérieur d'une application managée, incorporez le code du service à l'intérieur du code de l'application managée, définissez un point de terminaison pour le service soit de manière impérative dans le code, soit de façon déclarative par le biais de la configuration ou à l'aide des points de terminaison par défaut, puis créez une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0f57-103">To host a service inside a managed application, embed the code for the service inside the managed application code, define an endpoint for the service either imperatively in code, declaratively through configuration, or using default endpoints, and then create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="e0f57-104">Pour commencer à recevoir des messages, appelez <xref:System.ServiceModel.ICommunicationObject.Open%2A><xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0f57-104">To start receiving messages, call <xref:System.ServiceModel.ICommunicationObject.Open%2A> on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e0f57-105">De cette manière, vous créez et ouvrez l'écouteur pour le service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-105">This creates and opens the listener for the service.</span></span> <span data-ttu-id="e0f57-106">L'hébergement d'un service selon cette méthode est souvent appelé « auto-hébergement » parce que l'application managée effectue le travail d'hébergement elle-même.</span><span class="sxs-lookup"><span data-stu-id="e0f57-106">Hosting a service in this way is often referred to as "self-hosting" because the managed application is doing the hosting work itself.</span></span> <span data-ttu-id="e0f57-107">Pour fermer le service, appelez <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0f57-107">To close the service, call <xref:System.ServiceModel.Channels.CommunicationObject.Close%2A?displayProperty=nameWithType> on <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="e0f57-108">Un service peut également être hébergé dans un service Windows managé, dans le service IIS (Internet Information Services), ou le service WAS (Windows Process Activation Service).</span><span class="sxs-lookup"><span data-stu-id="e0f57-108">A service can also be hosted in a managed Windows service, in Internet Information Services (IIS), or in Windows Process Activation Service (WAS).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e0f57-109">options pour un service d’hébergement, consultez [Services d’hébergement](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0f57-109"> hosting options for a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
 <span data-ttu-id="e0f57-110">L'hébergement d'un service dans une application managée constitue l'option d'hébergement la plus flexible parce qu'il requiert le déploiement de moins d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="e0f57-110">Hosting a service in a managed application is the most flexible option because it requires the least infrastructure to deploy.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e0f57-111">hébergement des services dans les applications managées, consultez [hébergement dans une Application gérée](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span><span class="sxs-lookup"><span data-stu-id="e0f57-111"> hosting services in managed applications, see [Hosting in a Managed Application](../../../docs/framework/wcf/feature-details/hosting-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="e0f57-112">La procédure suivante montre comment implémenter un service auto-hébergé dans une application console.</span><span class="sxs-lookup"><span data-stu-id="e0f57-112">The following procedure demonstrates how to implement a self-hosted service in a console application.</span></span>  
  
### <a name="to-create-a-self-hosted-service"></a><span data-ttu-id="e0f57-113">Pour créer un service auto-hébergé</span><span class="sxs-lookup"><span data-stu-id="e0f57-113">To create a self-hosted service</span></span>  
  
1.  <span data-ttu-id="e0f57-114">Ouvrez [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] et sélectionnez **nouveau**, **projet...**  à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="e0f57-114">Open [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and select **New**, **Project...** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="e0f57-115">Dans le **modèles installés** liste, sélectionnez **Visual C#**, **Windows** ou **Visual Basic**, **Windows**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-115">In the **Installed Templates** list, select **Visual C#**, **Windows** or **Visual Basic**, **Windows**.</span></span> <span data-ttu-id="e0f57-116">Selon votre [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] paramètres, une ou deux de ces peut se trouver sous le **autres langages** nœud dans le **modèles installés** liste.</span><span class="sxs-lookup"><span data-stu-id="e0f57-116">Depending on your [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] settings, one or both of these may be under the **Other Languages** node in the **Installed Templates** list.</span></span>  
  
3.  <span data-ttu-id="e0f57-117">Sélectionnez **Application Console** à partir de la **Windows** liste.</span><span class="sxs-lookup"><span data-stu-id="e0f57-117">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="e0f57-118">Type `SelfHost` dans les **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-118">Type `SelfHost` in the **Name** box and click **OK**.</span></span>  
  
4.  <span data-ttu-id="e0f57-119">Avec le bouton droit **SelfHost** dans **l’Explorateur de solutions** et sélectionnez **ajouter une référence...** . Sélectionnez **System.ServiceModel** à partir de la **.NET** onglet et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-119">Right-click **SelfHost** in **Solution Explorer** and select **Add Reference...**. Select **System.ServiceModel** from the **.NET** tab and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e0f57-120">Si le **l’Explorateur de solutions** fenêtre n’est pas visible, sélectionnez **l’Explorateur de solutions** à partir de la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="e0f57-120">If the **Solution Explorer** window is not visible, select **Solution Explorer** from the **View** menu.</span></span>  
  
5.  <span data-ttu-id="e0f57-121">Double-cliquez sur **Program.cs** ou **Module1.vb** dans **l’Explorateur de solutions** pour l’ouvrir dans la fenêtre de code s’il n’est pas déjà ouvert.</span><span class="sxs-lookup"><span data-stu-id="e0f57-121">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to open it in the code window if it is not already open.</span></span> <span data-ttu-id="e0f57-122">En tête du fichier, ajoutez les instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="e0f57-122">Add the following statements at the top of the file.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#1](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#1)]
     [!code-vb[CFX_SelfHost4#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#1)]  
  
6.  <span data-ttu-id="e0f57-123">Définissez et implémentez un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-123">Define and implement a service contract.</span></span> <span data-ttu-id="e0f57-124">Cet exemple définit un `HelloWorldService` qui retourne un message basé sur l'entrée au service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-124">This example defines a `HelloWorldService` that returns a message based on the input to the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#2](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#2)]
     [!code-vb[CFX_SelfHost4#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#2)]  
  
    > [!NOTE]
    >  [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e0f57-125">comment définir et implémenter une interface de service, consultez [Comment : définir un contrat de Service](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) et [Comment : implémenter un contrat de Service](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span><span class="sxs-lookup"><span data-stu-id="e0f57-125"> how to define and implement a service interface, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md) and [How to: Implement a Service Contract](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md).</span></span>  
  
7.  <span data-ttu-id="e0f57-126">En tête de la méthode `Main`, créez une instance de la classe <xref:System.Uri> avec l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-126">At the top of the `Main` method, create an instance of the <xref:System.Uri> class with the base address for the service.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#3](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#3)]
     [!code-vb[CFX_SelfHost4#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#3)]  
  
8.  <span data-ttu-id="e0f57-127">Créez une instance de la classe <xref:System.ServiceModel.ServiceHost>, en passant un <xref:System.Type> qui représente le type de service et l'URI d'adresse de base (Uniform Resource Identifier) à <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="e0f57-127">Create an instance of the <xref:System.ServiceModel.ServiceHost> class, passing a <xref:System.Type> that represents the service type and the base address Uniform Resource Identifier (URI) to the <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Type%2CSystem.Uri%5B%5D%29>.</span></span> <span data-ttu-id="e0f57-128">Activez la publication des métadonnées, puis appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost> pour initialiser le service et le préparer à recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="e0f57-128">Enable metadata publishing, and then call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on the <xref:System.ServiceModel.ServiceHost> to initialize the service and prepare it to receive messages.</span></span>  
  
     [!code-csharp[CFX_SelfHost4#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#4)]
     [!code-vb[CFX_SelfHost4#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#4)]       
  
    > [!NOTE]
    >  <span data-ttu-id="e0f57-129">Cet exemple utilise les points de terminaison par défaut et aucun fichier de configuration n'est requis pour ce service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-129">This example uses default endpoints, and no configuration file is required for this service.</span></span> <span data-ttu-id="e0f57-130">Si aucun point de terminaison n'est configuré, le runtime en crée un pour chaque adresse de base pour chaque contrat de service implémenté par le service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-130">If no endpoints are configured, then the runtime creates one endpoint for each base address for each service contract implemented by the service.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e0f57-131">par défaut des points de terminaison, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [simplifié la Configuration des Services WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="e0f57-131"> default endpoints, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
9. <span data-ttu-id="e0f57-132">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="e0f57-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
### <a name="to-test-the-service"></a><span data-ttu-id="e0f57-133">Pour tester le service</span><span class="sxs-lookup"><span data-stu-id="e0f57-133">To test the service</span></span>  
  
1.  <span data-ttu-id="e0f57-134">Appuyez sur Ctrl+F5 pour exécuter le service.</span><span class="sxs-lookup"><span data-stu-id="e0f57-134">Press Ctrl + F5 to run the service.</span></span>  
  
2.  <span data-ttu-id="e0f57-135">Ouvrez **Client Test WCF**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-135">Open **WCF Test Client**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e0f57-136">Pour ouvrir **Client Test WCF**, ouvrez un [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] invite de commandes et exécutez **WcfTestClient.exe**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-136">To open **WCF Test Client**, open a [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] command prompt and execute **WcfTestClient.exe**.</span></span>  
  
3.  <span data-ttu-id="e0f57-137">Sélectionnez **ajouter Service...**  à partir de la **fichier** menu.</span><span class="sxs-lookup"><span data-stu-id="e0f57-137">Select **Add Service...** from the **File** menu.</span></span>  
  
4.  <span data-ttu-id="e0f57-138">Type `http://localhost:8080/hello` dans la zone d’adresse et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-138">Type `http://localhost:8080/hello` into the address box and click **OK**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="e0f57-139">Assurez-vous que le service est en cours d'exécution, sinon cette étape échouera.</span><span class="sxs-lookup"><span data-stu-id="e0f57-139">Make sure the service is running or else this step fails.</span></span> <span data-ttu-id="e0f57-140">Si vous avez changé l'adresse de base dans le code, utilisez cette adresse modifiée dans cette étape.</span><span class="sxs-lookup"><span data-stu-id="e0f57-140">If you have changed the base address in the code, then use the modified base address in this step.</span></span>  
  
5.  <span data-ttu-id="e0f57-141">Double-cliquez sur **SayHello** sous le **Mes projets de Service** nœud.</span><span class="sxs-lookup"><span data-stu-id="e0f57-141">Double-click **SayHello** under the **My Service Projects** node.</span></span> <span data-ttu-id="e0f57-142">Tapez votre nom dans la **valeur** colonne dans la **demande** liste, puis cliquez sur **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="e0f57-142">Type your name into the **Value** column in the **Request** list, and click **Invoke**.</span></span> <span data-ttu-id="e0f57-143">Un message de réponse s’affiche dans le **réponse** liste.</span><span class="sxs-lookup"><span data-stu-id="e0f57-143">A reply message appears in the **Response** list.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f57-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="e0f57-144">Example</span></span>  
 <span data-ttu-id="e0f57-145">L'exemple suivant crée un objet <xref:System.ServiceModel.ServiceHost> pour héberger un service de type `HelloWorldService`, puis appelle la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="e0f57-145">The following example creates a <xref:System.ServiceModel.ServiceHost> object to host a service of type `HelloWorldService`, and then calls the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method on <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="e0f57-146">Une adresse de base est fournie dans le code, la publication des métadonnées est activée et les points de terminaison par défaut sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="e0f57-146">A base address is provided in code, metadata publishing is enabled, and default endpoints are used.</span></span>  
  
 [!code-csharp[CFX_SelfHost4#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_selfhost4/cs/program.cs#5)]
 [!code-vb[CFX_SelfHost4#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_selfhost4/vb/module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="e0f57-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0f57-147">See Also</span></span>  
 <xref:System.Uri>  
 <xref:System.Configuration.ConfigurationManager.AppSettings%2A>  
 <xref:System.Configuration.ConfigurationManager>  
 [<span data-ttu-id="e0f57-148">How to: Host a WCF Service in IIS (Comment : héberger un service WCF dans IIS)</span><span class="sxs-lookup"><span data-stu-id="e0f57-148">How to: Host a WCF Service in IIS</span></span>](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)  
 [<span data-ttu-id="e0f57-149">L’auto-hébergement</span><span class="sxs-lookup"><span data-stu-id="e0f57-149">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="e0f57-150">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="e0f57-150">Hosting Services</span></span>](../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="e0f57-151">Guide pratique pour définir un contrat de service</span><span class="sxs-lookup"><span data-stu-id="e0f57-151">How to: Define a Service Contract</span></span>](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 [<span data-ttu-id="e0f57-152">Guide pratique pour implémenter un contrat de service</span><span class="sxs-lookup"><span data-stu-id="e0f57-152">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="e0f57-153">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="e0f57-153">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [<span data-ttu-id="e0f57-154">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="e0f57-154">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="e0f57-155">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="e0f57-155">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
