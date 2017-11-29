---
title: OperationScope
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56206a21-1e63-422d-b92a-e5d8b713e707
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d1e2738e8cdb546a1dcbb00689e5b4c360ddd04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="operationscope"></a><span data-ttu-id="03569-102">OperationScope</span><span class="sxs-lookup"><span data-stu-id="03569-102">OperationScope</span></span>
<span data-ttu-id="03569-103">Cet exemple montre comment les activités de messagerie, <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>, peuvent être utilisées pour exposer une activité personnalisée existante en tant qu'opération dans un service de workflow.</span><span class="sxs-lookup"><span data-stu-id="03569-103">This sample demonstrates how the messaging activities, <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> can be used to expose an existing custom activity as an operation in a workflow service.</span></span> <span data-ttu-id="03569-104">Cet exemple inclut une nouvelle activité personnalisée appelée `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="03569-104">This sample includes a new custom activity called an `OperationScope`.</span></span> <span data-ttu-id="03569-105">Elle est destinée à faciliter le développement d'un service de workflow en permettant aux utilisateurs de créer le corps de leurs opérations séparément en tant qu'activités personnalisées et de les exposer facilement en tant qu'opérations de service à l'aide de l'activité `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="03569-105">It is intended to ease the development of a workflow service by allowing users to author the body of their operations separately as custom activities and then easily exposing them as service operations using the `OperationScope` activity.</span></span> <span data-ttu-id="03569-106">Par exemple, une activité `Add` personnalisée que prend deux arguments `in` et qui retourne un argument `out` pourrait être exposée en tant qu'opération `Add` sur le service de workflow en le déposant dans un `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="03569-106">For example, a custom `Add` activity that takes two `in` arguments and returns one `out` argument could be exposed as an `Add` operation on the workflow service by dropping it into an `OperationScope`.</span></span>  
  
 <span data-ttu-id="03569-107">L'étendue fonctionne en inspectant l'activité fournie comme étant son corps.</span><span class="sxs-lookup"><span data-stu-id="03569-107">The scope works by inspecting the activity provided as its body.</span></span> <span data-ttu-id="03569-108">Tous les arguments `in` non liés sont supposés être des entrées du message entrant.</span><span class="sxs-lookup"><span data-stu-id="03569-108">Any unbound `in` arguments are assumed to be inputs from the incoming message.</span></span> <span data-ttu-id="03569-109">Tous les arguments `out`, qu'ils soient liés ou non, sont supposés être des sorties dans le message de réponse suivant.</span><span class="sxs-lookup"><span data-stu-id="03569-109">All `out` arguments, regardless of whether they are bound, are assumed to be outputs in the subsequent reply message.</span></span> <span data-ttu-id="03569-110">Le nom de l'opération exposée provient du nom complet de l'activité `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="03569-110">The exposed operation’s name is taken from the display name of the `OperationScope` activity.</span></span> <span data-ttu-id="03569-111">Le résultat final est que l'activité de corps est incluse dans un wrapper dans un <xref:System.ServiceModel.Activities.Receive> et un <xref:System.ServiceModel.Activities.SendReply> avec les paramètres provenant des messages liés aux arguments de l'activité.</span><span class="sxs-lookup"><span data-stu-id="03569-111">The end result is that the body activity is wrapped in a <xref:System.ServiceModel.Activities.Receive> and <xref:System.ServiceModel.Activities.SendReply> with the parameters from the messages bound to the arguments of the activity.</span></span>  
  
 <span data-ttu-id="03569-112">Cet exemple expose un service de workflow à l'aide de points de terminaison HTTP.</span><span class="sxs-lookup"><span data-stu-id="03569-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="03569-113">Pour s'exécuter, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées.</span><span class="sxs-lookup"><span data-stu-id="03569-113">To run, proper URL ACLs must be added.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="03569-114">[Configuration de HTTP et HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span><span class="sxs-lookup"><span data-stu-id="03569-114"> [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353).</span></span> <span data-ttu-id="03569-115">L’exécution de la commande suivante à une invite de commandes avec élévation de privilèges ajoute les ACL appropriées (Vérifiez que votre domaine et le nom d’utilisateur sont substitués pour le domaine %\\%username%).</span><span class="sxs-lookup"><span data-stu-id="03569-115">Executing the following command at an elevated prompt adds the appropriate ACLs (ensure that your Domain and Username are substituted for %DOMAIN%\\%UserName%).</span></span>  
  
 <span data-ttu-id="03569-116">**netsh http ajouter urlacl url = http : / / + : 8000 / utilisateur = domaine %\\%UserName%**</span><span class="sxs-lookup"><span data-stu-id="03569-116">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="03569-117">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="03569-117">To run the sample</span></span>  
  
1.  <span data-ttu-id="03569-118">Ouvrez la solution OperationScope.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="03569-118">Open the OperationScope.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="03569-119">Définir plusieurs projets de démarrage en cliquant sur la solution dans l’Explorateur de solutions et en sélectionnant **définir les projets de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="03569-119">Set multiple start-up projects by right-clicking the solution in Solution Explorer and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="03569-120">Ajoutez Scénario et Scenario_Client (dans cet ordre) en tant que plusieurs projets de démarrage.</span><span class="sxs-lookup"><span data-stu-id="03569-120">Add Scenario and Scenario_Client (in that order) as multiple start-up projects.</span></span>  
  
3.  <span data-ttu-id="03569-121">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="03569-121">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
    > [!WARNING]
    >  <span data-ttu-id="03569-122">Cette étape est requise pour consulter le workflow BankService.xaml en raison de l'activité personnalisée `OperationScope`.</span><span class="sxs-lookup"><span data-stu-id="03569-122">This step is required to view the BankService.xaml workflow due to the custom activity `OperationScope`.</span></span>  
  
4.  <span data-ttu-id="03569-123">Appuyez sur CTRL+F5 pour exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="03569-123">Press CTRL+F5 to run the application.</span></span> <span data-ttu-id="03569-124">La console Scenario_Client vous demande des entrées, et la sortie correspondante s'affiche sur la console Scenario.</span><span class="sxs-lookup"><span data-stu-id="03569-124">The Scenario_Client console prompts you for inputs and the corresponding output is seen in the Scenario console.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="03569-125">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="03569-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03569-126">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="03569-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="03569-127">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="03569-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03569-128">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="03569-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\OperationScope`  
  
## <a name="see-also"></a><span data-ttu-id="03569-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03569-129">See Also</span></span>
