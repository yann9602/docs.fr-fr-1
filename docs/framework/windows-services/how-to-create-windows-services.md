---
title: "Comment : créer des services Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, creating
- templates, Windows Service
ms.assetid: 0f5e2cbb-d95d-477c-b2b5-4b990e6b86ff
caps.latest.revision: "18"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: c4d7f2f19c8d156f86513ac7138bccd59ae3b7fb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-windows-services"></a><span data-ttu-id="ce5fc-102">Comment : créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="ce5fc-102">How to: Create Windows Services</span></span>
<span data-ttu-id="ce5fc-103">Lorsque vous créez un service, vous pouvez utiliser un modèle de projet Visual Studio appelé **Service Windows**.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-103">When you create a service, you can use a Visual Studio project template called **Windows Service**.</span></span> <span data-ttu-id="ce5fc-104">Ce modèle accomplit automatiquement pour vous une grande part du travail : il référence les classes et les espaces de noms appropriés, définit l'héritage à partir de la classe de base des services et substitue les méthodes que vous êtes le plus susceptible de vouloir substituer.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-104">This template automatically does much of the work for you by referencing the appropriate classes and namespaces, setting up the inheritance from the base class for services, and overriding several of the methods you're likely to want to override.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ce5fc-105">Le modèle de projet Services Windows n'est pas disponible dans l'édition Express de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-105">The Windows Services project template is not available in the Express edition of Visual Studio.</span></span>  
  
 <span data-ttu-id="ce5fc-106">Pour créer un service fonctionnel, vous devez, au minimum :</span><span class="sxs-lookup"><span data-stu-id="ce5fc-106">At a minimum, to create a functional service you must:</span></span>  
  
-   <span data-ttu-id="ce5fc-107">définir la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> ;</span><span class="sxs-lookup"><span data-stu-id="ce5fc-107">Set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property.</span></span>  
  
-   <span data-ttu-id="ce5fc-108">ajouter les programmes d'installation nécessaires à votre application de service ;</span><span class="sxs-lookup"><span data-stu-id="ce5fc-108">Create the necessary installers for your service application.</span></span>  
  
-   <span data-ttu-id="ce5fc-109">substituer et spécifier le code des méthodes <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> pour personnaliser le comportement de votre service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-109">Override and specify code for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods to customize the ways in which your service behaves.</span></span>  
  
### <a name="to-create-a-windows-service-application"></a><span data-ttu-id="ce5fc-110">Pour créer une application de service Windows</span><span class="sxs-lookup"><span data-stu-id="ce5fc-110">To create a Windows Service application</span></span>  
  
1.  <span data-ttu-id="ce5fc-111">Créer un **Windows Service** projet.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-111">Create a **Windows Service** project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5fc-112">Pour obtenir des instructions sur l’écriture d’un service sans utiliser le modèle, consultez [Comment : écrire des Services par programmation](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-112">For instructions on writing a service without using the template, see [How to: Write Services Programmatically](../../../docs/framework/windows-services/how-to-write-services-programmatically.md).</span></span>  
  
2.  <span data-ttu-id="ce5fc-113">Dans le **propriétés** , configurez le <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> propriété pour votre service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-113">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property for your service.</span></span>  
  
     <span data-ttu-id="ce5fc-114">![Définissez la propriété ServiceName. ] (../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span><span class="sxs-lookup"><span data-stu-id="ce5fc-114">![Set the ServiceName property.](../../../docs/framework/windows-services/media/windowsservice-servicename.PNG "WindowsService_ServiceName")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5fc-115">La valeur de la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> doit toujours correspondre au nom enregistré dans les classes Installer.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-115">The value of the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property must always match the name recorded in the installer classes.</span></span> <span data-ttu-id="ce5fc-116">Si vous modifiez cette propriété, vous devez également mettre à jour la propriété <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> des classes Installer.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-116">If you change this property, you must update the <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> property of installer classes as well.</span></span>  
  
3.  <span data-ttu-id="ce5fc-117">Définissez le fonctionnement de votre service à l'aide des propriétés suivantes.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-117">Set any of the following properties to determine how your service will function.</span></span>  
  
    |<span data-ttu-id="ce5fc-118">Propriété</span><span class="sxs-lookup"><span data-stu-id="ce5fc-118">Property</span></span>|<span data-ttu-id="ce5fc-119">Paramètre</span><span class="sxs-lookup"><span data-stu-id="ce5fc-119">Setting</span></span>|  
    |--------------|-------------|  
    |<xref:System.ServiceProcess.ServiceBase.CanStop%2A>|<span data-ttu-id="ce5fc-120">`True` pour indiquer que le service acceptera des demandes d'arrêt ; `false` pour empêcher tout arrêt du service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-120">`True` to indicate that the service will accept requests to stop running; `false` to prevent the service from being stopped.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanShutdown%2A>|<span data-ttu-id="ce5fc-121">`True` pour indiquer que le service doit recevoir une notification en cas d'arrêt de l'ordinateur sur lequel il s'exécute, ce qui lui permet d'appeler la procédure <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-121">`True` to indicate that the service wants to receive notification when the computer on which it lives shuts down, enabling it to call the <xref:System.ServiceProcess.ServiceBase.OnShutdown%2A> procedure.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A>|<span data-ttu-id="ce5fc-122">`True` pour indiquer que le service acceptera les demandes de suspension ou de redémarrage ; `false` pour empêcher une suspension et un redémarrage du service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-122">`True` to indicate that the service will accept requests to pause or to resume running; `false` to prevent the service from being paused and resumed.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.CanHandlePowerEvent%2A>|<span data-ttu-id="ce5fc-123">`True`pour indiquer que le service peut gérer la notification des modifications apportées à l’état d’alimentation de l’ordinateur ; `false` pour empêcher le service d’être notifié de ces modifications.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-123">`True` to indicate that the service can handle notification of changes to the computer's power status; `false` to prevent the service from being notified of these changes.</span></span>|  
    |<xref:System.ServiceProcess.ServiceBase.AutoLog%2A>|<span data-ttu-id="ce5fc-124">`True` pour écrire des entrées à caractère informatif dans le journal des événements de l'application lorsque votre service effectue une action ; `false` pour désactiver cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-124">`True` to write informational entries to the Application event log when your service performs an action; `false` to disable this functionality.</span></span> <span data-ttu-id="ce5fc-125">Pour plus d’informations, consultez [Comment : journal des informations sur les Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-125">For more information, see [How to: Log Information About Services](../../../docs/framework/windows-services/how-to-log-information-about-services.md).</span></span> <span data-ttu-id="ce5fc-126">**Remarque :** par défaut, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-126">**Note:**  By default, <xref:System.ServiceProcess.ServiceBase.AutoLog%2A> is set to `true`.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5fc-127">Lorsque <xref:System.ServiceProcess.ServiceBase.CanStop%2A> ou <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> sont définies sur `false`, le **Service Control Manager** désactive les options de menu correspondant à arrêter, suspendre ou reprendre le service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-127">When <xref:System.ServiceProcess.ServiceBase.CanStop%2A> or <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> are set to `false`, the **Service Control Manager** will disable the corresponding menu options to stop, pause, or continue the service.</span></span>  
  
4.  <span data-ttu-id="ce5fc-128">Accédez à l'éditeur de code et indiquez le traitement souhaité pour les procédures <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A>.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-128">Access the Code Editor and fill in the processing you want for the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures.</span></span>  
  
5.  <span data-ttu-id="ce5fc-129">Substituez toutes les autres méthodes pour lesquelles vous voulez définir des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-129">Override any other methods for which you want to define functionality.</span></span>  
  
6.  <span data-ttu-id="ce5fc-130">Ajoutez les programmes d'installation nécessaires à votre application de service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-130">Add the necessary installers for your service application.</span></span> <span data-ttu-id="ce5fc-131">Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-131">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
7.  <span data-ttu-id="ce5fc-132">Générez votre projet en sélectionnant **générer la Solution** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-132">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ce5fc-133">N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-133">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
8.  <span data-ttu-id="ce5fc-134">Installez le service.</span><span class="sxs-lookup"><span data-stu-id="ce5fc-134">Install the service.</span></span> <span data-ttu-id="ce5fc-135">Pour plus d'informations, consultez [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="ce5fc-135">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce5fc-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce5fc-136">See Also</span></span>  
 [<span data-ttu-id="ce5fc-137">Introduction aux Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="ce5fc-137">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="ce5fc-138">Comment : écrire des Services par programmation</span><span class="sxs-lookup"><span data-stu-id="ce5fc-138">How to: Write Services Programmatically</span></span>](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)  
 [<span data-ttu-id="ce5fc-139">Comment : ajouter des programmes d’installation à votre Application de Service</span><span class="sxs-lookup"><span data-stu-id="ce5fc-139">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="ce5fc-140">Comment : enregistrer des informations sur les Services</span><span class="sxs-lookup"><span data-stu-id="ce5fc-140">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="ce5fc-141">Comment : démarrer des Services</span><span class="sxs-lookup"><span data-stu-id="ce5fc-141">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="ce5fc-142">Comment : spécifier le contexte de sécurité pour les Services</span><span class="sxs-lookup"><span data-stu-id="ce5fc-142">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)  
 [<span data-ttu-id="ce5fc-143">Comment : installer et désinstaller des Services</span><span class="sxs-lookup"><span data-stu-id="ce5fc-143">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="ce5fc-144">Procédure pas à pas : Création d’une Application de Service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="ce5fc-144">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
