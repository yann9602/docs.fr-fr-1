---
title: "Comment : ajouter des programmes d'installation à votre application de service"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, deploying
- installation components, adding to services
- installers, adding to services
- Windows Service applications, adding installers
- services, adding installers
- ServiceInstaller class, adding installers to services
- ServiceProcessInstaller class, adding installers to services
ms.assetid: 8b698e9a-b88e-4f44-ae45-e0c5ea0ae5a8
caps.latest.revision: "14"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 15487d4311f896aa09c1c7712292058086a49b50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-installers-to-your-service-application"></a><span data-ttu-id="62f4b-102">Comment : ajouter des programmes d'installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="62f4b-102">How to: Add Installers to Your Service Application</span></span>
<span data-ttu-id="62f4b-103">Visual Studio est fourni à des composants qui peuvent installer des ressources associées à vos applications de service.</span><span class="sxs-lookup"><span data-stu-id="62f4b-103">Visual Studio ships installation components that can install resources associated with your service applications.</span></span> <span data-ttu-id="62f4b-104">Composants d’installation inscrivent chaque service dans le système auquel il est en cours d’installation et informe le Gestionnaire de contrôle des Services de l’existence du service.</span><span class="sxs-lookup"><span data-stu-id="62f4b-104">Installation components register an individual service on the system to which it is being installed and let the Services Control Manager know that the service exists.</span></span> <span data-ttu-id="62f4b-105">Lorsque vous travaillez avec une application de service, vous pouvez sélectionner un lien dans la fenêtre Propriétés pour ajouter automatiquement les programmes d’installation appropriées à votre projet.</span><span class="sxs-lookup"><span data-stu-id="62f4b-105">When you work with a service application, you can select a link in the Properties window to automatically add the appropriate installers to your project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62f4b-106">Les valeurs de propriété de votre service sont copiées à partir de la classe de service à la classe de programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="62f4b-106">Property values for your service are copied from the service class to the installer class.</span></span> <span data-ttu-id="62f4b-107">Si vous mettez à jour les valeurs de propriété sur la classe de service, ils ne sont pas automatiquement répercutées dans le programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="62f4b-107">If you update the property values on the service class, they are not automatically updated in the installer.</span></span>  
  
 <span data-ttu-id="62f4b-108">Lorsque vous ajoutez un programme d’installation à votre projet, une nouvelle classe (qui, par défaut, se nomme `ProjectInstaller`) est créé dans le projet et les instances de l’installation appropriée des composants sont créés dans celui-ci.</span><span class="sxs-lookup"><span data-stu-id="62f4b-108">When you add an installer to your project, a new class (which, by default, is named `ProjectInstaller`) is created in the project, and instances of the appropriate installation components are created within it.</span></span> <span data-ttu-id="62f4b-109">Cette classe sert de point central pour tous les composants d’installation a besoin de votre projet.</span><span class="sxs-lookup"><span data-stu-id="62f4b-109">This class acts as a central point for all of the installation components your project needs.</span></span> <span data-ttu-id="62f4b-110">Par exemple, si vous ajoutez un deuxième service à votre application et cliquez sur le lien Ajouter le programme d’installation, une deuxième classe de programme d’installation n’est pas créée ; au lieu de cela, le composant d’installation supplémentaires nécessaires pour le deuxième service est ajouté à la classe existante.</span><span class="sxs-lookup"><span data-stu-id="62f4b-110">For example, if you add a second service to your application and click the Add Installer link, a second installer class is not created; instead, the necessary additional installation component for the second service is added to the existing class.</span></span>  
  
 <span data-ttu-id="62f4b-111">Vous n’avez pas besoin écrire un code spécial dans les programmes d’installation pour que vos services ne s’installe correctement.</span><span class="sxs-lookup"><span data-stu-id="62f4b-111">You do not need to do any special coding within the installers to make your services install correctly.</span></span> <span data-ttu-id="62f4b-112">Toutefois, vous devrez peut-être parfois modifier le contenu des programmes d’installation si vous avez besoin ajouter des fonctionnalités spéciales pour le processus d’installation.</span><span class="sxs-lookup"><span data-stu-id="62f4b-112">However, you may occasionally need to modify the contents of the installers if you need to add special functionality to the installation process.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62f4b-113">Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée.</span><span class="sxs-lookup"><span data-stu-id="62f4b-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="62f4b-114">Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** .</span><span class="sxs-lookup"><span data-stu-id="62f4b-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="62f4b-115">Pour plus d’informations, consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="62f4b-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-installers-to-your-service-application"></a><span data-ttu-id="62f4b-116">Pour ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="62f4b-116">To add installers to your service application</span></span>  
  
1.  <span data-ttu-id="62f4b-117">Dans **l’Explorateur de solutions**, accès **conception** mode pour le service pour lequel vous souhaitez ajouter un composant d’installation.</span><span class="sxs-lookup"><span data-stu-id="62f4b-117">In **Solution Explorer**, access **Design** view for the service for which you want to add an installation component.</span></span>  
  
2.  <span data-ttu-id="62f4b-118">Cliquez sur l’arrière-plan du concepteur pour sélectionner le service lui-même, plutôt que son contenu.</span><span class="sxs-lookup"><span data-stu-id="62f4b-118">Click the background of the designer to select the service itself, rather than any of its contents.</span></span>  
  
3.  <span data-ttu-id="62f4b-119">Avec le concepteur dans le focus, avec le bouton droit, puis cliquez sur **ajouter le programme d’installation**.</span><span class="sxs-lookup"><span data-stu-id="62f4b-119">With the designer in focus, right-click, and then click **Add Installer**.</span></span>  
  
     <span data-ttu-id="62f4b-120">Une nouvelle classe, `ProjectInstaller`et deux composants d’installation, <xref:System.ServiceProcess.ServiceProcessInstaller> et <xref:System.ServiceProcess.ServiceInstaller>, sont ajoutés à votre projet et les valeurs de propriété pour le service sont copiés vers les composants.</span><span class="sxs-lookup"><span data-stu-id="62f4b-120">A new class, `ProjectInstaller`, and two installation components, <xref:System.ServiceProcess.ServiceProcessInstaller> and <xref:System.ServiceProcess.ServiceInstaller>, are added to your project, and property values for the service are copied to the components.</span></span>  
  
4.  <span data-ttu-id="62f4b-121">Cliquez sur le <xref:System.ServiceProcess.ServiceInstaller> composant et vérifiez que la valeur de la <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> est définie sur la même valeur que le <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> propriété sur le service lui-même.</span><span class="sxs-lookup"><span data-stu-id="62f4b-121">Click the <xref:System.ServiceProcess.ServiceInstaller> component and verify that the value of the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property is set to the same value as the <xref:System.ServiceProcess.ServiceInstaller.ServiceName%2A> property on the service itself.</span></span>  
  
5.  <span data-ttu-id="62f4b-122">Pour déterminer le mode de démarrage de votre service, cliquez sur le <xref:System.ServiceProcess.ServiceInstaller> composant et définissez le <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> propriété la valeur appropriée.</span><span class="sxs-lookup"><span data-stu-id="62f4b-122">To determine how your service will be started, click the <xref:System.ServiceProcess.ServiceInstaller> component and set the <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> property to the appropriate value.</span></span>  
  
    |<span data-ttu-id="62f4b-123">Value</span><span class="sxs-lookup"><span data-stu-id="62f4b-123">Value</span></span>|<span data-ttu-id="62f4b-124">Résultat</span><span class="sxs-lookup"><span data-stu-id="62f4b-124">Result</span></span>|  
    |-----------|------------|  
    |<xref:System.ServiceProcess.ServiceStartMode.Manual>|<span data-ttu-id="62f4b-125">Le service doit être démarré manuellement après l’installation.</span><span class="sxs-lookup"><span data-stu-id="62f4b-125">The service must be manually started after installation.</span></span> <span data-ttu-id="62f4b-126">Pour plus d’informations, consultez [Comment : démarrer des Services](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="62f4b-126">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Automatic>|<span data-ttu-id="62f4b-127">Le service démarre par lui-même chaque fois que l’ordinateur redémarre.</span><span class="sxs-lookup"><span data-stu-id="62f4b-127">The service will start by itself whenever the computer reboots.</span></span>|  
    |<xref:System.ServiceProcess.ServiceStartMode.Disabled>|<span data-ttu-id="62f4b-128">Le service ne peut pas être démarré.</span><span class="sxs-lookup"><span data-stu-id="62f4b-128">The service cannot be started.</span></span>|  
  
6.  <span data-ttu-id="62f4b-129">Pour déterminer le contexte de sécurité dans lequel s’exécute le service, cliquez sur le <xref:System.ServiceProcess.ServiceProcessInstaller> composant et définissez les valeurs de propriété appropriée.</span><span class="sxs-lookup"><span data-stu-id="62f4b-129">To determine the security context in which your service will run, click the <xref:System.ServiceProcess.ServiceProcessInstaller> component and set the appropriate property values.</span></span> <span data-ttu-id="62f4b-130">Pour plus d’informations, consultez [Comment : spécifier le contexte de sécurité pour les Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span><span class="sxs-lookup"><span data-stu-id="62f4b-130">For more information, see [How to: Specify the Security Context for Services](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md).</span></span>  
  
7.  <span data-ttu-id="62f4b-131">Substituez toutes les méthodes pour lesquelles vous devez effectuer un traitement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="62f4b-131">Override any methods for which you need to perform custom processing.</span></span>  
  
8.  <span data-ttu-id="62f4b-132">Effectuez les étapes 1 à 7 pour chaque service supplémentaire de votre projet.</span><span class="sxs-lookup"><span data-stu-id="62f4b-132">Perform steps 1 through 7 for each additional service in your project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="62f4b-133">Pour chaque service supplémentaire de votre projet, vous devez ajouter un <xref:System.ServiceProcess.ServiceInstaller> composant du projet `ProjectInstaller` classe.</span><span class="sxs-lookup"><span data-stu-id="62f4b-133">For each additional service in your project, you must add an additional <xref:System.ServiceProcess.ServiceInstaller> component to the project's `ProjectInstaller` class.</span></span> <span data-ttu-id="62f4b-134">Le <xref:System.ServiceProcess.ServiceProcessInstaller> composant ajouté à l’étape 3 fonctionne avec tous les programmes d’installation de service individuels dans le projet.</span><span class="sxs-lookup"><span data-stu-id="62f4b-134">The <xref:System.ServiceProcess.ServiceProcessInstaller> component added in step three works with all of the individual service installers in the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f4b-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62f4b-135">See Also</span></span>  
 [<span data-ttu-id="62f4b-136">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="62f4b-136">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="62f4b-137">Guide pratique pour installer et désinstaller des services</span><span class="sxs-lookup"><span data-stu-id="62f4b-137">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="62f4b-138">Guide pratique pour démarrer des services</span><span class="sxs-lookup"><span data-stu-id="62f4b-138">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="62f4b-139">Guide pratique pour spécifier le contexte de sécurité des services</span><span class="sxs-lookup"><span data-stu-id="62f4b-139">How to: Specify the Security Context for Services</span></span>](../../../docs/framework/windows-services/how-to-specify-the-security-context-for-services.md)
