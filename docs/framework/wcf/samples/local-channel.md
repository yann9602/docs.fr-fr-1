---
title: Local Channel
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5bf10b872d484f8b4b40de7c332f80280e2ac912
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="local-channel"></a><span data-ttu-id="606cb-102">Local Channel</span><span class="sxs-lookup"><span data-stu-id="606cb-102">Local Channel</span></span>
<span data-ttu-id="606cb-103">Local Channel est un canal du transport [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] utilisé pour la communication dans un même domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="606cb-103">Local Channel is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport channel that is used for communication within the same application domain.</span></span> <span data-ttu-id="606cb-104">Cela peut être utile pour les scénarios où le client et le service s’exécutent dans le même domaine d’application et où la charge liée à la pile de canaux WCF classique (sérialisation et désérialisation de messages) doit être évitée.</span><span class="sxs-lookup"><span data-stu-id="606cb-104">This is useful for scenarios where the client and the service are running in the same application domain and the overhead of the typical WCF channel stack (serialization and deserialization of messages) must be avoided.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="606cb-105">Démonstrations</span><span class="sxs-lookup"><span data-stu-id="606cb-105">Demonstrates</span></span>  
 <span data-ttu-id="606cb-106">Local Channel</span><span class="sxs-lookup"><span data-stu-id="606cb-106">Local Channel</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="606cb-107">Discussion</span><span class="sxs-lookup"><span data-stu-id="606cb-107">Discussion</span></span>  
 <span data-ttu-id="606cb-108">Cet exemple est composé de deux fichiers projet :</span><span class="sxs-lookup"><span data-stu-id="606cb-108">The sample consists of two project files:</span></span>  
  
-   <span data-ttu-id="606cb-109">**LocalChannel**: la représentation par programme du canal local dans le domaine d’application actuel.</span><span class="sxs-lookup"><span data-stu-id="606cb-109">**LocalChannel**: The programmatic representation of the local channel within the current application domain.</span></span> <span data-ttu-id="606cb-110">Dans ce projet, le composant expéditeur place le message dans une file d'attente en mémoire et le composant récepteur retire le message de la file d'attente pour le recevoir.</span><span class="sxs-lookup"><span data-stu-id="606cb-110">In this project, the sending component places the message in an in-memory queue and the receiving component de-queues the message to receive it.</span></span>  
  
-   <span data-ttu-id="606cb-111">**ClientAndService**: ce projet héberge un service dans une application console, puis l’exécute un client pour appeler le service à partir du même domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="606cb-111">**ClientAndService**: This project hosts a service in a console application and then runs a client to call the service from within the same application domain.</span></span>  
  
 <span data-ttu-id="606cb-112">Le canal local est conçu pour ignorer la pile de canaux et le processus de sérialisation afin de gagner en vitesse.</span><span class="sxs-lookup"><span data-stu-id="606cb-112">The local channel design skips both the channel stack and the serialization process to increase speed.</span></span> <span data-ttu-id="606cb-113">Le canal de transport local est implémenté à l'aide d'une file d'attente pour transporter les appels de service du client au service et pour retourner la valeur au client.</span><span class="sxs-lookup"><span data-stu-id="606cb-113">The local transport channel is implemented using a queue to transport service calls from the client to the service and to return back the value to the client.</span></span> <span data-ttu-id="606cb-114">Au lieu de sérialiser des paramètres et des valeurs de retour, l'exemple copie les objets.</span><span class="sxs-lookup"><span data-stu-id="606cb-114">Rather than serializing parameters and return values, the sample copies the objects.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="606cb-115">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="606cb-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="606cb-116">Générez et exécutez la solution LocalChannel.</span><span class="sxs-lookup"><span data-stu-id="606cb-116">Build and run the LocalChannel solution.</span></span>  
  
2.  <span data-ttu-id="606cb-117">L'hôte du service démarre et le client appelle le service en utilisant le canal local.</span><span class="sxs-lookup"><span data-stu-id="606cb-117">The service host is started and the client calls the service using the local channel.</span></span> <span data-ttu-id="606cb-118">Une fenêtre de console apparaît pour afficher le résultat de l'appel de service.</span><span class="sxs-lookup"><span data-stu-id="606cb-118">A console window appears to display the results of the service call.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="606cb-119">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="606cb-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="606cb-120">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="606cb-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="606cb-121">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="606cb-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="606cb-122">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="606cb-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
