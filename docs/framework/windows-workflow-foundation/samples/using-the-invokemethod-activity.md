---
title: "Utilisation de l'activité InvokeMethod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6643550-d043-4ac7-8069-9c55ebbb4233
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ba0c2333c14eaebdb6409323bb6b92aa2b29d2ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="using-the-invokemethod-activity"></a><span data-ttu-id="58da7-102">Utilisation de l'activité InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="58da7-102">Using the InvokeMethod Activity</span></span>
<span data-ttu-id="58da7-103">Cet exemple montre comment utiliser le <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité qui permet d’appeler des méthodes publiques dans des classes publiques.</span><span class="sxs-lookup"><span data-stu-id="58da7-103">This sample demonstrates how to use the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity to invoke public methods in public classes.</span></span> <span data-ttu-id="58da7-104">Le <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité permet à un workflow à appeler des méthodes sur des objets, passer des paramètres, obtenir la valeur de retour, spécifier des types pour les méthodes génériques et indiquer si la méthode est synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="58da7-104">The <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity allows a workflow to call methods against objects, pass in parameters, get the return value, specify types for generic methods, and specify whether the method is synchronous or asynchronous.</span></span> 
  
<span data-ttu-id="58da7-105">Il existe une version non générique de la <xref:System.Activities.Statements.InvokeMethod> activité où la valeur de retour est définie pour le <xref:System.Activities.Statements.InvokeMethod.Result%2A> propriété et une version générique de la <!--zz <xref:System.Activities.Statements.InvokeMethod%601> --> [ <code>System.Activities.Statements.InvokeMethod\`1</code> ](https://msdn.microsoft.com/library/dd647677.aspx) activité où la valeur de retour est retournée via le <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> --> [ <code>System.Activities.Statements.InvokeMethod\`1.Result</code> ](https://msdn.microsoft.com/library/dd987724.aspx) propriété de type `TResult`.</span><span class="sxs-lookup"><span data-stu-id="58da7-105">There is a non-generic version of the <xref:System.Activities.Statements.InvokeMethod> activity where the return value is set to the <xref:System.Activities.Statements.InvokeMethod.Result%2A> property and a generic version of the <!--zz <xref:System.Activities.Statements.InvokeMethod%601> -->[<code>System.Activities.Statements.InvokeMethod\`1</code>](https://msdn.microsoft.com/library/dd647677.aspx) activity where the return value is returned through the <!--zz <xref:System.Activities.Statements.InvokeMethod.Result%601.Result%2A> -->[<code>System.Activities.Statements.InvokeMethod\`1.Result</code>](https://msdn.microsoft.com/library/dd987724.aspx) property of type `TResult`.</span></span> 
  
 <span data-ttu-id="58da7-106">Cet exemple montre comment appeler différents types de méthode.</span><span class="sxs-lookup"><span data-stu-id="58da7-106">This sample demonstrates how to call various method types.</span></span> <span data-ttu-id="58da7-107">La liste suivante détaille les types de méthode illustrés dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="58da7-107">The following list details the method types demonstrated in this sample:</span></span>  
  
-   <span data-ttu-id="58da7-108">Appeler une méthode d'instance sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="58da7-108">Invoke an instance method without parameters.</span></span>  
  
-   <span data-ttu-id="58da7-109">Appeler une méthode d'instance avec deux paramètres (System.String et System.Int32).</span><span class="sxs-lookup"><span data-stu-id="58da7-109">Invoke an instance method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="58da7-110">Appeler une méthode d'instance avec deux paramètres (System.String et System.Int32) et un tableau de paramètres de type System.String[].</span><span class="sxs-lookup"><span data-stu-id="58da7-110">Invoke an instance method with two parameters (System.String and System.Int32) and a parameter array of type System.String[].</span></span>  
  
-   <span data-ttu-id="58da7-111">Appeler une méthode d'instance avec deux paramètres (deux nombres System.Int32) et un résultat de type System.Int32.</span><span class="sxs-lookup"><span data-stu-id="58da7-111">Invoke an instance method with two parameters (two System.Int32 numbers) and a result of type System.Int32.</span></span>  
  
     <span data-ttu-id="58da7-112">La valeur de retour est liée à une variable et imprimée sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="58da7-112">The return value is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="58da7-113">Appeler une méthode statique avec deux paramètres (System.String et System.Int32).</span><span class="sxs-lookup"><span data-stu-id="58da7-113">Invoke a static method with two parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="58da7-114">Appeler une méthode d'instance avec un paramètre générique (System.String).</span><span class="sxs-lookup"><span data-stu-id="58da7-114">Invoke an instance method with one generic parameter (System.String).</span></span>  
  
-   <span data-ttu-id="58da7-115">Appeler une méthode statique avec deux paramètres génériques (System.String et System.Int32).</span><span class="sxs-lookup"><span data-stu-id="58da7-115">Invoke a static method with two generic parameters (System.String and System.Int32).</span></span>  
  
-   <span data-ttu-id="58da7-116">Appeler une méthode d'instance qui a un paramètre passée par référence (System.String).</span><span class="sxs-lookup"><span data-stu-id="58da7-116">Invoke an instance method that has one parameter passed by reference (System.String).</span></span>  
  
     <span data-ttu-id="58da7-117">Le paramètre référencé est lié à une variable et imprimé sur la console à l'aide de l'activité <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="58da7-117">The referenced parameter is bound to a variable and printed to the console using the <xref:System.Activities.Statements.WriteLine> activity.</span></span>  
  
-   <span data-ttu-id="58da7-118">Appeler une méthode d'instance asynchrone.</span><span class="sxs-lookup"><span data-stu-id="58da7-118">Invoke an asynchronous instance method.</span></span>  
  
## <a name="to-use-this-sample"></a><span data-ttu-id="58da7-119">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="58da7-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="58da7-120">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution InvokeMethodUsage.sln.</span><span class="sxs-lookup"><span data-stu-id="58da7-120">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the InvokeMethodUsage.sln solution file.</span></span>  
  
2.  <span data-ttu-id="58da7-121">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="58da7-121">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="58da7-122">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="58da7-122">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="58da7-123">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="58da7-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58da7-124">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="58da7-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="58da7-125">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="58da7-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58da7-126">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="58da7-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\InvokeMethod`