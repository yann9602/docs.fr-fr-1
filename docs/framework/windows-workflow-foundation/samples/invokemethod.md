---
title: InvokeMethod
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04988eb3-65f8-456d-b1bd-509f5d05a57c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b90ebec929b310442cde2be8d96386e016a9bbb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="invokemethod"></a><span data-ttu-id="71343-102">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="71343-102">InvokeMethod</span></span>
<span data-ttu-id="71343-103">Cet exemple présente les différentes façons d'utiliser l'activité <xref:System.Activities.Statements.InvokeMethod> pour appeler les méthodes d'une classe.</span><span class="sxs-lookup"><span data-stu-id="71343-103">This sample shows the different ways of using the <xref:System.Activities.Statements.InvokeMethod> activity to invoke methods of a class.</span></span>  
  
 <span data-ttu-id="71343-104">Une méthode appartient à une classe et représente un ensemble contenu d'opérations.</span><span class="sxs-lookup"><span data-stu-id="71343-104">A method belongs to a class and represents a contained set of operations.</span></span> <span data-ttu-id="71343-105">L'activité <xref:System.Activities.Statements.InvokeMethod> vous permet d'appeler des méthodes sur des objets ou des types, de passer des paramètres et d'obtenir la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="71343-105">The <xref:System.Activities.Statements.InvokeMethod> activity gives you the ability to call methods against objects or types, pass in parameters, and get the return value.</span></span> <span data-ttu-id="71343-106">Les méthodes peuvent être appelées de façon synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="71343-106">Methods can be invoked synchronously or asynchronously.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="71343-107">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="71343-107">Sample Details</span></span>  
 <span data-ttu-id="71343-108">Cet exemple utilise l'activité <xref:System.Activities.Statements.InvokeMethod> pour effectuer les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="71343-108">This sample uses the <xref:System.Activities.Statements.InvokeMethod> activity to perform the following scenarios:</span></span>  
  
1.  <span data-ttu-id="71343-109">Appeler une méthode d'instance sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="71343-109">Invoke an instance method without parameters.</span></span>  
  
2.  <span data-ttu-id="71343-110">Appeler une méthode d'instance avec deux paramètres (<xref:System.String> et <xref:System.Int32>).</span><span class="sxs-lookup"><span data-stu-id="71343-110">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>).</span></span>  
  
3.  <span data-ttu-id="71343-111">Appeler une méthode d'instance avec deux paramètres (<xref:System.String> et <xref:System.Int32>) et un tableau de paramètres de type <xref:System.String>[].</span><span class="sxs-lookup"><span data-stu-id="71343-111">Invoke an instance method with two parameters (<xref:System.String> and <xref:System.Int32>) and a parameter array of type <xref:System.String>[].</span></span>  
  
4.  <span data-ttu-id="71343-112">Appeler une méthode d'instance avec deux paramètres de type <xref:System.Int32> et un résultat de type <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="71343-112">Invoke an instance method with two parameters of type <xref:System.Int32> and a result of type <xref:System.Int32>.</span></span> <span data-ttu-id="71343-113">Dans ce scénario, la valeur de résultat est liée à une variable et utilisée dans une autre activité.</span><span class="sxs-lookup"><span data-stu-id="71343-113">In this scenario, the result value is bound to a variable and used in another activity.</span></span> <span data-ttu-id="71343-114">Elle est affichée dans la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="71343-114">It is displayed in the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
5.  <span data-ttu-id="71343-115">Appeler une méthode statique avec deux paramètres de type <xref:System.String> et <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="71343-115">Invoke a static method with two parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
6.  <span data-ttu-id="71343-116">Appeler une méthode d'instance avec un paramètre générique de type <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="71343-116">Invoke an instance method with one generic parameter of type <xref:System.String>.</span></span>  
  
7.  <span data-ttu-id="71343-117">Appeler une méthode statique avec deux paramètres génériques de type <xref:System.String> et <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="71343-117">Invoke a static method with two generic parameters of type <xref:System.String> and <xref:System.Int32>.</span></span>  
  
8.  <span data-ttu-id="71343-118">Appeler une méthode d'instance qui a un paramètre passée par référence de type <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="71343-118">Invoke an instance method that has one parameter passed by reference of type <xref:System.String>.</span></span> <span data-ttu-id="71343-119">Dans ce scénario, le paramètre de référence est lié à une variable (`outParam`) et utilisé dans une autre activité.</span><span class="sxs-lookup"><span data-stu-id="71343-119">In this scenario, the reference parameter is bound to a variable (`outParam`) and used in another activity.</span></span> <span data-ttu-id="71343-120">Il est affiché sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="71343-120">It is displayed on the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
9. <span data-ttu-id="71343-121">Appeler une méthode d'instance asynchrone.</span><span class="sxs-lookup"><span data-stu-id="71343-121">Invoke an asynchronous instance method.</span></span>  
  
10. <span data-ttu-id="71343-122">Appeler deux méthodes différentes sur la même instance d'un objet à l'aide de deux activités <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="71343-122">Invoke two different methods on the same instance of an object using two <xref:System.Activities.Statements.InvokeMethod> activities.</span></span>  
  
11. <span data-ttu-id="71343-123">Stocker une valeur dans une instance d'un objet.</span><span class="sxs-lookup"><span data-stu-id="71343-123">Store a value in an instance of an object.</span></span>  
  
12. <span data-ttu-id="71343-124">Récupérer une valeur à partir d'une instance d'un objet.</span><span class="sxs-lookup"><span data-stu-id="71343-124">Retrieve a value from an instance of an object.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="71343-125">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="71343-125">To use this sample</span></span>  
 <span data-ttu-id="71343-126">Cet exemple est fourni dans deux versions.</span><span class="sxs-lookup"><span data-stu-id="71343-126">This sample is provided in two versions.</span></span> <span data-ttu-id="71343-127">La première version de cet exemple, qui illustre l'utilisation de <xref:System.Activities.Statements.InvokeMethod> par le biais de code C# à l'aide du modèle de programmation [!INCLUDE[wf](../../../../includes/wf-md.md)], se trouve dans le dossier CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="71343-127">The first version of this sample demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> through C# code using the [!INCLUDE[wf](../../../../includes/wf-md.md)] programming model and can be found under the CodedWorkflow\CS folder.</span></span> <span data-ttu-id="71343-128">La deuxième version, qui illustre l'utilisation de <xref:System.Activities.Statements.InvokeMethod> à l'aide de code XAML, se trouve dans le dossier DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="71343-128">The second version demonstrates the usage of <xref:System.Activities.Statements.InvokeMethod> using XAML and can be found under the DesignerWorkflow\CS folder.</span></span>  
  
#### <a name="to-run-the-coded-workflow-sample"></a><span data-ttu-id="71343-129">Pour exécuter l'exemple de workflow encodé</span><span class="sxs-lookup"><span data-stu-id="71343-129">To run the coded workflow sample</span></span>  
  
1.  <span data-ttu-id="71343-130">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InvokeMethodUsage.sln situé dans le dossier CodedWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="71343-130">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the CodedWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="71343-131">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="71343-131">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="71343-132">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="71343-132">To run the solution, press CTRL+F5.</span></span>  
  
#### <a name="to-run-the-designer-workflow-sample"></a><span data-ttu-id="71343-133">Pour exécuter l'exemple de concepteur de workflow</span><span class="sxs-lookup"><span data-stu-id="71343-133">To run the designer workflow sample</span></span>  
  
1.  <span data-ttu-id="71343-134">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InvokeMethodUsage.sln situé dans le dossier DesignerWorkflow\CS.</span><span class="sxs-lookup"><span data-stu-id="71343-134">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file in the DesignerWorkflow\CS folder.</span></span>  
  
2.  <span data-ttu-id="71343-135">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="71343-135">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="71343-136">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="71343-136">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71343-137">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="71343-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71343-138">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="71343-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="71343-139">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="71343-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71343-140">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="71343-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`