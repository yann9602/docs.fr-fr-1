---
title: Configuration Channel Factory
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b749493-bd8a-4ccb-893e-5948901a1486
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4aa0f4aec0a673a07c6b6d752d8609caedbcfa4b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="configuration-channel-factory"></a><span data-ttu-id="3544f-102">Configuration Channel Factory</span><span class="sxs-lookup"><span data-stu-id="3544f-102">Configuration Channel Factory</span></span>
<span data-ttu-id="3544f-103">Cet exemple couvre l'utilisation du <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="3544f-103">This sample covers the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span> <span data-ttu-id="3544f-104">Le <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> permet une gestion centralisée de la configuration du client [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3544f-104">The <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> allows central management of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client configuration.</span></span> <span data-ttu-id="3544f-105">Celle-ci peut également être utile dans les scénarios où la configuration est sélectionnée ou modifiée après le chargement du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="3544f-105">This can also be useful in scenarios in which configuration is selected or changed after the application domain load time.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="3544f-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="3544f-106">Demonstrates</span></span>  
 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>  
  
## <a name="discussion"></a><span data-ttu-id="3544f-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="3544f-107">Discussion</span></span>  
 <span data-ttu-id="3544f-108">Cet exemple montre comment utiliser <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> pour ajouter un fichier de configuration particulier à une application cliente, sans avoir à utiliser le fichier de configuration de l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="3544f-108">This sample shows how to use <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> to add a particular configuration file to a client application, without having to use the default application configuration file.</span></span>  
  
 <span data-ttu-id="3544f-109">Cet exemple est composé de deux projets.</span><span class="sxs-lookup"><span data-stu-id="3544f-109">The sample consists of two projects.</span></span> <span data-ttu-id="3544f-110">Le premier projet est un service simple qui s'exécute pour répondre aux messages provenant des clients.</span><span class="sxs-lookup"><span data-stu-id="3544f-110">The first project is a simple service that runs to reply to messages coming from the clients.</span></span> <span data-ttu-id="3544f-111">Le deuxième projet est une application cliente qui génère deux objets <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> à l'aide d'un <xref:System.Configuration.ExeConfigurationFileMap> pour le fichier de configuration Test.config et les utilise pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="3544f-111">The second project is a client application that builds two <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> objects using a <xref:System.Configuration.ExeConfigurationFileMap> for the Test.config configuration file and uses them to communicate with the service.</span></span> <span data-ttu-id="3544f-112">Les deux clients communiquent avec le service à l'aide de la configuration spécifiée dans Test.config.</span><span class="sxs-lookup"><span data-stu-id="3544f-112">Both clients communicate with the service using the configuration specified in Test.config.</span></span>  
  
 <span data-ttu-id="3544f-113">Le code suivant ajoute un fichier de configuration personnalisé à une application cliente.</span><span class="sxs-lookup"><span data-stu-id="3544f-113">The following code adds a custom configuration file to a client application.</span></span>  
  
```  
ExeConfigurationFileMap fileMap = new ExeConfigurationFileMap();  
fileMap.ExeConfigFilename = "Test.config";  
Configuration newConfiguration = ConfigurationManager.OpenMappedExeConfiguration(fileMap, ConfigurationUserLevel.None);  
  
ConfigurationChannelFactory<ICalculatorChannel> factory1 = new ConfigurationChannelFactory<ICalculatorChannel>("endpoint1", newConfiguration, new EndpointAddress("http://localhost:8000/servicemodelsamples/service"));  
ICalculatorChannel client1 = factory1.CreateChannel();  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3544f-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="3544f-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3544f-115">Ouvrez [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] avec les privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="3544f-115">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="3544f-116">Avec le bouton droit de la solution ConfigurationChannelFactory (2 projets), puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3544f-116">Right-click the ConfigurationChannelFactory solution (2 projects) and then select **Properties**.</span></span>  
  
3.  <span data-ttu-id="3544f-117">Dans **propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **plusieurs projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="3544f-117">In **Common Properties**, select **Startup Project**, and then click **Multiple startup projects**.</span></span>  
  
4.  <span data-ttu-id="3544f-118">Déplacer le **Service** de projet vers le début de la liste, avec la **Action 'Start'**, puis déplacez le **Client** projet après le **Service**projet, également avec la **Action 'Start'**, donc le **Client** projet est exécuté après le **Service** projet.</span><span class="sxs-lookup"><span data-stu-id="3544f-118">Move the **Service** project to the beginning of the list, with the **Action ‘Start’**, and then move the **Client** project after the **Service** project, also with the **Action ‘Start’**, so the **Client** project is executed after the **Service** project.</span></span>  
  
5.  <span data-ttu-id="3544f-119">Cliquez sur **OK**, puis appuyez sur F5 (ou CTRL + F5) pour exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="3544f-119">Click **OK**, and then press F5 (or CTRL+F5) to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3544f-120">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3544f-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3544f-121">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="3544f-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3544f-122">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3544f-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3544f-123">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="3544f-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigurationChannelFactory`
