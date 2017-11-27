---
title: "Activité RangeEnumeration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca5b78f4-94fa-4aa7-830d-26039ac422c8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 024cdc9ae082171fb33a63493ac0fbfdd45d3c72
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="rangeenumeration-activity"></a><span data-ttu-id="6cf1f-102">Activité RangeEnumeration</span><span class="sxs-lookup"><span data-stu-id="6cf1f-102">RangeEnumeration Activity</span></span>
<span data-ttu-id="6cf1f-103">Cet exemple montre comment créer une activité personnalisée qui itère au sein d'une collection de nombres. Le tableau suivant détaille les fichiers principaux inclus dans l'exemple.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-103">This sample demonstrates how to create a custom activity that iterates over a collection of numbers.The following table details the main files included in the sample.</span></span>  
  
|<span data-ttu-id="6cf1f-104">Nom de fichier</span><span class="sxs-lookup"><span data-stu-id="6cf1f-104">File name</span></span>|<span data-ttu-id="6cf1f-105">Description</span><span class="sxs-lookup"><span data-stu-id="6cf1f-105">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6cf1f-106">RangeEnumeration.cs</span><span class="sxs-lookup"><span data-stu-id="6cf1f-106">RangeEnumeration.cs</span></span>|<span data-ttu-id="6cf1f-107">Définit une activité personnalisée nommée `RangeEnumeration` qui substitue la classe <xref:System.Activities.NativeActivity> et effectue une boucle sur une série de nombres.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-107">Defines a custom activity named `RangeEnumeration` that overrides the <xref:System.Activities.NativeActivity> class and loops through a series of numbers.</span></span>|  
|<span data-ttu-id="6cf1f-108">RangeEnumerationSample.cs</span><span class="sxs-lookup"><span data-stu-id="6cf1f-108">RangeEnumerationSample.cs</span></span>|<span data-ttu-id="6cf1f-109">Application cliente qui utilise l'activité `RangeEnumeration` pour itérer au sein d'une collection de nombres.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-109">A client application that uses the `RangeEnumeration` activity to iterate over a collection of numbers.</span></span>|  
  
 <span data-ttu-id="6cf1f-110">Le tableau suivant détaille les propriétés de l'activité `RangeEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-110">The following table details the properties of the `RangeEnumeration` activity.</span></span>  
  
|<span data-ttu-id="6cf1f-111">Propriété</span><span class="sxs-lookup"><span data-stu-id="6cf1f-111">Property</span></span>|<span data-ttu-id="6cf1f-112">Description</span><span class="sxs-lookup"><span data-stu-id="6cf1f-112">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6cf1f-113">Démarrer</span><span class="sxs-lookup"><span data-stu-id="6cf1f-113">Start</span></span>|<span data-ttu-id="6cf1f-114">Entier auquel démarrer la boucle.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-114">The integer to start the loop from.</span></span>|  
|<span data-ttu-id="6cf1f-115">Arrêter</span><span class="sxs-lookup"><span data-stu-id="6cf1f-115">Stop</span></span>|<span data-ttu-id="6cf1f-116">Entier auquel arrêter la boucle.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-116">The integer to stop the loop at.</span></span>|  
|<span data-ttu-id="6cf1f-117">Étape</span><span class="sxs-lookup"><span data-stu-id="6cf1f-117">Step</span></span>|<span data-ttu-id="6cf1f-118">Spécifie le volume d'itération à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-118">Specifies how much to iterate each time.</span></span>|  
|<span data-ttu-id="6cf1f-119">Corps</span><span class="sxs-lookup"><span data-stu-id="6cf1f-119">Body</span></span>|<span data-ttu-id="6cf1f-120">Spécifie le code à exécuter pendant chaque itération.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-120">Specifies the code to execute during each iteration.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="6cf1f-121">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="6cf1f-121">To use this sample</span></span>  
  
1.  <span data-ttu-id="6cf1f-122">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution RangeEnumeration.sln.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-122">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the RangeEnumeration.sln solution file.</span></span>  
  
2.  <span data-ttu-id="6cf1f-123">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-123">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="6cf1f-124">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-124">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6cf1f-125">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6cf1f-126">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="6cf1f-127">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6cf1f-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6cf1f-128">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="6cf1f-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\RangeEnumeration`  
  
## <a name="see-also"></a><span data-ttu-id="6cf1f-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cf1f-129">See Also</span></span>
