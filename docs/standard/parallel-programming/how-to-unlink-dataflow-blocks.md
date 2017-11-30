---
title: "Comment : dissocier des blocs de flux de données"
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
- dataflow blocks, unlinking in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, unlinking dataflow blocks
ms.assetid: 40f0208d-4618-47f7-85cf-4913d07d2d7d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 41f1b83fab6ff44e69ac2f010f70e6e254341f5e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-unlink-dataflow-blocks"></a><span data-ttu-id="6778d-102">Comment : dissocier des blocs de flux de données</span><span class="sxs-lookup"><span data-stu-id="6778d-102">How to: Unlink Dataflow Blocks</span></span>
<span data-ttu-id="6778d-103">Ce document décrit comment dissocier un bloc de flux de données cible à partir de sa source.</span><span class="sxs-lookup"><span data-stu-id="6778d-103">This document describes how to unlink a target dataflow block from its source.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="6778d-104">La bibliothèque de flux de données TPL (espace de noms <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType>) n'est pas distribuée avec le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6778d-104">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="6778d-105">Pour installer l'espace de noms <xref:System.Threading.Tasks.Dataflow>, ouvrez votre projet dans [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], dans le menu Projet choisissez **Gérer les packages NuGet**, puis recherchez en ligne le package `Microsoft.Tpl.Dataflow`.</span><span class="sxs-lookup"><span data-stu-id="6778d-105">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6778d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="6778d-106">Example</span></span>  
 <span data-ttu-id="6778d-107">L’exemple suivant crée trois <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> d’objets, chacun des qui appelle le `TrySolution` méthode pour calculer une valeur.</span><span class="sxs-lookup"><span data-stu-id="6778d-107">The following example creates three <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objects, each of which calls the `TrySolution` method to compute a value.</span></span> <span data-ttu-id="6778d-108">Cet exemple ne requiert que le résultat du premier appel à `TrySolution` à terminer.</span><span class="sxs-lookup"><span data-stu-id="6778d-108">This example requires only the result from the first call to `TrySolution` to finish.</span></span>  
  
 [!code-csharp[TPLDataflow_ReceiveAny#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_receiveany/cs/dataflowreceiveany.cs#1)]
 [!code-vb[TPLDataflow_ReceiveAny#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_receiveany/vb/dataflowreceiveany.vb#1)]  
  
 <span data-ttu-id="6778d-109">Pour recevoir la valeur de la première <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objet qui se termine, cet exemple définit le `ReceiveFromAny(T)` (méthode).</span><span class="sxs-lookup"><span data-stu-id="6778d-109">To receive the value from the first <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> object that finishes, this example defines the `ReceiveFromAny(T)` method.</span></span> <span data-ttu-id="6778d-110">Le `ReceiveFromAny(T)` méthode accepte un tableau de <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objets ainsi que des liens de chacun de ces objets pour un <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet.</span><span class="sxs-lookup"><span data-stu-id="6778d-110">The `ReceiveFromAny(T)` method accepts an array of <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> objects and links each of these objects to a <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6778d-111">Lorsque vous utilisez la <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> méthode pour lier un bloc de flux de données source à un bloc cible, la source de propage les messages vers la cible de données deviennent disponibles.</span><span class="sxs-lookup"><span data-stu-id="6778d-111">When you use the <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method to link a source dataflow block to a target block, the source propagates messages to the target as data becomes available.</span></span> <span data-ttu-id="6778d-112">Étant donné que la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> classe accepte uniquement le premier message Il est fourni, le `ReceiveFromAny(T)` méthode produit ses résultats en appelant le <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="6778d-112">Because the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> class accepts only the first message that it is offered, the `ReceiveFromAny(T)` method produces its result by calling the <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> method.</span></span> <span data-ttu-id="6778d-113">Cela génère le premier message qui est proposé à la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet.</span><span class="sxs-lookup"><span data-stu-id="6778d-113">This produces the first message that is offered to the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object.</span></span> <span data-ttu-id="6778d-114">Le <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> méthode a une version surchargée qui accepte un <xref:System.Boolean> paramètre, `unlinkAfterOne` qui, lorsqu’il est défini `True`, fait en sorte que le bloc source pour supprimer la liaison de la cible une fois que la cible reçoit un message à partir de la source.</span><span class="sxs-lookup"><span data-stu-id="6778d-114">The <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601.LinkTo%2A> method has an overloaded version that takes a <xref:System.Boolean> parameter, `unlinkAfterOne` that, when it is set to `True`, instructs the source block to unlink from the target after the target receives one message from the source.</span></span> <span data-ttu-id="6778d-115">Il est important pour le <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet dissocier de ses sources, car la relation entre le tableau de sources et le <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet n’est plus nécessaire après la <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> objet reçoit un message.</span><span class="sxs-lookup"><span data-stu-id="6778d-115">It is important for the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object to unlink from its sources because the relationship between the array of sources and the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object is no longer required after the <xref:System.Threading.Tasks.Dataflow.WriteOnceBlock%601> object receives a message.</span></span>  
  
 <span data-ttu-id="6778d-116">Pour activer les appels restants à `TrySolution` à la fin une fois qu’un d’eux calcule une valeur, le `TrySolution` méthode prend un <xref:System.Threading.CancellationToken> objet qui est annulée après l’appel à `ReceiveFromAny(T)` renvoie.</span><span class="sxs-lookup"><span data-stu-id="6778d-116">To enable the remaining calls to `TrySolution` to end after one of them computes a value, the `TrySolution` method takes a <xref:System.Threading.CancellationToken> object that is canceled after the call to `ReceiveFromAny(T)` returns.</span></span> <span data-ttu-id="6778d-117">Le <xref:System.Threading.SpinWait.SpinUntil%2A> méthode retourne quand cela <xref:System.Threading.CancellationToken> objet est annulé.</span><span class="sxs-lookup"><span data-stu-id="6778d-117">The <xref:System.Threading.SpinWait.SpinUntil%2A> method returns when this <xref:System.Threading.CancellationToken> object is canceled.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6778d-118">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6778d-118">Compiling the Code</span></span>  
 <span data-ttu-id="6778d-119">Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6778d-119">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `DataflowReceiveAny.cs` (`DataflowReceiveAny.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="6778d-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span><span class="sxs-lookup"><span data-stu-id="6778d-120">**csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="6778d-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span><span class="sxs-lookup"><span data-stu-id="6778d-121">**vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowReceiveAny.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6778d-122">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="6778d-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6778d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6778d-123">See Also</span></span>  
 [<span data-ttu-id="6778d-124">Le flux de données</span><span class="sxs-lookup"><span data-stu-id="6778d-124">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
