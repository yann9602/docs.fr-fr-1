---
title: "Utilisation de variables avec un Ruleset .NET Framework 3.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27b56249-22fe-4252-840f-74c0d6c7a6b3
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9b5cc982aaad92258102b313d8fc19a9ff1521a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-variables-with-a-net-framework-35-ruleset"></a><span data-ttu-id="f71a9-102">Utilisation de variables avec un Ruleset .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="f71a9-102">Using Variables with a .NET Framework 3.5 Ruleset</span></span>
<span data-ttu-id="f71a9-103">Cet exemple montre comment créer un workflow qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégrer une activité personnalisée écrite dans [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] et qui utilise une stratégie et des règles.</span><span class="sxs-lookup"><span data-stu-id="f71a9-103">This sample demonstrates how to create a workflow that uses the <xref:System.Activities.Statements.Interop> activity to integrate a custom activity written in [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] that uses policy and rules.</span></span> <span data-ttu-id="f71a9-104">Le workflow passe des données à l'activité personnalisée en liant des variables aux propriétés de dépendance exposées par l'activité personnalisée.</span><span class="sxs-lookup"><span data-stu-id="f71a9-104">The workflow passes data to the custom activity by binding variables to the dependency properties exposed by the custom activity.</span></span>  
  
## <a name="sample-walkthrough"></a><span data-ttu-id="f71a9-105">Exemple de procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="f71a9-105">Sample walkthrough</span></span>  
  
#### <a name="to-examine-travelrulelibrary"></a><span data-ttu-id="f71a9-106">Pour examiner TravelRuleLibrary</span><span class="sxs-lookup"><span data-stu-id="f71a9-106">To examine TravelRuleLibrary</span></span>  
  
1.  <span data-ttu-id="f71a9-107">À l'aide de [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="f71a9-107">Using [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f71a9-108">Ouvrez TravelRuleSet.cs dans le concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="f71a9-108">Open the TravelRuleSet.cs in the workflow designer.</span></span>  
  
     <span data-ttu-id="f71a9-109">Une activité séquentielle personnalisée qui contient un <xref:System.Workflow.Activities.PolicyActivity> s'affiche.</span><span class="sxs-lookup"><span data-stu-id="f71a9-109">A custom sequential activity that contains a <xref:System.Workflow.Activities.PolicyActivity> is displayed.</span></span>  
  
3.  <span data-ttu-id="f71a9-110">Double-cliquez sur l'activité de stratégie DiscountPolicy pour examiner les règles.</span><span class="sxs-lookup"><span data-stu-id="f71a9-110">Double-click the DiscountPolicy policy activity to examine the rules.</span></span>  
  
     <span data-ttu-id="f71a9-111">L'éditeur de règles s'affiche pour présenter les règles.</span><span class="sxs-lookup"><span data-stu-id="f71a9-111">The Rules editor pops up to show the rules.</span></span>  
  
4.  <span data-ttu-id="f71a9-112">Bouton droit sur le `DiscountPolicy` et sélectionnez le **afficher le Code** option pour examiner le code en regard de code c# pour l’activité.</span><span class="sxs-lookup"><span data-stu-id="f71a9-112">Right click the `DiscountPolicy` and select the **View Code** option to examine the code beside C# code for the activity.</span></span>  
  
     <span data-ttu-id="f71a9-113">Observez le paramètre de propriété de dépendance pour `DiscountLevel`.</span><span class="sxs-lookup"><span data-stu-id="f71a9-113">Observe the dependency property setting for `DiscountLevel`.</span></span> <span data-ttu-id="f71a9-114">Cela est équivalent à des arguments dans le [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f71a9-114">This is equivalent to arguments in [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f71a9-115">arguments, consultez [Variables et Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f71a9-115"> arguments, see [Variables and Arguments](../../../../docs/framework/windows-workflow-foundation/variables-and-arguments.md).</span></span>  
  
## <a name="interopwith35ruleset"></a><span data-ttu-id="f71a9-116">InteropWith35RuleSet</span><span class="sxs-lookup"><span data-stu-id="f71a9-116">InteropWith35RuleSet</span></span>  
 <span data-ttu-id="f71a9-117">C'est un projet de workflow séquentiel qui utilise l'activité <xref:System.Activities.Statements.Interop> pour une intégration à l'ensemble de règles personnalisé créé dans le projet `TravelRuleLibrary`.</span><span class="sxs-lookup"><span data-stu-id="f71a9-117">This is a sequential workflow project that uses the <xref:System.Activities.Statements.Interop> activity to integrate with the custom Rule set created in the `TravelRuleLibrary` project.</span></span> <span data-ttu-id="f71a9-118">Les variables sont créées sur l'activité <xref:System.Activities.Statements.Sequence> de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="f71a9-118">Variables are created on the top level <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="f71a9-119">L'activité <xref:System.Activities.Statements.Interop> est utilisée pour une intégration à l'activité `TravelRuleSet`.</span><span class="sxs-lookup"><span data-stu-id="f71a9-119">The <xref:System.Activities.Statements.Interop> activity is used to integrate with the `TravelRuleSet` activity.</span></span> <span data-ttu-id="f71a9-120">Les variables déclarées sur <xref:System.Activities.Statements.Sequence> sont utilisées pour créer une liaison aux propriétés de dépendance.</span><span class="sxs-lookup"><span data-stu-id="f71a9-120">The variables that are declared on the <xref:System.Activities.Statements.Sequence> are used to bind to the dependency properties.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="f71a9-121">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="f71a9-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="f71a9-122">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InteropWith35RuleSet.sln.</span><span class="sxs-lookup"><span data-stu-id="f71a9-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InteropWith35RuleSet.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f71a9-123">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="f71a9-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f71a9-124">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="f71a9-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f71a9-125">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f71a9-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f71a9-126">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f71a9-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f71a9-127">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f71a9-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f71a9-128">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f71a9-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InteropWith35RuleSet`  
  
## <a name="see-also"></a><span data-ttu-id="f71a9-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f71a9-129">See Also</span></span>
