---
title: "Comment : démarrer des services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, starting
- services, starting
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: e4f93da8a2a5be00d798d64caba0f54bfd71ceb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-start-services"></a><span data-ttu-id="e116a-102">Comment : démarrer des services</span><span class="sxs-lookup"><span data-stu-id="e116a-102">How to: Start Services</span></span>
<span data-ttu-id="e116a-103">Une fois un service est installé, il doit être démarré.</span><span class="sxs-lookup"><span data-stu-id="e116a-103">After a service is installed, it must be started.</span></span> <span data-ttu-id="e116a-104">Appelez le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode sur la classe de service.</span><span class="sxs-lookup"><span data-stu-id="e116a-104">Starting calls the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method on the service class.</span></span> <span data-ttu-id="e116a-105">En règle générale, le <xref:System.ServiceProcess.ServiceBase.OnStart%2A> méthode définit le travail utile effectué par le service.</span><span class="sxs-lookup"><span data-stu-id="e116a-105">Usually, the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method defines the useful work the service will perform.</span></span> <span data-ttu-id="e116a-106">Après le démarrage d’un service, il reste actif jusqu'à ce qu’il est suspendu ou arrêté.</span><span class="sxs-lookup"><span data-stu-id="e116a-106">After a service starts, it remains active until it is manually paused or stopped.</span></span>  
  
 <span data-ttu-id="e116a-107">Services peuvent être configurés pour démarrer automatiquement ou manuellement.</span><span class="sxs-lookup"><span data-stu-id="e116a-107">Services can be set up to start automatically or manually.</span></span> <span data-ttu-id="e116a-108">Un service qui démarre automatiquement démarrera lorsque l’ordinateur sur lequel il est installé est tension ou redémarré.</span><span class="sxs-lookup"><span data-stu-id="e116a-108">A service that starts automatically will be started when the computer on which it is installed is rebooted or first turned on.</span></span> <span data-ttu-id="e116a-109">Un utilisateur doit démarrer un service qui démarre manuellement.</span><span class="sxs-lookup"><span data-stu-id="e116a-109">A user must start a service that starts manually.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e116a-110">Par défaut, les services créés avec [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] sont configurés pour démarrer manuellement.</span><span class="sxs-lookup"><span data-stu-id="e116a-110">By default, services created with [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] are set to start manually.</span></span>  
  
 <span data-ttu-id="e116a-111">Il existe plusieurs façons, vous pouvez démarrer manuellement un service — à partir de **l’Explorateur de serveurs**, à partir de la **Gestionnaire de contrôle des Services**, ou à partir du code à l’aide d’un composant appelé le <xref:System.ServiceProcess.ServiceController>.</span><span class="sxs-lookup"><span data-stu-id="e116a-111">There are several ways you can manually start a service — from **Server Explorer**, from the **Services Control Manager**, or from code using a component called the <xref:System.ServiceProcess.ServiceController>.</span></span>  
  
 <span data-ttu-id="e116a-112">Vous définissez la <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété sur la <xref:System.ServiceProcess.ServiceInstaller> classe pour déterminer si un service doit être démarré manuellement ou automatiquement.</span><span class="sxs-lookup"><span data-stu-id="e116a-112">You set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property on the <xref:System.ServiceProcess.ServiceInstaller> class to determine whether a service should be started manually or automatically.</span></span>  
  
### <a name="to-specify-how-a-service-should-start"></a><span data-ttu-id="e116a-113">Pour spécifier la manière dont un service doit démarrer.</span><span class="sxs-lookup"><span data-stu-id="e116a-113">To specify how a service should start</span></span>  
  
1.  <span data-ttu-id="e116a-114">Après avoir créé votre service, ajoutez les programmes d’installation nécessaires pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="e116a-114">After creating your service, add the necessary installers for it.</span></span> <span data-ttu-id="e116a-115">Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="e116a-115">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
2.  <span data-ttu-id="e116a-116">Dans le concepteur, cliquez sur le programme d’installation de service pour le service que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="e116a-116">In the designer, click the service installer for the service you are working with.</span></span>  
  
3.  <span data-ttu-id="e116a-117">Dans le **propriétés** , configurez le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété à une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e116a-117">In the **Properties** window, set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to one of the following:</span></span>  
  
    |<span data-ttu-id="e116a-118">Pour installer votre service</span><span class="sxs-lookup"><span data-stu-id="e116a-118">To have your service install</span></span>|<span data-ttu-id="e116a-119">Définissez cette valeur</span><span class="sxs-lookup"><span data-stu-id="e116a-119">Set this value</span></span>|  
    |----------------------------------|--------------------|  
    |<span data-ttu-id="e116a-120">Lorsque l’ordinateur est redémarré.</span><span class="sxs-lookup"><span data-stu-id="e116a-120">When the computer is restarted</span></span>|<span data-ttu-id="e116a-121">**Automatique**</span><span class="sxs-lookup"><span data-stu-id="e116a-121">**Automatic**</span></span>|  
    |<span data-ttu-id="e116a-122">Lorsqu’une action explicite de l’utilisateur démarre le service</span><span class="sxs-lookup"><span data-stu-id="e116a-122">When an explicit user action starts the service</span></span>|<span data-ttu-id="e116a-123">**Manuelle**</span><span class="sxs-lookup"><span data-stu-id="e116a-123">**Manual**</span></span>|  
  
    > [!TIP]
    >  <span data-ttu-id="e116a-124">Pour empêcher le démarrage du tout votre service, vous pouvez définir le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété **désactivé**.</span><span class="sxs-lookup"><span data-stu-id="e116a-124">To prevent your service from being started at all, you can set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to **Disabled**.</span></span> <span data-ttu-id="e116a-125">Vous pouvez procéder de la sorte si vous prévoyez de redémarrer un serveur plusieurs fois et que vous souhaitez gagner du temps en empêchant les services qui seraient normalement de démarrer.</span><span class="sxs-lookup"><span data-stu-id="e116a-125">You might do this if you are going to reboot a server several times and want to save time by preventing the services that would normally start from starting up.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e116a-126">Ces autres propriétés et peuvent être modifiées après l’installation du service.</span><span class="sxs-lookup"><span data-stu-id="e116a-126">These and other properties can be changed after your service is installed.</span></span>  
  
     <span data-ttu-id="e116a-127">Il existe plusieurs façons de démarrer un service qui a son <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> processus défini sur **manuel** : à partir de **l’Explorateur de serveurs**, à partir de la **Gestionnaire de contrôle des Services Windows**, ou à partir du code.</span><span class="sxs-lookup"><span data-stu-id="e116a-127">There are several ways you can start a service that has its <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> process set to **Manual** — from **Server Explorer**, from the **Windows Services Control Manager**, or from code.</span></span> <span data-ttu-id="e116a-128">Il est important de noter que toutes ces méthodes démarrent le service dans le contexte de la **Gestionnaire de contrôle des Services**; **L’Explorateur de serveurs** et méthodes de démarrage du service par programmation agissent en réalité sur le contrôleur.</span><span class="sxs-lookup"><span data-stu-id="e116a-128">It is important to note that not all of these methods actually start the service in the context of the **Services Control Manager**; **Server Explorer** and programmatic methods of starting the service actually manipulate the controller.</span></span>  
  
### <a name="to-manually-start-a-service-from-server-explorer"></a><span data-ttu-id="e116a-129">Pour démarrer manuellement un service à partir de l’Explorateur de serveurs</span><span class="sxs-lookup"><span data-stu-id="e116a-129">To manually start a service from Server Explorer</span></span>  
  
1.  <span data-ttu-id="e116a-130">Dans **l’Explorateur de serveurs**, ajoutez le serveur souhaité s’il n’est pas déjà répertorié.</span><span class="sxs-lookup"><span data-stu-id="e116a-130">In **Server Explorer**, add the server you want if it is not already listed.</span></span> <span data-ttu-id="e116a-131">Pour plus d’informations, consultez Comment : accès et initialiser l’Explorateur de base de données de l’Explorateur de serveurs.</span><span class="sxs-lookup"><span data-stu-id="e116a-131">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
2.  <span data-ttu-id="e116a-132">Développez le **Services** nœud, puis recherchez le service que vous souhaitez démarrer.</span><span class="sxs-lookup"><span data-stu-id="e116a-132">Expand the **Services** node, and then locate the service you want to start.</span></span>  
  
3.  <span data-ttu-id="e116a-133">Cliquez sur le nom du service, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="e116a-133">Right-click the name of the service, and click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-services-control-manager"></a><span data-ttu-id="e116a-134">Pour démarrer manuellement un service de gestionnaire de contrôle des Services</span><span class="sxs-lookup"><span data-stu-id="e116a-134">To manually start a service from Services Control Manager</span></span>  
  
1.  <span data-ttu-id="e116a-135">Ouvrez le **Gestionnaire de contrôle des Services** en effectuant l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e116a-135">Open the **Services Control Manager** by doing one of the following:</span></span>  
  
    -   <span data-ttu-id="e116a-136">Dans Windows XP et 2000 Professionnel, avec le bouton droit **poste** sur le bureau, puis cliquez sur **gérer**.</span><span class="sxs-lookup"><span data-stu-id="e116a-136">In Windows XP and 2000 Professional, right-click **My Computer** on the desktop, and then click **Manage**.</span></span> <span data-ttu-id="e116a-137">Dans la boîte de dialogue qui s’affiche, développez le **Services et Applications** nœud.</span><span class="sxs-lookup"><span data-stu-id="e116a-137">In the dialog box that appears, expand the **Services and Applications** node.</span></span>  
  
         <span data-ttu-id="e116a-138">\- ou -</span><span class="sxs-lookup"><span data-stu-id="e116a-138">\- or -</span></span>  
  
    -   <span data-ttu-id="e116a-139">Dans Windows Server 2003 et Windows 2000 Server, cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **outils d’administration**, puis cliquez sur **Services**.</span><span class="sxs-lookup"><span data-stu-id="e116a-139">In Windows Server 2003 and Windows 2000 Server, click **Start**, point to **Programs**, click **Administrative Tools**, and then click **Services**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="e116a-140">Dans Windows NT version 4.0, vous pouvez ouvrir cette boîte de dialogue à partir de **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="e116a-140">In Windows NT version 4.0, you can open this dialog box from **Control Panel**.</span></span>  
  
     <span data-ttu-id="e116a-141">Vous devez maintenant voir votre service répertorié dans le **Services** section de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e116a-141">You should now see your service listed in the **Services** section of the window.</span></span>  
  
2.  <span data-ttu-id="e116a-142">Sélectionnez votre service dans la liste, faites un clic droit, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="e116a-142">Select your service in the list, right-click it, and then click **Start**.</span></span>  
  
### <a name="to-manually-start-a-service-from-code"></a><span data-ttu-id="e116a-143">Pour démarrer manuellement un service à partir du code</span><span class="sxs-lookup"><span data-stu-id="e116a-143">To manually start a service from code</span></span>  
  
1.  <span data-ttu-id="e116a-144">Créez une instance de la <xref:System.ServiceProcess.ServiceController> classe et le configurer pour interagir avec le service que vous souhaitez administrer.</span><span class="sxs-lookup"><span data-stu-id="e116a-144">Create an instance of the <xref:System.ServiceProcess.ServiceController> class, and configure it to interact with the service you want to administer.</span></span>  
  
2.  <span data-ttu-id="e116a-145">Appelez la méthode <xref:System.ServiceProcess.ServiceController.Start%2A> pour démarrer le service.</span><span class="sxs-lookup"><span data-stu-id="e116a-145">Call the <xref:System.ServiceProcess.ServiceController.Start%2A> method to start the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e116a-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e116a-146">See Also</span></span>  
 [<span data-ttu-id="e116a-147">Introduction aux Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="e116a-147">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="e116a-148">Comment : créer des Services Windows</span><span class="sxs-lookup"><span data-stu-id="e116a-148">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="e116a-149">Comment : ajouter des programmes d’installation à votre Application de Service</span><span class="sxs-lookup"><span data-stu-id="e116a-149">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
