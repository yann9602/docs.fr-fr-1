---
title: Reliable Secure Profile
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 921edc41-e91b-40f9-bde9-b6148b633e61
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 89a6d5c2e485699a55c77797c34eaca2c9848c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-secure-profile"></a><span data-ttu-id="d5a51-102">Reliable Secure Profile</span><span class="sxs-lookup"><span data-stu-id="d5a51-102">Reliable Secure Profile</span></span>
<span data-ttu-id="d5a51-103">Cet exemple montre comment composer [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] et [Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP).</span><span class="sxs-lookup"><span data-stu-id="d5a51-103">This sample demonstrates how to compose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and [Reliable Secure Profile](http://go.microsoft.com/fwlink/?LinkId=178140) (RSP).</span></span> <span data-ttu-id="d5a51-104">Cet exemple montre l’implémentation d’un [établir une connexion](http://go.microsoft.com/fwlink/?LinkId=178141) canal qui peut être composée avec une messagerie fiable et éventuellement un canal sécurisé pour créer une liaison sécurisée fiable basé sur la spécification de RSP.</span><span class="sxs-lookup"><span data-stu-id="d5a51-104">This sample demonstrates the implementation of a [Make Connection](http://go.microsoft.com/fwlink/?LinkId=178141) channel which can be composed together with Reliable Messaging and optionally a secure channel to create a Reliable Secure Binding based on the RSP specification.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5a51-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="d5a51-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5a51-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="d5a51-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5a51-107">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="d5a51-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5a51-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="d5a51-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ReliableSecureProfile`  
  
## <a name="discussion"></a><span data-ttu-id="d5a51-109">Discussion</span><span class="sxs-lookup"><span data-stu-id="d5a51-109">Discussion</span></span>  
 <span data-ttu-id="d5a51-110">Cet exemple illustre un scénario d'échange de messages bidirectionnel, asynchrone et fiable.</span><span class="sxs-lookup"><span data-stu-id="d5a51-110">This sample demonstrates a reliable asynchronous two-way message exchange scenario.</span></span> <span data-ttu-id="d5a51-111">Le service a un contrat duplex et le client implémente le contrat de rappel duplex.</span><span class="sxs-lookup"><span data-stu-id="d5a51-111">The service has a duplex contract and the client implements the duplex callback contract.</span></span> <span data-ttu-id="d5a51-112">Le client initie une demande à un service, pour laquelle une réponse est attendue sur une connexion distincte.</span><span class="sxs-lookup"><span data-stu-id="d5a51-112">The client initiates a request to a service, for which a response is expected on a separate connection.</span></span> <span data-ttu-id="d5a51-113">Le message de demande est envoyé de manière fiable.</span><span class="sxs-lookup"><span data-stu-id="d5a51-113">The request message is sent reliably.</span></span> <span data-ttu-id="d5a51-114">Le client ne souhaite pas ouvrir de point de terminaison d'écoute de son côté.</span><span class="sxs-lookup"><span data-stu-id="d5a51-114">The client does not want to open a listening endpoint at its end.</span></span> <span data-ttu-id="d5a51-115">Il interroge donc le service au moyen de demandes « Make Connection » de sorte que le service renvoie la réponse sur le canal arrière de cette demande « Make Connection ».</span><span class="sxs-lookup"><span data-stu-id="d5a51-115">Thus, it polls the service with ‘Make Connection’ requests for the service to send back the response on the back channel of this ‘Make Connection’ request.</span></span> <span data-ttu-id="d5a51-116">Cet exemple montre comment bénéficier d'une communication en duplex fiable et sécurisée sur HTTP sans que le client n'expose de point de terminaison d'écoute (et ne crée d'exception de pare-feu).</span><span class="sxs-lookup"><span data-stu-id="d5a51-116">This sample demonstrates how to have secure reliable duplex communication over HTTP without the client exposing a listening endpoint (and creating a firewall exception).</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5a51-117">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="d5a51-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d5a51-118">Ouvrez le **ReliableSecureProfile** solution.</span><span class="sxs-lookup"><span data-stu-id="d5a51-118">Open the **ReliableSecureProfile** solution.</span></span>  
  
2.  <span data-ttu-id="d5a51-119">Bouton droit sur le **Service** projet **l’Explorateur de solutions**, sélectionnez **déboguer**, **démarrer une nouvelle instance** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="d5a51-119">Right click the **Service** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="d5a51-120">Cela démarre l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="d5a51-120">This starts up the service host.</span></span>  
  
3.  <span data-ttu-id="d5a51-121">Bouton droit sur le **Client** projet **l’Explorateur de solutions**, sélectionnez **déboguer**, **démarrer une nouvelle instance** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="d5a51-121">Right click the **Client** project in **Solution Explorer**, select **Debug**, **Start new instance** from the context menu.</span></span> <span data-ttu-id="d5a51-122">Cela démarre le client.</span><span class="sxs-lookup"><span data-stu-id="d5a51-122">This starts up the client.</span></span>  
  
4.  <span data-ttu-id="d5a51-123">Tapez une chaîne quelconque dans l'invite de la fenêtre de console du client et appuyez sur ENTRÉE. Cela envoie la chaîne entrée au service, qui calcule un hachage de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="d5a51-123">Type in any string in the prompt on the client console window and click ENTER.This sends the input string to the service, which computes a hash of this string.</span></span>  
  
5.  <span data-ttu-id="d5a51-124">Examinez le résultat sur les fenêtres du client lorsque le service rappelle l'opération de contrat de rappel duplex pour afficher le résultat dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="d5a51-124">View the result on the client windows when the service calls back the duplex callback contract operation to display the result on the client console window.</span></span> <span data-ttu-id="d5a51-125">Un délai intentionnel est appliqué au service pour simuler une longue opération de traitement des données.</span><span class="sxs-lookup"><span data-stu-id="d5a51-125">There is an intentional delay on the service to simulate a long running operation of processing the data.</span></span>  
  
6.  <span data-ttu-id="d5a51-126">La surveillance du trafic HTTP (par l'un des outils d'analyse de réseau en ligne, comme le Moniteur réseau, Fiddler, etc.) montre qu'une séquence de communication est établie entre le client et le service comme stipulé par Reliable Secure Profile, et comment le client interroge le service avec des demandes « Make Connection ».</span><span class="sxs-lookup"><span data-stu-id="d5a51-126">Monitoring the HTTP traffic (by any of the online network monitoring tools like Network Monitor, Fiddler and so on) shows that a sequence for communication is established between the client and the service as laid down by the Reliable Secure Profile, and how the client polls the service with ‘Make Connection’ requests.</span></span> <span data-ttu-id="d5a51-127">Lorsque le service est prêt à renvoyer la réponse traitée, il utilise le canal arrière de la dernière demande « Make Connection » pour renvoyer les résultats.</span><span class="sxs-lookup"><span data-stu-id="d5a51-127">When the service gets ready to send back the processed response, it uses the back channel of the last ‘Make Connection’ request to send back the results.</span></span>  
  
7.  <span data-ttu-id="d5a51-128">Appuyez sur ENTRÉE dans la fenêtre de console du service pour le fermer.</span><span class="sxs-lookup"><span data-stu-id="d5a51-128">Press ENTER on the service console window to close the service.</span></span> <span data-ttu-id="d5a51-129">Appuyez sur ENTRÉE dans la fenêtre de console du client pour le fermer.</span><span class="sxs-lookup"><span data-stu-id="d5a51-129">Press ENTER on the client console window to close the client.</span></span>
