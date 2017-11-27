---
title: "Comment : écrire les services par programmation"
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
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 1721417b8d1fc799e6af5d09762ee852d9fbfb03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="54dc7-102">Comment : écrire les services par programmation</span><span class="sxs-lookup"><span data-stu-id="54dc7-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="54dc7-103">Si vous choisissez de ne pas utiliser le modèle de projet de Service Windows, vous pouvez écrire vos propres services en définissant l’héritage et autres éléments d’infrastructure vous-même.</span><span class="sxs-lookup"><span data-stu-id="54dc7-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="54dc7-104">Lorsque vous créez un service par programme, vous devez effectuer plusieurs étapes qui prendrait autrement en charge le modèle pour vous :</span><span class="sxs-lookup"><span data-stu-id="54dc7-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="54dc7-105">Vous devez configurer votre classe de service d’hériter la <xref:System.ServiceProcess.ServiceBase> classe.</span><span class="sxs-lookup"><span data-stu-id="54dc7-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="54dc7-106">Vous devez créer un `Main` méthode pour votre projet de service qui définit les services à exécuter et les appels le <xref:System.ServiceProcess.ServiceBase.Run%2A> méthode dessus.</span><span class="sxs-lookup"><span data-stu-id="54dc7-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="54dc7-107">Vous devez substituer la <xref:System.ServiceProcess.ServiceBase.OnStart%2A> et <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procédures et remplissage dans n’importe quel code souhaité pour s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="54dc7-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="54dc7-108">Pour créer un service par programme</span><span class="sxs-lookup"><span data-stu-id="54dc7-108">To write a service programmatically</span></span>  
  
1.  <span data-ttu-id="54dc7-109">Créer un projet vide et une référence aux espaces de noms nécessaires en suivant ces étapes :</span><span class="sxs-lookup"><span data-stu-id="54dc7-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="54dc7-110">Dans **l’Explorateur de solutions**, cliquez sur le **références** nœud et cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="54dc7-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="54dc7-111">Sur le **.NET Framework** onglet, accédez à **System.dll** et cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="54dc7-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="54dc7-112">Faites défiler vers **sur System.Diagnostics.dll** et cliquez sur **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="54dc7-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="54dc7-113">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="54dc7-113">Click **OK**.</span></span>  
  
2.  <span data-ttu-id="54dc7-114">Ajoutez une classe et le configurer pour qu’elle hérite de <xref:System.ServiceProcess.ServiceBase>:</span><span class="sxs-lookup"><span data-stu-id="54dc7-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3.  <span data-ttu-id="54dc7-115">Ajoutez le code suivant pour configurer votre classe de service :</span><span class="sxs-lookup"><span data-stu-id="54dc7-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4.  <span data-ttu-id="54dc7-116">Créer un `Main` méthode pour votre classe et l’utiliser pour définir le service que votre classe contiendra ; `userService1` est le nom de la classe :</span><span class="sxs-lookup"><span data-stu-id="54dc7-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5.  <span data-ttu-id="54dc7-117">Remplacer la <xref:System.ServiceProcess.ServiceBase.OnStart%2A> (méthode) et définissez le traitement doit se produire lorsque votre service est démarré.</span><span class="sxs-lookup"><span data-stu-id="54dc7-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6.  <span data-ttu-id="54dc7-118">Substituez toutes les méthodes que vous souhaitez définir traitement personnalisé et écrire du code pour déterminer les actions que le service doit accomplir dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="54dc7-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7.  <span data-ttu-id="54dc7-119">Ajoutez les programmes d'installation nécessaires à votre application de service.</span><span class="sxs-lookup"><span data-stu-id="54dc7-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="54dc7-120">Pour plus d’informations, consultez [Comment : ajouter des programmes d’installation à votre Application de Service](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span><span class="sxs-lookup"><span data-stu-id="54dc7-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8.  <span data-ttu-id="54dc7-121">Générez votre projet en sélectionnant **générer la Solution** à partir de la **générer** menu.</span><span class="sxs-lookup"><span data-stu-id="54dc7-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="54dc7-122">N'appuyez pas sur la touche F5 pour exécuter votre projet : vous ne pouvez pas exécuter un projet de service de cette manière.</span><span class="sxs-lookup"><span data-stu-id="54dc7-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="54dc7-123">Créez un projet d’installation et les actions personnalisées pour installer votre service.</span><span class="sxs-lookup"><span data-stu-id="54dc7-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="54dc7-124">Pour obtenir un exemple, consultez [procédure pas à pas : création d’une Application de Service Windows dans le Concepteur de composants](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span><span class="sxs-lookup"><span data-stu-id="54dc7-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="54dc7-125">Installez le service.</span><span class="sxs-lookup"><span data-stu-id="54dc7-125">Install the service.</span></span> <span data-ttu-id="54dc7-126">Pour plus d'informations, consultez [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="54dc7-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dc7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54dc7-127">See Also</span></span>  
 [<span data-ttu-id="54dc7-128">Introduction aux Applications de Service Windows</span><span class="sxs-lookup"><span data-stu-id="54dc7-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="54dc7-129">Comment : créer des Services Windows</span><span class="sxs-lookup"><span data-stu-id="54dc7-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [<span data-ttu-id="54dc7-130">Comment : ajouter des programmes d’installation à votre Application de Service</span><span class="sxs-lookup"><span data-stu-id="54dc7-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [<span data-ttu-id="54dc7-131">Comment : enregistrer des informations sur les Services</span><span class="sxs-lookup"><span data-stu-id="54dc7-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)  
 [<span data-ttu-id="54dc7-132">Procédure pas à pas : Création d’une Application de Service Windows dans le Concepteur de composants</span><span class="sxs-lookup"><span data-stu-id="54dc7-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
