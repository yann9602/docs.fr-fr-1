---
title: "Charge à partir du XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f103ef6-7bed-4f16-ae52-9e665c5a43d7
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19fd22f2756399cc768332cbaa653717611e5e54
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="load-from-xaml"></a><span data-ttu-id="5be1a-102">Charge à partir du XAML</span><span class="sxs-lookup"><span data-stu-id="5be1a-102">Load From XAML</span></span>
<span data-ttu-id="5be1a-103">Cet exemple montre comment charger dynamiquement un workflow XAML sans devoir exécuter l'outil XamlBuildTask.</span><span class="sxs-lookup"><span data-stu-id="5be1a-103">This sample demonstrates how to dynamically load a XAML workflow without having to run the XamlBuildTask tool.</span></span> <span data-ttu-id="5be1a-104">Au lieu de cela, l'exemple appelle la méthode <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="5be1a-104">Instead, the sample calls the <xref:System.Activities.XamlIntegration.ActivityXamlServices.Load%2A> method.</span></span> <span data-ttu-id="5be1a-105">L'exemple est une application cliente [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] qui charge des workflows XAML à l'aide de la classe <xref:System.Activities.XamlIntegration.ActivityXamlServices> et qui les exécute.</span><span class="sxs-lookup"><span data-stu-id="5be1a-105">The sample is a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client application that loads XAML workflows using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class and executes them.</span></span> <span data-ttu-id="5be1a-106">Une fois qu'ils ont été chargés à l'aide de la classe <xref:System.Activities.XamlIntegration.ActivityXamlServices>, un <xref:System.Activities.DynamicActivity%601> pouvant être exécuté est retourné.</span><span class="sxs-lookup"><span data-stu-id="5be1a-106">After they have been loaded using the <xref:System.Activities.XamlIntegration.ActivityXamlServices> class, a <xref:System.Activities.DynamicActivity%601> is returned that can be executed.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5be1a-107">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="5be1a-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="5be1a-108">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution LoadFromXAML.sln.</span><span class="sxs-lookup"><span data-stu-id="5be1a-108">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LoadFromXAML.sln solution file.</span></span>  
  
2.  <span data-ttu-id="5be1a-109">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="5be1a-109">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="5be1a-110">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="5be1a-110">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5be1a-111">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5be1a-111">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5be1a-112">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5be1a-112">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5be1a-113">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5be1a-113">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5be1a-114">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5be1a-114">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\DynamicActivity\LoadFromXAML`