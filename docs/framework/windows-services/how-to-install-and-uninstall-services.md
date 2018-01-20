---
title: "Comment : installer et désinstaller des services"
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
- services, uninstalling
- services, installing
- installing Windows Services
- uninstalling applications, Windows Services
- installation, Windows Services
- uninstalling Windows Services
- installutil.exe tool
ms.assetid: c89c5169-f567-4305-9d62-db31a1de5481
caps.latest.revision: "19"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 1fcbc8e7a84b16d244561e0cd69f8661236e63de
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-install-and-uninstall-services"></a><span data-ttu-id="70516-102">Comment : installer et désinstaller des services</span><span class="sxs-lookup"><span data-stu-id="70516-102">How to: Install and Uninstall Services</span></span>
<span data-ttu-id="70516-103">Si vous développez un service Windows à l'aide du .NET Framework, vous pouvez installer rapidement votre application de service à l'aide d'un utilitaire de ligne de commande appelé InstallUtil.exe.</span><span class="sxs-lookup"><span data-stu-id="70516-103">If you’re developing a Windows Service by using the .NET Framework, you can quickly install your service application by using a command-line utility called InstallUtil.exe.</span></span> <span data-ttu-id="70516-104">Si vous êtes développeur et que vous souhaitez commercialiser un service Windows que les utilisateurs peuvent installer et désinstaller, vous devez utiliser InstallShield.</span><span class="sxs-lookup"><span data-stu-id="70516-104">If you’re a developer who wants to release a Windows Service that users can install and uninstall  you should use InstallShield.</span></span> <span data-ttu-id="70516-105">Consultez [déploiement de Windows Installer](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span><span class="sxs-lookup"><span data-stu-id="70516-105">See [Windows Installer Deployment](http://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="70516-106">Si vous voulez désinstaller un service de votre ordinateur, ne suivez pas les étapes décrites dans cet article.</span><span class="sxs-lookup"><span data-stu-id="70516-106">If you want to uninstall a service from your computer, don’t follow the steps in this article.</span></span> <span data-ttu-id="70516-107">Au lieu de cela, déterminez quel programme ou package logiciel a installé le service, puis choisissez **Ajout/Suppression de programmes** dans le panneau de configuration pour désinstaller ce programme.</span><span class="sxs-lookup"><span data-stu-id="70516-107">Instead, find out which program or software package installed the service, and then choose **Add/Remove Programs** in Control Panel to uninstall that program.</span></span> <span data-ttu-id="70516-108">Notez que de nombreux services font partie intégrante de Windows. Si vous les supprimez, vous pouvez rendre le système instable.</span><span class="sxs-lookup"><span data-stu-id="70516-108">Note that many services are integral parts of Windows; if you remove them, you might cause system instability.</span></span>  
  
 <span data-ttu-id="70516-109">Pour utiliser les étapes décrites dans cet article, vous devez d'abord ajouter un programme d'installation de service à votre service Windows.</span><span class="sxs-lookup"><span data-stu-id="70516-109">In order to use the steps in this article, you first need to add a service installer to your Windows Service.</span></span> <span data-ttu-id="70516-110">Consultez [procédure pas à pas : création d’une fenêtre de Service Application dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="70516-110">See [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
 <span data-ttu-id="70516-111">Les projets de service Windows ne peuvent pas être exécutés directement à partir de l'environnement de développement Visual Studio en appuyant sur F5.</span><span class="sxs-lookup"><span data-stu-id="70516-111">Windows Service projects cannot be run directly from the Visual Studio development environment by pressing F5.</span></span> <span data-ttu-id="70516-112">C'est pourquoi le service du projet doit être installé avant de pouvoir exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="70516-112">This is because the service in the project must be installed before you can run the project.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="70516-113">Vous pouvez lancer **l’Explorateur de serveurs** et vérifiez que votre service a été installé ou désinstallé.</span><span class="sxs-lookup"><span data-stu-id="70516-113">You can launch **Server Explorer** and verify that your service has been installed or uninstalled.</span></span> <span data-ttu-id="70516-114">Pour plus d’informations, consultez Comment : accès et initialiser l’Explorateur de base de données de l’Explorateur de serveurs.</span><span class="sxs-lookup"><span data-stu-id="70516-114">For more information, see How to: Access and Initialize Server Explorer-Database Explorer.</span></span>  
  
### <a name="to-install-your-service-manually"></a><span data-ttu-id="70516-115">Pour installer votre service manuellement</span><span class="sxs-lookup"><span data-stu-id="70516-115">To install your service manually</span></span>  
  
1.  <span data-ttu-id="70516-116">Sur les fenêtres **Démarrer** menu ou **Démarrer** écran, choisissez **Visual Studio** , **Visual Studio Tools**, **développeur Invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="70516-116">On the Windows **Start** menu or **Start** screen, choose **Visual Studio** , **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="70516-117">Une invite de commandes Visual Studio s'affiche.</span><span class="sxs-lookup"><span data-stu-id="70516-117">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="70516-118">Accédez au répertoire dans lequel se trouve le fichier exécutable compilé de votre projet.</span><span class="sxs-lookup"><span data-stu-id="70516-118">Access the directory where your project's compiled executable file is located.</span></span>  
  
3.  <span data-ttu-id="70516-119">Exécutez InstallUtil.exe à partir de l'invite de commandes avec le fichier exécutable de votre projet comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="70516-119">Run InstallUtil.exe from the command prompt with your project's executable as a parameter:</span></span>  
  
    ```  
    installutil <yourproject>.exe  
    ```  
  
     <span data-ttu-id="70516-120">Si vous utilisez l'invite de commandes de Visual Studio, InstallUtil.exe doit se trouver dans le répertoire système.</span><span class="sxs-lookup"><span data-stu-id="70516-120">If you’re using the Visual Studio command prompt, InstallUtil.exe should be on the system path.</span></span> <span data-ttu-id="70516-121">Si ce n'est pas le cas, vous pouvez ajouter le chemin d'accès ou utiliser le chemin d'accès complet à l'appeler.</span><span class="sxs-lookup"><span data-stu-id="70516-121">If not, you can add it to the path, or use the fully qualified path to invoke it.</span></span> <span data-ttu-id="70516-122">Cet outil est installé avec le .NET Framework, et son chemin d'accès est `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span><span class="sxs-lookup"><span data-stu-id="70516-122">This tool is installed with the .NET Framework, and its path is `%WINDIR%\Microsoft.NET\Framework[64]\<framework_version>`.</span></span> <span data-ttu-id="70516-123">Par exemple, pour la version 32 bits de .NET Framework 4 ou 4.5.\*, si votre répertoire d'installation de Windows est C:\Windows, le chemin d'accès est `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="70516-123">For example, for the 32-bit version of the .NET Framework 4 or 4.5.\*, if your Windows installation directory is C:\Windows, the path is `C:\Windows\Microsoft.NET\Framework\v4.0.30319\InstallUtil.exe`.</span></span> <span data-ttu-id="70516-124">Pour obtenir la version 64 bits de .NET Framework 4 ou 4.5. \*, le chemin d’accès par défaut est `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span><span class="sxs-lookup"><span data-stu-id="70516-124">For the 64-bit version of the .NET Framework 4 or 4.5.\*, the default path is `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe`.</span></span>  
  
### <a name="to-uninstall-your-service-manually"></a><span data-ttu-id="70516-125">Pour désinstaller votre service manuellement</span><span class="sxs-lookup"><span data-stu-id="70516-125">To uninstall your service manually</span></span>  
  
1.  <span data-ttu-id="70516-126">Sur les fenêtres **Démarrer** menu ou **Démarrer** écran, choisissez **Visual Studio**, **Visual Studio Tools**, **développeur Invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="70516-126">On the Windows **Start** menu or **Start** screen, choose **Visual Studio**, **Visual Studio Tools**, **Developer Command Prompt**.</span></span>  
  
     <span data-ttu-id="70516-127">Une invite de commandes Visual Studio s'affiche.</span><span class="sxs-lookup"><span data-stu-id="70516-127">A Visual Studio command prompt appears.</span></span>  
  
2.  <span data-ttu-id="70516-128">Exécutez InstallUtil.exe à partir de l'invite de commandes avec la sortie de votre projet comme paramètre :</span><span class="sxs-lookup"><span data-stu-id="70516-128">Run InstallUtil.exe from the command prompt with your project's output as a parameter:</span></span>  
  
    ```  
    installutil /u <yourproject>.exe  
    ```  
  
3.  <span data-ttu-id="70516-129">Parfois, après la suppression de l'exécutable d'un service est supprimée, le service peut encore être présent dans le Registre.</span><span class="sxs-lookup"><span data-stu-id="70516-129">Sometimes, after the executable for a service is deleted, the service might still be present in the registry.</span></span> <span data-ttu-id="70516-130">Dans ce cas, utilisez la commande [sc delete](http://technet.microsoft.com/library/cc742045.aspx) pour supprimer l’entrée pour le service à partir du Registre.</span><span class="sxs-lookup"><span data-stu-id="70516-130">In that case, use the command [sc delete](http://technet.microsoft.com/library/cc742045.aspx) to remove the entry for the service from the registry.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70516-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70516-131">See Also</span></span>  
 [<span data-ttu-id="70516-132">Introduction aux applications de service Windows</span><span class="sxs-lookup"><span data-stu-id="70516-132">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="70516-133">Guide pratique pour créer des services Windows</span><span class="sxs-lookup"><span data-stu-id="70516-133">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="70516-134">Guide pratique pour ajouter des programmes d’installation à votre application de service</span><span class="sxs-lookup"><span data-stu-id="70516-134">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="70516-135">Installutil.exe (outil Installer)</span><span class="sxs-lookup"><span data-stu-id="70516-135">Installutil.exe (Installer Tool)</span></span>](../../../docs/framework/tools/installutil-exe-installer-tool.md)
