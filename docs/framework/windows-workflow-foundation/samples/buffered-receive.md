---
title: "Mise en mémoire tampon de la réception"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b4851425609936d093762895cef6bdbc8ad7823
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="buffered-receive"></a><span data-ttu-id="af8ac-102">Mise en mémoire tampon de la réception</span><span class="sxs-lookup"><span data-stu-id="af8ac-102">Buffered Receive</span></span>
<span data-ttu-id="af8ac-103">Cet exemple montre comment installer et configurer la fonctionnalité de mise en mémoire tampon de la réception dans [!INCLUDE[wf](../../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af8ac-103">This sample demonstrates how to set up and configure the buffered receive feature in [!INCLUDE[wf](../../../../includes/wf-md.md)].</span></span> <span data-ttu-id="af8ac-104">La mise en mémoire tampon de la réception permet à l'auteur de workflow de créer un workflow sans devoir s'inquiéter de l'ordre dans lequel les messages sont reçus.</span><span class="sxs-lookup"><span data-stu-id="af8ac-104">Buffered receive allows the workflow author to create a workflow without having to worry about the order in which messages are received.</span></span> <span data-ttu-id="af8ac-105">La fonctionnalité de mise en mémoire tampon de la réception met les messages en mémoire tampon localement et les remet lorsque le workflow est prêt à les recevoir.</span><span class="sxs-lookup"><span data-stu-id="af8ac-105">The buffered receive feature buffers messages locally and delivers them when the workflow is ready to receive them.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="af8ac-106">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="af8ac-106">Demonstrates</span></span>  
 <span data-ttu-id="af8ac-107">Traitement des messages dans le désordre à l'aide de la mise en mémoire tampon de la réception avec les activités de messagerie.</span><span class="sxs-lookup"><span data-stu-id="af8ac-107">Out-of-order message processing using buffered receive with messaging activities.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af8ac-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af8ac-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af8ac-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="af8ac-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af8ac-110">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="af8ac-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af8ac-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="af8ac-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a><span data-ttu-id="af8ac-112">Discussion</span><span class="sxs-lookup"><span data-stu-id="af8ac-112">Discussion</span></span>  
 <span data-ttu-id="af8ac-113">Dans cet exemple, un service [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] est implémenté à l'aide de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] et a une séquence d'activités <xref:System.ServiceModel.Activities.Receive>.</span><span class="sxs-lookup"><span data-stu-id="af8ac-113">In this sample, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service is implemented using [!INCLUDE[wf1](../../../../includes/wf1-md.md)] and has a sequence of <xref:System.ServiceModel.Activities.Receive> activities.</span></span> <span data-ttu-id="af8ac-114">Ce workflow modélise un processus d'approbation d'un emprunt simple où le workflow attend trois notifications pour qu'un emprunt soit approuvé.</span><span class="sxs-lookup"><span data-stu-id="af8ac-114">This workflow models a simple loan approval process where the workflow expects three notifications for a loan to be approved.</span></span> <span data-ttu-id="af8ac-115">Une application cliente [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] envoie trois notifications corrélées dans l'ordre inverse de celui attendu par le service.</span><span class="sxs-lookup"><span data-stu-id="af8ac-115">A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client application sends three correlated notifications in the reverse order of what the service expects.</span></span> <span data-ttu-id="af8ac-116">Étant donné que la fonctionnalité de mise en mémoire tampon de la réception est activée au niveau du service, chaque message dans le désordre est mis en mémoire tampon au niveau du service et traité lorsque le workflow est prêt à le recevoir.</span><span class="sxs-lookup"><span data-stu-id="af8ac-116">Because the buffered receive feature is turned on at the service, each out-of-order message is buffered at the service and processed as the workflow becomes ready to receive it.</span></span>  
  
 <span data-ttu-id="af8ac-117">La fonctionnalité de mise en mémoire tampon de la réception nécessitant la prise en charge de <xref:System.ServiceModel.Activities.ReceiveContent> à partir de la liaison, le service utilise <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="af8ac-117">The buffered receive feature requires <xref:System.ServiceModel.Activities.ReceiveContent> support from the binding, therefore the service uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="af8ac-118">Aucune configuration spéciale n'étant requise pour la liaison, les valeurs par défaut sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="af8ac-118">No special configuration is required for the binding, so the defaults are used.</span></span>  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 <span data-ttu-id="af8ac-119">Le service expose également des métadonnées pour le service à l'aide de <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="af8ac-119">The service also exposes metadata for the service using <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span></span>  
  
 <span data-ttu-id="af8ac-120">De la même façon, le point de terminaison de client est configuré à l'aide de <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="af8ac-120">Similarly, the client endpoint is configured using <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="af8ac-121">Le code client et la configuration est généré à l’aide de la **ajouter une référence de Service** fonctionnalité de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af8ac-121">The client code and configuration is generated by using the **Add Service Reference** feature of [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="af8ac-122">L'exemple suivant est le point de terminaison de client généré dans le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="af8ac-122">The following example is the generated client endpoint in the App.config file.</span></span>  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 <span data-ttu-id="af8ac-123">Cet exemple requiert que les composants Windows suivants soient activés :</span><span class="sxs-lookup"><span data-stu-id="af8ac-123">This sample requires that the following Windows components are enabled:</span></span>  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  <span data-ttu-id="af8ac-124">Compatibilité avec la gestion [!INCLUDE[iis60](../../../../includes/iis60-md.md)], Compatibilité avec la métabase et la configuration</span><span class="sxs-lookup"><span data-stu-id="af8ac-124">[!INCLUDE[iis60](../../../../includes/iis60-md.md)] Management Compatibility, Metabase, and Configuration Compatibility</span></span>  
  
3.  <span data-ttu-id="af8ac-125">Services World Wide Web, Fonctionnalités de développement d'applications et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="af8ac-125">World Wide Web Services, Application Development Features, and ASP.NET</span></span>  
  
4.  <span data-ttu-id="af8ac-126">Serveur de file d'attente Microsoft Message Queue (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="af8ac-126">Microsoft Message Queues (MSMQ) Server</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="af8ac-127">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="af8ac-127">To set up, and build the sample</span></span>  
  
1.  <span data-ttu-id="af8ac-128">À une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], inscrivez ASP.NET en tapant `aspnet_regiis –I` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="af8ac-128">At a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by typing `aspnet_regiis –I` and press ENTER.</span></span>  
  
2.  <span data-ttu-id="af8ac-129">Exécutez [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="af8ac-129">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] as an Administrator.</span></span>  
  
3.  <span data-ttu-id="af8ac-130">Ouvrez LoanService.sln.</span><span class="sxs-lookup"><span data-stu-id="af8ac-130">Open LoanService.sln.</span></span>  
  
4.  <span data-ttu-id="af8ac-131">Lorsque vous êtes invité si vous souhaitez créer les répertoires virtuels pour le projet LoanService, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="af8ac-131">When asked if you would like to create the virtual directories for the LoanService project, select **Yes**.</span></span>  
  
#### <a name="to-set-up-the-service-queues"></a><span data-ttu-id="af8ac-132">Pour configurer les files d'attente de service</span><span class="sxs-lookup"><span data-stu-id="af8ac-132">To set up the service queues</span></span>  
  
1.  <span data-ttu-id="af8ac-133">Appuyez sur F5 pour exécuter l'application LoanClient qui crée les files d'attente et active le service défini dans Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="af8ac-133">Press F5 to run the LoanClient application that creates the queues and activates the service defined in Service1.xamlx.</span></span>  
  
2.  <span data-ttu-id="af8ac-134">Ouvrez le **gestion de l’ordinateur** console en exécutant Compmgmt.msc à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="af8ac-134">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
3.  <span data-ttu-id="af8ac-135">Dans le **gestion de l’ordinateur** de la console, développez **Service**, **Applications**, **Message Queuing**, **files d’attente privées** .</span><span class="sxs-lookup"><span data-stu-id="af8ac-135">In the **Computer Management** console, expand **Service**, **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
4.  <span data-ttu-id="af8ac-136">Avec le bouton droit de la file d’attente loanservice/Service1.xamlx et sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="af8ac-136">Right-click the loanservice/service1.xamlx queue and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="af8ac-137">Sélectionnez le **sécurité** onglet, puis ajoutez **tout le monde reçoit le Message**, **lire le Message** et **envoyer un Message** autorisations.</span><span class="sxs-lookup"><span data-stu-id="af8ac-137">Select the **Security** tab, and add **Everyone Receives Message**, **Peek Message** and **Send Message** permissions.</span></span>  
  
6.  <span data-ttu-id="af8ac-138">Ouvrez le Gestionnaire [!INCLUDE[iis60](../../../../includes/iis60-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af8ac-138">Open the [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Manager.</span></span>  
  
7.  <span data-ttu-id="af8ac-139">Accédez à **Server**, **Sites**, **site Web par défaut**, **privé**, **LoanService** et sélectionnez  **Options avancées**</span><span class="sxs-lookup"><span data-stu-id="af8ac-139">Browse to **Server**, **Sites**, **Default Web site**, **Private**, **LoanService** and select **Advanced Options**</span></span>  
  
8.  <span data-ttu-id="af8ac-140">Modifier la **protocoles activés** être **http**, **net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="af8ac-140">Change the **Enabled Protocols** to be **http**, **net.msmq**.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="af8ac-141">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="af8ac-141">To run the sample</span></span>  
  
1.  <span data-ttu-id="af8ac-142">Naviguez jusqu'à http://localhost/private/loanservice/service1.xamlx pour vérifier que le service s'exécute.</span><span class="sxs-lookup"><span data-stu-id="af8ac-142">Browse to http://localhost/private/loanservice/service1.xamlx to ensure that the service is running.</span></span>  
  
2.  <span data-ttu-id="af8ac-143">Appuyez sur F5 pour exécuter l'application LoanClient.</span><span class="sxs-lookup"><span data-stu-id="af8ac-143">Press F5 to run the LoanClient application.</span></span> <span data-ttu-id="af8ac-144">Une fois le workflow terminé, un fichier out.txt doit être enregistré dans C:\Inbox qui contient le résultat de l'échange de messages.</span><span class="sxs-lookup"><span data-stu-id="af8ac-144">Once the workflow is complete, an out.txt file should be saved to C:\Inbox that contains the result of the message exchange.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="af8ac-145">Pour nettoyer</span><span class="sxs-lookup"><span data-stu-id="af8ac-145">To clean up</span></span>  
  
1.  <span data-ttu-id="af8ac-146">Ouvrez le **gestion de l’ordinateur** console en exécutant Compmgmt.msc à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="af8ac-146">Open the **Computer Management** console by running Compmgmt.msc from a command prompt.</span></span>  
  
2.  <span data-ttu-id="af8ac-147">Développez **Service** et **Applications**, **Message Queuing**, **files d’attente privées**.</span><span class="sxs-lookup"><span data-stu-id="af8ac-147">Expand **Service** and **Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
3.  <span data-ttu-id="af8ac-148">Supprimez la file d'attente loanservice/service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="af8ac-148">Delete the loanservice/service1.xamlx queue.</span></span>  
  
4.  <span data-ttu-id="af8ac-149">Supprimez le répertoire C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="af8ac-149">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af8ac-150">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="af8ac-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af8ac-151">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="af8ac-151">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af8ac-152">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="af8ac-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af8ac-153">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="af8ac-153">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
