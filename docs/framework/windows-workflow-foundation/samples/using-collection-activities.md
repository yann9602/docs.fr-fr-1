---
title: "Utilisation d’activités de collection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84218f16f846e640baea663efc7153a40a6c764a
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-collection-activities"></a><span data-ttu-id="e2794-102">Utilisation d’activités de collection</span><span class="sxs-lookup"><span data-stu-id="e2794-102">Using Collection Activities</span></span>
<span data-ttu-id="e2794-103">Cet exemple montre comment utiliser les activités de collection (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601> et <xref:System.Activities.Statements.RemoveFromCollection%601>) avec une classe qui implémente l'interface <xref:System.Collections.ICollection> et comment créer une activité personnalisée qui itère au sein d'une collection pour imprimer le contenu de chaque élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-103">This sample demonstrates how to use the collection activities (<xref:System.Activities.Statements.AddToCollection%601>, <xref:System.Activities.Statements.ClearCollection%601>, <xref:System.Activities.Statements.ExistsInCollection%601>, and <xref:System.Activities.Statements.RemoveFromCollection%601>) with a class that implements the <xref:System.Collections.ICollection> interface and how to create a custom activity that iterates over a collection to print out the contents of each element in the collection.</span></span> <span data-ttu-id="e2794-104">L'activité personnalisée nommée `PrintCollection`imprime sur la console les membres d'élément d'une collection nommée `Numbers`.</span><span class="sxs-lookup"><span data-stu-id="e2794-104">The custom activity, which is named `PrintCollection`, prints to the console the item members of a collection named `Numbers`.</span></span>  
  
 <span data-ttu-id="e2794-105">Le tableau suivant décrit les quatre activités qui fournissent la manipulation de collection pour les workflows.</span><span class="sxs-lookup"><span data-stu-id="e2794-105">The following table describes the four activities that provide collection manipulation for workflows.</span></span>  
  
|<span data-ttu-id="e2794-106">Nom de l'activité</span><span class="sxs-lookup"><span data-stu-id="e2794-106">Activity name</span></span>|<span data-ttu-id="e2794-107">Description</span><span class="sxs-lookup"><span data-stu-id="e2794-107">Description</span></span>|  
|-------------------|-----------------|  
|<xref:System.Activities.Statements.AddToCollection%601>|<span data-ttu-id="e2794-108">Ajoute un élément à une collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-108">Adds an item to a collection.</span></span>|  
|<xref:System.Activities.Statements.ClearCollection%601>|<span data-ttu-id="e2794-109">Efface tous les éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-109">Clears all items in a collection</span></span>|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|<span data-ttu-id="e2794-110">Retourne `true` si l'élément spécifié existe dans la collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-110">Returns `true` if specified item exists in collection.</span></span>|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|<span data-ttu-id="e2794-111">Supprime un élément d’une collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-111">Removes an item from a collection.</span></span>|  
  
 <span data-ttu-id="e2794-112">L'exemple se compose de deux solutions, une sous le répertoire CodedWorkflow et l'autre sous le répertoire DesignerWorkflow.</span><span class="sxs-lookup"><span data-stu-id="e2794-112">The sample consists of two solutions, one under the CodedWorkflow directory and the other under the DesignerWorkflow directory.</span></span> <span data-ttu-id="e2794-113">Elles illustrent deux façons différentes d'utiliser les activités dans le même but.</span><span class="sxs-lookup"><span data-stu-id="e2794-113">They demonstrate two different ways of using the activities for the same purposes.</span></span>  
  
|<span data-ttu-id="e2794-114">Solution</span><span class="sxs-lookup"><span data-stu-id="e2794-114">Solution</span></span>|<span data-ttu-id="e2794-115">Description</span><span class="sxs-lookup"><span data-stu-id="e2794-115">Description</span></span>|<span data-ttu-id="e2794-116">Fichiers principaux</span><span class="sxs-lookup"><span data-stu-id="e2794-116">Main Files</span></span>|  
|-|-|-|  
|<span data-ttu-id="e2794-117">CodedWorkflow</span><span class="sxs-lookup"><span data-stu-id="e2794-117">CodedWorkflow</span></span>|<span data-ttu-id="e2794-118">Exemple d'application cliente qui montre comment appeler les activités de collection par programmation.</span><span class="sxs-lookup"><span data-stu-id="e2794-118">Sample client application that demonstrates how to invoke the collection activities programmatically.</span></span>|<span data-ttu-id="e2794-119">**PrintCollection.cs**: activité d’assistance pour imprimer sur la console chaque élément dans une collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-119">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="e2794-120">**Program.cs**: crée par programmation une activité de séquence qui contient une série d’activités de collection et l’exécute.</span><span class="sxs-lookup"><span data-stu-id="e2794-120">**Program.cs**: programmatically builds a sequence activity that contains a series of collection activities, and executes it.</span></span>|  
|<span data-ttu-id="e2794-121">DesignerWorkflow</span><span class="sxs-lookup"><span data-stu-id="e2794-121">DesignerWorkflow</span></span>|<span data-ttu-id="e2794-122">Exemple d'application cliente qui montre comment utiliser de façon déclarative les activités de collection dans le concepteur de workflow.</span><span class="sxs-lookup"><span data-stu-id="e2794-122">Sample client application that demonstrates how to use the collection activities declaratively in the workflow designer.</span></span>|<span data-ttu-id="e2794-123">**CollectionWorkflow.xaml**: un workflow créé de façon déclarative avec le concepteur qui utilise les activités de collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-123">**CollectionWorkflow.xaml**: a workflow created declaratively with the designer that uses the collection activities.</span></span><br /><br /> <span data-ttu-id="e2794-124">**PrintCollection.cs**: activité d’assistance pour imprimer sur la console chaque élément dans une collection.</span><span class="sxs-lookup"><span data-stu-id="e2794-124">**PrintCollection.cs**: helper activity to print out to the console every item in a collection.</span></span><br /><br /> <span data-ttu-id="e2794-125">**Program.cs**: appelle le workflow décrit dans CollectionWorkflow.xaml.</span><span class="sxs-lookup"><span data-stu-id="e2794-125">**Program.cs**: invokes the workflow described in CollectionWorkflow.xaml.</span></span>|  
  
 <span data-ttu-id="e2794-126">Dans la démonstration, les membres d'élément de collection `Numbers` sont imprimés sur la console à l'aide d'une activité définie pour la personnalisation appelée `PrintCollection`.</span><span class="sxs-lookup"><span data-stu-id="e2794-126">In the demonstration, the item members of collection `Numbers` are printed on the console using a custom-defined activity called `PrintCollection`.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e2794-127">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="e2794-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="e2794-128">À l'aide de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], ouvrez le fichier solution Collection.sln.</span><span class="sxs-lookup"><span data-stu-id="e2794-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Collection.sln solution file.</span></span>  
  
2.  <span data-ttu-id="e2794-129">Pour générer la solution, appuyez sur Ctrl+Maj+B.</span><span class="sxs-lookup"><span data-stu-id="e2794-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="e2794-130">Pour exécuter la solution, appuyez sur Ctrl+F5.</span><span class="sxs-lookup"><span data-stu-id="e2794-130">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2794-131">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e2794-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2794-132">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="e2794-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2794-133">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e2794-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2794-134">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="e2794-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`