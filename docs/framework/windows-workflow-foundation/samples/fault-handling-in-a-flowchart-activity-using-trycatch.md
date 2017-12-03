---
title: "Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d8bccc1b9505f685fd4e358216e76c22ec751e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a><span data-ttu-id="a7412-102">Gestion des erreurs dans une activité Flowchart à l'aide de TryCatch</span><span class="sxs-lookup"><span data-stu-id="a7412-102">Fault Handling in a Flowchart Activity Using TryCatch</span></span>
<span data-ttu-id="a7412-103">Cet exemple montre comment l'activité <xref:System.Activities.Statements.TryCatch> peut être utilisée dans une activité de flux de contrôle complexe.</span><span class="sxs-lookup"><span data-stu-id="a7412-103">This sample shows how the <xref:System.Activities.Statements.TryCatch> activity can be used within a complex control flow activity.</span></span>  
  
 <span data-ttu-id="a7412-104">Dans cet exemple, un code promotionnel et un nombre d'enfants sont passés en tant que variables à une activité <xref:System.Activities.Statements.Flowchart> qui calcule une remise basée sur des formules qui correspondent au code promotionnel.</span><span class="sxs-lookup"><span data-stu-id="a7412-104">In this sample, a promotion code and number of children are passed as variables to a <xref:System.Activities.Statements.Flowchart> activity that calculates a discount based on formulae that correspond to the promotion code.</span></span> <span data-ttu-id="a7412-105">L'exemple inclut les versions du code impératif et du concepteur de workflow de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a7412-105">The sample includes imperative code and workflow designer versions of the sample.</span></span>  
  
 <span data-ttu-id="a7412-106">Le tableau suivant décrit en détail les variables pour l'activité `CreateFlowchartWithFaults`.</span><span class="sxs-lookup"><span data-stu-id="a7412-106">The following table details the variables for the `CreateFlowchartWithFaults` activity.</span></span>  
  
|<span data-ttu-id="a7412-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7412-107">Parameters</span></span>|<span data-ttu-id="a7412-108">Description</span><span class="sxs-lookup"><span data-stu-id="a7412-108">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="a7412-109">promoCode</span><span class="sxs-lookup"><span data-stu-id="a7412-109">promoCode</span></span>|<span data-ttu-id="a7412-110">Code promotionnel.</span><span class="sxs-lookup"><span data-stu-id="a7412-110">The promotion code.</span></span> <span data-ttu-id="a7412-111">Type : chaîne</span><span class="sxs-lookup"><span data-stu-id="a7412-111">Type: String</span></span><br /><br /> <span data-ttu-id="a7412-112">Valeurs possibles avec la description entre parenthèses :</span><span class="sxs-lookup"><span data-stu-id="a7412-112">The possible values with description in parentheses:</span></span><br /><br /> <span data-ttu-id="a7412-113">-Unique (unique)</span><span class="sxs-lookup"><span data-stu-id="a7412-113">-   Single (Single)</span></span><br /><span data-ttu-id="a7412-114">-MNK (marié avec aucune enfants).</span><span class="sxs-lookup"><span data-stu-id="a7412-114">-   MNK (Married with no kids.)</span></span><br /><span data-ttu-id="a7412-115">-MWK (marié avec enfants).</span><span class="sxs-lookup"><span data-stu-id="a7412-115">-   MWK (Married with kids.)</span></span>|  
|<span data-ttu-id="a7412-116">numKids</span><span class="sxs-lookup"><span data-stu-id="a7412-116">numKids</span></span>|<span data-ttu-id="a7412-117">Nombre d'enfants.</span><span class="sxs-lookup"><span data-stu-id="a7412-117">The number of children.</span></span> <span data-ttu-id="a7412-118">Type : int</span><span class="sxs-lookup"><span data-stu-id="a7412-118">Type: int</span></span>|  
  
 <span data-ttu-id="a7412-119">L'activité `CreateFlowchartWithFaults` utilise une activité <xref:System.Activities.Statements.FlowSwitch%601> qui active l'argument `promoCode` et calcule la remise à l'aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="a7412-119">The `CreateFlowchartWithFaults` activity uses a <xref:System.Activities.Statements.FlowSwitch%601> activity that switches on the `promoCode` argument and calculates the discount using the following formula.</span></span>  
  
|<span data-ttu-id="a7412-120">Valeur de `promoCode`</span><span class="sxs-lookup"><span data-stu-id="a7412-120">Value of `promoCode`</span></span>|<span data-ttu-id="a7412-121">Remise (%)</span><span class="sxs-lookup"><span data-stu-id="a7412-121">Discount (%)</span></span>|  
|--------------------------|--------------------|  
|<span data-ttu-id="a7412-122">Single</span><span class="sxs-lookup"><span data-stu-id="a7412-122">Single</span></span>|<span data-ttu-id="a7412-123">10</span><span class="sxs-lookup"><span data-stu-id="a7412-123">10</span></span>|  
|<span data-ttu-id="a7412-124">MNK</span><span class="sxs-lookup"><span data-stu-id="a7412-124">MNK</span></span>|<span data-ttu-id="a7412-125">15</span><span class="sxs-lookup"><span data-stu-id="a7412-125">15</span></span>|  
|<span data-ttu-id="a7412-126">MWK</span><span class="sxs-lookup"><span data-stu-id="a7412-126">MWK</span></span>|<span data-ttu-id="a7412-127">15 + (1 – 1 /`numberOfKids`)\*10 **Remarque :** potentiellement, ce calcul peut lever un <xref:System.DivideByZeroException>.</span><span class="sxs-lookup"><span data-stu-id="a7412-127">15 + (1 – 1/`numberOfKids`)\*10 **Note:**  Potentially, this calculation can throw a <xref:System.DivideByZeroException>.</span></span> <span data-ttu-id="a7412-128">Par conséquent, le calcul de la remise est inclus dans un wrapper dans une activité <xref:System.Activities.Statements.TryCatch> qui intercepte l'exception <xref:System.DivideByZeroException> et définit la remise à zéro.</span><span class="sxs-lookup"><span data-stu-id="a7412-128">So, the discount calculation is wrapped in a <xref:System.Activities.Statements.TryCatch> activity that catches the <xref:System.DivideByZeroException> exception and sets the discount to zero.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a7412-129">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="a7412-129">To use this sample</span></span>  
  
1.  <span data-ttu-id="a7412-130">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution FlowchartWithFaultHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="a7412-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the FlowchartWithFaultHandling.sln solution file.</span></span>  
  
2.  <span data-ttu-id="a7412-131">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="a7412-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="a7412-132">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="a7412-132">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7412-133">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a7412-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a7412-134">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="a7412-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a7412-135">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a7412-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a7412-136">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="a7412-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a><span data-ttu-id="a7412-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7412-137">See Also</span></span>  
 [<span data-ttu-id="a7412-138">Workflows d’organigramme</span><span class="sxs-lookup"><span data-stu-id="a7412-138">Flowchart Workflows</span></span>](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [<span data-ttu-id="a7412-139">Exceptions</span><span class="sxs-lookup"><span data-stu-id="a7412-139">Exceptions</span></span>](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
