---
title: "Comment : spécifier le degré de parallélisme dans un bloc de flux de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c1ccd64a9acbc75a30984719671af2dc7dda6922
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a><span data-ttu-id="d224d-102">Comment : spécifier le degré de parallélisme dans un bloc de flux de données</span><span class="sxs-lookup"><span data-stu-id="d224d-102">How to: Specify the Degree of Parallelism in a Dataflow Block</span></span>
<span data-ttu-id="d224d-103">Ce document décrit comment définir la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> pour permettre à un bloc de flux de données d'exécution de traiter plusieurs messages à la fois.</span><span class="sxs-lookup"><span data-stu-id="d224d-103">This document describes how to set the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> property to enable an execution dataflow block to process more than one message at a time.</span></span> <span data-ttu-id="d224d-104">Cela est utile quand vous avez un bloc de flux de données qui effectue un calcul de longue durée et qui peut tirer parti du traitement des messages en parallèle.</span><span class="sxs-lookup"><span data-stu-id="d224d-104">Doing this is useful when you have a dataflow block that performs a long-running computation and can benefit from processing messages in parallel.</span></span> <span data-ttu-id="d224d-105">Cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> pour effectuer plusieurs opérations de flux de données simultanément ; toutefois, vous pouvez spécifier le degré maximum de parallélisme dans les types de bloc d'exécution prédéfinis fournis par la bibliothèque de flux de données TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d224d-105">This example uses the <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> class to perform multiple dataflow operations concurrently; however, you can specify the maximum degree of parallelism in any of the predefined execution block types that the TPL Dataflow Library provides, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="d224d-106">La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d224d-106">The TPL Dataflow Library (the <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="d224d-107">Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.</span><span class="sxs-lookup"><span data-stu-id="d224d-107">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d224d-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="d224d-108">Example</span></span>  
 <span data-ttu-id="d224d-109">L’exemple suivant effectue deux calculs de flux de données et affiche la durée calendaire nécessaire pour chaque calcul.</span><span class="sxs-lookup"><span data-stu-id="d224d-109">The following example performs two dataflow computations and prints the elapsed time that is required for each computation.</span></span> <span data-ttu-id="d224d-110">Le premier calcul spécifie un degré maximum de parallélisme de 1, qui est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d224d-110">The first computation specifies a maximum degree of parallelism of 1, which is the default.</span></span> <span data-ttu-id="d224d-111">Un degré maximum de parallélisme égal à 1 amène le bloc de flux de données à traiter les messages en série.</span><span class="sxs-lookup"><span data-stu-id="d224d-111">A maximum degree of parallelism of 1 causes the dataflow block to process messages serially.</span></span> <span data-ttu-id="d224d-112">Le deuxième calcul ressemble à la première, à ceci près qu'il spécifie un degré maximum de parallélisme égal au nombre de processeurs disponibles.</span><span class="sxs-lookup"><span data-stu-id="d224d-112">The second computation resembles the first, except that it specifies a maximum degree of parallelism that is equal to the number of available processors.</span></span> <span data-ttu-id="d224d-113">Cela permet au bloc de flux de données d'effectuer plusieurs opérations en parallèle.</span><span class="sxs-lookup"><span data-stu-id="d224d-113">This enables the dataflow block to perform multiple operations in parallel.</span></span>  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d224d-114">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d224d-114">Compiling the Code</span></span>  
 <span data-ttu-id="d224d-115">Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d224d-115">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="d224d-116">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span><span class="sxs-lookup"><span data-stu-id="d224d-116">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="d224d-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span><span class="sxs-lookup"><span data-stu-id="d224d-117">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d224d-118">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d224d-118">Robust Programming</span></span>  
 <span data-ttu-id="d224d-119">Par défaut, chaque bloc de flux de données prédéfini propage les messages dans l'ordre dans lequel ils sont reçus.</span><span class="sxs-lookup"><span data-stu-id="d224d-119">By default, each predefined dataflow block propagates out messages in the order in which the messages are received.</span></span>  <span data-ttu-id="d224d-120">Bien que plusieurs messages soient traités simultanément quand vous spécifiez un degré maximum de parallélisme supérieur 1, ils sont toujours propagés dans l'ordre dans lequel ils sont reçus.</span><span class="sxs-lookup"><span data-stu-id="d224d-120">Although multiple messages are processed simultaneously when you specify a maximum degree of parallelism that is greater than 1, they are still propagated out in the order in which they are received.</span></span>  
  
 <span data-ttu-id="d224d-121">Étant donné que la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> représente le degré maximal de parallélisme, le bloc de flux de données peut s'exécuter avec un degré de parallélisme moindre spécifié par vos soins.</span><span class="sxs-lookup"><span data-stu-id="d224d-121">Because the <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> property represents the maximum degree of parallelism, the dataflow block might execute with a lesser degree of parallelism than you specify.</span></span> <span data-ttu-id="d224d-122">Le bloc de flux de données peut utiliser un degré de parallélisme moindre pour satisfaire ses exigences fonctionnelles ou pour prendre en compte un manque de ressources système disponibles.</span><span class="sxs-lookup"><span data-stu-id="d224d-122">The dataflow block can use a lesser degree of parallelism to meet its functional requirements or to account for a lack of available system resources.</span></span> <span data-ttu-id="d224d-123">Un bloc de flux de données ne choisit jamais un degré de parallélisme supérieur à celui que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="d224d-123">A dataflow block never chooses a greater degree of parallelism than you specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d224d-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d224d-124">See Also</span></span>  
 [<span data-ttu-id="d224d-125">Le flux de données</span><span class="sxs-lookup"><span data-stu-id="d224d-125">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
