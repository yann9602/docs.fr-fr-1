---
title: Report absolu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94eb9f401786ef05beaa51077ff4ddc170595752
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="absolute-delay"></a><span data-ttu-id="0999d-102">Report absolu</span><span class="sxs-lookup"><span data-stu-id="0999d-102">Absolute Delay</span></span>
<span data-ttu-id="0999d-103">Le principal scénario de cet exemple consiste à définir un report jusqu'à un <xref:System.DateTime> spécifié, à l'aide de minuteurs durables dans une application de workflow.</span><span class="sxs-lookup"><span data-stu-id="0999d-103">The main scenario for this sample is to delay until a specified <xref:System.DateTime> using durable timers in a workflow application.</span></span> <span data-ttu-id="0999d-104">Cette opération n'est pas comparable à l'utilisation de l'activité <xref:System.Activities.Statements.Delay> intégrée, dans la mesure où elle vous permet seulement de définir un report pour un <xref:System.TimeSpan> donné (ou nombre de minutes/secondes).</span><span class="sxs-lookup"><span data-stu-id="0999d-104">This is different from using the built-in <xref:System.Activities.Statements.Delay> activity as this will only allow you to delay for a given <xref:System.TimeSpan> (or number of minutes/seconds).</span></span>  
  
 <span data-ttu-id="0999d-105">Voici quelques scénarios tirés de la vie réelle pour lesquels cette distinction peut être importante :</span><span class="sxs-lookup"><span data-stu-id="0999d-105">Some real-life scenarios in which you may want to make this distinction include the following:</span></span>  
  
1.  <span data-ttu-id="0999d-106">Vous souhaitez différer l'envoi d'un message électronique de 30 secondes afin de vous assurer que vous n'avez fait aucune erreur.</span><span class="sxs-lookup"><span data-stu-id="0999d-106">You want to delay sending a mail for 30 seconds to make sure you didn’t make any errors.</span></span>  
  
2.  <span data-ttu-id="0999d-107">Vous faites des heures supplémentaires et souhaitez différer l'envoi de l'ensemble de vos messages électroniques en attendant les heures de bureau normales (8 heures du matin, par exemple).</span><span class="sxs-lookup"><span data-stu-id="0999d-107">You are working overtime and want to delay all of your mails until normal business hours (such as 8 am).</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0999d-108">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="0999d-108">Demonstrates</span></span>  
  
1.  <span data-ttu-id="0999d-109"><xref:System.Activities.Statements.DurableTimerExtension> pour implémenter un report absolu</span><span class="sxs-lookup"><span data-stu-id="0999d-109"><xref:System.Activities.Statements.DurableTimerExtension> for implementing Absolute Delay</span></span>  
  
2.  <span data-ttu-id="0999d-110">Configuration de la persistance à l'aide de <xref:System.Activities.WorkflowApplication> pour les minuteurs durables</span><span class="sxs-lookup"><span data-stu-id="0999d-110">Setting up persistence using <xref:System.Activities.WorkflowApplication> for Durable Timers</span></span>  
  
3.  <span data-ttu-id="0999d-111">Utilisation de <xref:System.Activities.NativeActivity%601> pour le recours à des points d'extensibilité</span><span class="sxs-lookup"><span data-stu-id="0999d-111">Use of <xref:System.Activities.NativeActivity%601> for using Extensibility points</span></span>  
  
4.  <span data-ttu-id="0999d-112">Utilisation de <xref:System.Activities.CodeActivity%601> dans l'activité SendEmail</span><span class="sxs-lookup"><span data-stu-id="0999d-112">Use of <xref:System.Activities.CodeActivity%601> in the SendEmail activity</span></span>  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  <span data-ttu-id="0999d-113">Flux de travail XAML uniquement</span><span class="sxs-lookup"><span data-stu-id="0999d-113">XAML-only workflow</span></span>  
  
 <span data-ttu-id="0999d-114">Cet exemple montre comment créer une activité personnalisée qui a lieu à un <xref:System.DateTime> défini et utilise des minuteurs durables pour enregistrer la durée du report.</span><span class="sxs-lookup"><span data-stu-id="0999d-114">This sample demonstrates how to create a custom activity which takes in a <xref:System.DateTime> and uses durable timers to register the delay duration.</span></span> <span data-ttu-id="0999d-115">Lors de l'utilisation de minuteurs durables, vous devez utiliser un <xref:System.Activities.NativeActivity> afin de créer un signet, car vous devrez enregistrer ce signet avec l'extension de minuterie.</span><span class="sxs-lookup"><span data-stu-id="0999d-115">When using durable timers, you must use a <xref:System.Activities.NativeActivity> to create a bookmark, as you will need to register this bookmark with the timer extension.</span></span> <span data-ttu-id="0999d-116">Dans cet exemple, lorsque le minuteur durable arrive à expiration, un appel à la méthode `OnTimerExpired` a lieu.</span><span class="sxs-lookup"><span data-stu-id="0999d-116">In this sample, when the durable timer expires, the `OnTimerExpired` method will be called.</span></span> <span data-ttu-id="0999d-117">Assurez-vous que vous ajoutez l'extension de minuterie dans l'événement <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> pour fournir le runtime avec ces informations.</span><span class="sxs-lookup"><span data-stu-id="0999d-117">Make sure that you are adding the timer extension in the <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> event to ensure you are providing the runtime with this information.</span></span> <span data-ttu-id="0999d-118">Le seul autre détail d'implémentation consiste à implémenter une logique afin de convertir <xref:System.DateTime> en <xref:System.TimeSpan>, du fait que les minuteurs durables n'acceptent qu'un <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="0999d-118">The only other implementation detail is that you will need to implement logic to convert from <xref:System.DateTime> to <xref:System.TimeSpan>, as durable timers only take in a <xref:System.DateTime>.</span></span> <span data-ttu-id="0999d-119">Notez une petite dégradation de la précision à cette occasion</span><span class="sxs-lookup"><span data-stu-id="0999d-119">Do note that there is a small lapse in accuracy by doing</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0999d-120">Une petite dégradation de la précision est constatée lors de la conversion de <xref:System.DateTime> en <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="0999d-120">There is a small loss of accuracy by converting from <xref:System.DateTime> to <xref:System.TimeSpan>.</span></span>  
  
 <span data-ttu-id="0999d-121">Cet exemple montre également comment activer la persistance pour un <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="0999d-121">This sample also demonstrates how to turn on persistence for a <xref:System.Activities.WorkflowApplication>.</span></span> <span data-ttu-id="0999d-122">Dans cet exemple particulier, nous allons utiliser des minuteurs durables dans lesquels les données du flux de travail sont déchargées dans la base de données de persistance au cours de la période d'inactivité en attente de l'expiration du minuteur.</span><span class="sxs-lookup"><span data-stu-id="0999d-122">For this particular sample, we will be using durable timers in which the workflow data will be unloaded into the persistence database during the idle time while waiting for timer to expire.</span></span> <span data-ttu-id="0999d-123">Cette implémentation peut également servir à d'autres actions de persistance.</span><span class="sxs-lookup"><span data-stu-id="0999d-123">This implementation can also be used for other persistence actions.</span></span> <span data-ttu-id="0999d-124">Cet exemple montre comment configurer la chaîne de connexion de persistance avec SQL Server, et comment créer le magasin d'instances afin de rendre les données persistantes pour les instances du flux de travail.</span><span class="sxs-lookup"><span data-stu-id="0999d-124">This sample shows how to set up the persistence connection string with SQL Server, and how to create the instance store in order to persist the data for workflow instances.</span></span> <span data-ttu-id="0999d-125">Une logique est fournie sur la manière de reprendre le flux de travail une fois qu'un événement rendant l'instance du flux de travail exécutable est généré.</span><span class="sxs-lookup"><span data-stu-id="0999d-125">Logic is provided on how to resume the workflow once an event is raised which makes the workflow instance runnable.</span></span>  
  
 <span data-ttu-id="0999d-126">Pendant l'exécution de cet exemple, vous pouvez noter l'heure de début et de fin du report intégré, à l'issue duquel un message électronique est envoyé.</span><span class="sxs-lookup"><span data-stu-id="0999d-126">As you step through this sample, you will see the time in which the built-in delay begins and completes, which in turn will cause an e-mail message to be sent.</span></span> <span data-ttu-id="0999d-127">À partir de là, l'activité AbsoluteDelay s'arrête jusqu'à un <xref:System.DateTime> spécifié (ou 0 seconde si <xref:System.DateTime> est arrivé à expiration), suite à quoi un message électronique est envoyé à l'expiration.</span><span class="sxs-lookup"><span data-stu-id="0999d-127">From there, the AbsoluteDelay activity will halt until a specified <xref:System.DateTime> (or 0 seconds if the <xref:System.DateTime> has expired) which in turn will send out an email upon expiration.</span></span> <span data-ttu-id="0999d-128">Cet exemple montre les deux cas d'utilisation différents de la fonctionnalité <xref:System.Activities.Statements.Delay> intégrée par rapport à l'utilisation d'une activité AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="0999d-128">This will show the two different use cases of the built-in <xref:System.Activities.Statements.Delay> functionality versus using an AbsoluteDelay activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0999d-129">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="0999d-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0999d-130">Assurez-vous que SQL Server Express (ou version ultérieure) est installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0999d-130">Ensure you have SQL Server Express (or higher) installed on your machine</span></span>  
  
2.  <span data-ttu-id="0999d-131">Exécutez setup.cmd (à partir de WF/Basic/Services/AbsoluteDelay/CS) dans une invite de commandes [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] afin de créer la base de données AbsoluteDelaySampleDB, le schéma de persistance et la logique de persistance.</span><span class="sxs-lookup"><span data-stu-id="0999d-131">Run setup.cmd (from WF/Basic/Services/AbsoluteDelay/CS) in a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt to create the AbsoluteDelaySampleDB database, create the persistence schema and create the persistence logic.</span></span>  
  
3.  <span data-ttu-id="0999d-132">Ouvrez la solution dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0999d-132">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="0999d-133">Spécifiez la durée de l'activité de report.</span><span class="sxs-lookup"><span data-stu-id="0999d-133">Specify the Duration in the Delay activity.</span></span>  
  
5.  <span data-ttu-id="0999d-134">Spécifiez l'heure d'expiration dans l'activité AbsoluteDelay.</span><span class="sxs-lookup"><span data-stu-id="0999d-134">Specify the ExpirationTime in the AbsoluteDelay activity.</span></span>  
  
6.  <span data-ttu-id="0999d-135">Mettez à jour les champs SendMailTo, SendMailFrom, SendMailSubject, SendMailBody et SmtpHost dans l'activité SendMail.</span><span class="sxs-lookup"><span data-stu-id="0999d-135">Update the SendMailTo, SendMailFrom, SendMailSubject, SendMailBody, and SmtpHost fields in the SendMail activity.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0999d-136">Si vous n'entrez pas d'hôte SMTP valide, l'application lèvera une exception SMTP.</span><span class="sxs-lookup"><span data-stu-id="0999d-136">If you do not enter a valid SMTP host, the application will throw a SMTP exception.</span></span>  
  
7.  <span data-ttu-id="0999d-137">Générez la solution en sélectionnant **générer**, **générer la Solution**.</span><span class="sxs-lookup"><span data-stu-id="0999d-137">Build the solution by selecting **Build**, **Build Solution**.</span></span>  
  
8.  <span data-ttu-id="0999d-138">Exécutez la solution en appuyant sur **F5**.</span><span class="sxs-lookup"><span data-stu-id="0999d-138">Run the solution by pressing **F5**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0999d-139">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="0999d-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0999d-140">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="0999d-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0999d-141">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="0999d-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0999d-142">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="0999d-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
