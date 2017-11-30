---
title: "Activité personnalisée Hello World"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72b1dd0a-9aad-47d5-95a9-a1024ee1d0a1
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75f4a75a38b79e7b7ab18ac2ce3eff2a13aab15f
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="hello-world-custom-activity"></a><span data-ttu-id="f1d54-102">Activité personnalisée Hello World</span><span class="sxs-lookup"><span data-stu-id="f1d54-102">Hello World Custom Activity</span></span>
<span data-ttu-id="f1d54-103">Cet exemple illustre plusieurs fonctionnalités clés de [!INCLUDE[wf](../../../../includes/wf-md.md)], notamment la façon de créer une activité personnalisée simple.</span><span class="sxs-lookup"><span data-stu-id="f1d54-103">This sample demonstrates several key features of [!INCLUDE[wf](../../../../includes/wf-md.md)], including how to create a simple custom activity.</span></span> <span data-ttu-id="f1d54-104">Certaines des fonctionnalités présentées dans cet exemple créent une activité personnalisée en C# et utilisent les arguments `in` et `out` (<xref:System.Activities.InArgument> et <xref:System.Activities.OutArgument>).</span><span class="sxs-lookup"><span data-stu-id="f1d54-104">Some of the features demonstrated in this sample are creating a custom activity in C# and using `in` and `out` arguments (<xref:System.Activities.InArgument> and <xref:System.Activities.OutArgument>).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1d54-105">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f1d54-105">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f1d54-106">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f1d54-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1d54-107">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="f1d54-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1d54-108">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f1d54-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Code-Bodied\HelloWorld`  
  
## <a name="creating-a-workflow-in-code"></a><span data-ttu-id="f1d54-109">Création d'un workflow dans le code</span><span class="sxs-lookup"><span data-stu-id="f1d54-109">Creating a Workflow in Code</span></span>  
 <span data-ttu-id="f1d54-110">Dans cet exemple, deux activités personnalisées sont créées à l'aide de code C#.</span><span class="sxs-lookup"><span data-stu-id="f1d54-110">In this sample, two custom activities are created using C# code.</span></span> <span data-ttu-id="f1d54-111">Les deux activités personnalisées héritent directement ou indirectement d'<xref:System.Activities.Activity%601> pour retourner une valeur unique.</span><span class="sxs-lookup"><span data-stu-id="f1d54-111">Both custom activities inherit directly or indirectly from <xref:System.Activities.Activity%601> to return a single value.</span></span> <span data-ttu-id="f1d54-112">L'avantage de l'utilisation de la valeur de retour générique, plutôt que d'hériter de la classe <xref:System.Activities.Activity> non générique, est que certaines activités (telles que <xref:System.Activities.Statements.Assign>) peuvent accéder à la valeur de retour lorsqu'elles sont utilisées dans le cadre d'une activité composée.</span><span class="sxs-lookup"><span data-stu-id="f1d54-112">The advantage of using the generic return value, instead of inheriting from the non-generic <xref:System.Activities.Activity> class, is that some activities (such as <xref:System.Activities.Statements.Assign>) are able to access the return value when used as part of a composed activity.</span></span>  
  
 <span data-ttu-id="f1d54-113">AppendString</span><span class="sxs-lookup"><span data-stu-id="f1d54-113">AppendString</span></span>  
 <span data-ttu-id="f1d54-114">Cette activité hérite d'<xref:System.Activities.Activity%601>, et utilise une activité <xref:System.Activities.Statements.Assign> qui concatène deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="f1d54-114">This activity inherits from <xref:System.Activities.Activity%601>, and uses an <xref:System.Activities.Statements.Assign> activity that concatenates two strings together.</span></span>  
  
 <span data-ttu-id="f1d54-115">PrependString</span><span class="sxs-lookup"><span data-stu-id="f1d54-115">Prepend String</span></span>  
 <span data-ttu-id="f1d54-116">Cette activité hérite directement de <xref:System.Activities.CodeActivity%601>, et crée des fonctionnalités semblables à l'activité `AppendString`, laquelle utilise la logique implémentée au lieu d'être composée d'une activité préexistante.</span><span class="sxs-lookup"><span data-stu-id="f1d54-116">This activity inherits directly from <xref:System.Activities.CodeActivity%601>, and creates similar functionality to the `AppendString` activity, which uses logic implemented in code rather than being composed of a pre-existing activity.</span></span>  
  
 <span data-ttu-id="f1d54-117">Les fichiers suivants sont inclus dans ce projet :</span><span class="sxs-lookup"><span data-stu-id="f1d54-117">The following files are included in this project.</span></span>  
  
 <span data-ttu-id="f1d54-118">AppendString.cs</span><span class="sxs-lookup"><span data-stu-id="f1d54-118">AppendString.cs</span></span>  
 <span data-ttu-id="f1d54-119">Activité personnalisée qui ajoute des chaînes ensemble.</span><span class="sxs-lookup"><span data-stu-id="f1d54-119">The custom activity that appends strings together.</span></span> <span data-ttu-id="f1d54-120">Il accepte une chaîne et combine avec une chaîne de texte littéral « says hello world », pour former un message complet en tant que sortie.</span><span class="sxs-lookup"><span data-stu-id="f1d54-120">It takes in a string and combines it with a literal text string " says hello world" to form a complete message as output.</span></span>  
  
 <span data-ttu-id="f1d54-121">PrependString.cs</span><span class="sxs-lookup"><span data-stu-id="f1d54-121">PrependString.cs</span></span>  
 <span data-ttu-id="f1d54-122">Cette activité fait précéder une chaîne d'entrée d'une chaîne prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="f1d54-122">This activity prefixes a predefined string to an input string.</span></span>  
  
 <span data-ttu-id="f1d54-123">Sequence1.xaml</span><span class="sxs-lookup"><span data-stu-id="f1d54-123">Sequence1.xaml</span></span>  
 <span data-ttu-id="f1d54-124">Workflow qui utilise les activités personnalisées `AppendString` et `PrependString`.</span><span class="sxs-lookup"><span data-stu-id="f1d54-124">A workflow that uses the `AppendString` and `PrependString` custom activities.</span></span>  
  
 <span data-ttu-id="f1d54-125">Program.cs</span><span class="sxs-lookup"><span data-stu-id="f1d54-125">Program.cs</span></span>  
 <span data-ttu-id="f1d54-126">Programme qui exécute le workflow.</span><span class="sxs-lookup"><span data-stu-id="f1d54-126">A program that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="f1d54-127">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="f1d54-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="f1d54-128">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution HelloWorld.sln.</span><span class="sxs-lookup"><span data-stu-id="f1d54-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the HelloWorld.sln solution file.</span></span>  
  
2.  <span data-ttu-id="f1d54-129">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="f1d54-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="f1d54-130">Pour exécuter la solution, appuyez sur F5.</span><span class="sxs-lookup"><span data-stu-id="f1d54-130">To run the solution, press F5.</span></span>