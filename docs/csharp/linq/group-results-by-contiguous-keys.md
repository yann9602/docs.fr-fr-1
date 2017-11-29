---
title: "Regrouper des résultats par clés contiguës"
description: "Comment regrouper des résultats par clés contiguës."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: cdd06a6fad037291bbc5aa011b47bb668fa2f062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="group-results-by-contiguous-keys"></a><span data-ttu-id="2cfe1-104">Regrouper des résultats par clés contiguës</span><span class="sxs-lookup"><span data-stu-id="2cfe1-104">Group results by contiguous keys</span></span>

<span data-ttu-id="2cfe1-105">L’exemple suivant montre comment regrouper des éléments dans des blocs représentant des sous-séquences de clés contiguës.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-105">The following example shows how to group elements into chunks that represent subsequences of contiguous keys.</span></span> <span data-ttu-id="2cfe1-106">Par exemple, supposons que vous disposiez de la séquence de paires clé-valeur suivante :</span><span class="sxs-lookup"><span data-stu-id="2cfe1-106">For example, assume that you are given the following sequence of key-value pairs:</span></span>  
  
|<span data-ttu-id="2cfe1-107">Clé</span><span class="sxs-lookup"><span data-stu-id="2cfe1-107">Key</span></span>|<span data-ttu-id="2cfe1-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="2cfe1-108">Value</span></span>|  
|---------|-----------|  
|<span data-ttu-id="2cfe1-109">A</span><span class="sxs-lookup"><span data-stu-id="2cfe1-109">A</span></span>|<span data-ttu-id="2cfe1-110">Nous</span><span class="sxs-lookup"><span data-stu-id="2cfe1-110">We</span></span>|  
|<span data-ttu-id="2cfe1-111">A</span><span class="sxs-lookup"><span data-stu-id="2cfe1-111">A</span></span>|<span data-ttu-id="2cfe1-112">pensons</span><span class="sxs-lookup"><span data-stu-id="2cfe1-112">think</span></span>|  
|<span data-ttu-id="2cfe1-113">A</span><span class="sxs-lookup"><span data-stu-id="2cfe1-113">A</span></span>|<span data-ttu-id="2cfe1-114">que</span><span class="sxs-lookup"><span data-stu-id="2cfe1-114">that</span></span>|  
|<span data-ttu-id="2cfe1-115">B</span><span class="sxs-lookup"><span data-stu-id="2cfe1-115">B</span></span>|<span data-ttu-id="2cfe1-116">Linq</span><span class="sxs-lookup"><span data-stu-id="2cfe1-116">Linq</span></span>|  
|<span data-ttu-id="2cfe1-117">C</span><span class="sxs-lookup"><span data-stu-id="2cfe1-117">C</span></span>|<span data-ttu-id="2cfe1-118">est</span><span class="sxs-lookup"><span data-stu-id="2cfe1-118">is</span></span>|  
|<span data-ttu-id="2cfe1-119">A</span><span class="sxs-lookup"><span data-stu-id="2cfe1-119">A</span></span>|<span data-ttu-id="2cfe1-120">vraiment</span><span class="sxs-lookup"><span data-stu-id="2cfe1-120">really</span></span>|  
|<span data-ttu-id="2cfe1-121">B</span><span class="sxs-lookup"><span data-stu-id="2cfe1-121">B</span></span>|<span data-ttu-id="2cfe1-122">chouette</span><span class="sxs-lookup"><span data-stu-id="2cfe1-122">cool</span></span>|  
|<span data-ttu-id="2cfe1-123">B</span><span class="sxs-lookup"><span data-stu-id="2cfe1-123">B</span></span>|<span data-ttu-id="2cfe1-124">!</span><span class="sxs-lookup"><span data-stu-id="2cfe1-124">!</span></span>|  
  
 <span data-ttu-id="2cfe1-125">Les groupes suivants seront créés dans cet ordre :</span><span class="sxs-lookup"><span data-stu-id="2cfe1-125">The following groups will be created in this order:</span></span>  
  
1.  <span data-ttu-id="2cfe1-126">Nous, pensons, que</span><span class="sxs-lookup"><span data-stu-id="2cfe1-126">We, think, that</span></span>  
  
2.  <span data-ttu-id="2cfe1-127">Linq</span><span class="sxs-lookup"><span data-stu-id="2cfe1-127">Linq</span></span>  
  
3.  <span data-ttu-id="2cfe1-128">est</span><span class="sxs-lookup"><span data-stu-id="2cfe1-128">is</span></span>  
  
4.  <span data-ttu-id="2cfe1-129">vraiment</span><span class="sxs-lookup"><span data-stu-id="2cfe1-129">really</span></span>  
  
5.  <span data-ttu-id="2cfe1-130">chouette, !</span><span class="sxs-lookup"><span data-stu-id="2cfe1-130">cool, !</span></span>  
  
 <span data-ttu-id="2cfe1-131">La solution est implémentée comme une méthode d’extension thread-safe qui retourne ses résultats en continu.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-131">The solution is implemented as an extension method that is thread-safe and that returns its results in a streaming manner.</span></span> <span data-ttu-id="2cfe1-132">En d’autres termes, elle produit ses groupes à mesure qu’elle se déplace dans la séquence source.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-132">In other words, it produces its groups as it moves through the source sequence.</span></span> <span data-ttu-id="2cfe1-133">Contrairement aux opérateurs `group` ou `orderby`, elle peut commencer à retourner des groupes à l’appelant avant que l’intégralité de la séquence ait été lue.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-133">Unlike the `group` or `orderby` operators, it can begin returning groups to the caller before all of the sequence has been read.</span></span>  
  
 <span data-ttu-id="2cfe1-134">La cohérence de thread est obtenue en effectuant une copie de chaque groupe ou bloc pendant l’itération de la séquence source, comme expliqué dans les commentaires du code source.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-134">Thread-safety is accomplished by making a copy of each group or chunk as the source sequence is iterated, as explained in the source code comments.</span></span> <span data-ttu-id="2cfe1-135">Si la séquence source comporte une longue séquence d’éléments contigus, le common language runtime peut lever une <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-135">If the source sequence has a large sequence of contiguous items, the common language runtime may throw an <xref:System.OutOfMemoryException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cfe1-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cfe1-136">Example</span></span>  
 <span data-ttu-id="2cfe1-137">L’exemple suivant montre la méthode d’extension et le code client qui l’utilise.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-137">The following example shows both the extension method and the client code that uses it.</span></span>  
  
 [!code-csharp[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 <span data-ttu-id="2cfe1-138">Pour utiliser la méthode d’extension dans votre projet, copiez la classe statique `MyExtensions` dans un fichier de code source nouveau ou existant et, si nécessaire, ajoutez une directive `using` pour l’espace de noms dans lequel elle se trouve.</span><span class="sxs-lookup"><span data-stu-id="2cfe1-138">To use the extension method in your project, copy the `MyExtensions` static class to a new or existing source code file and if it is required, add a `using` directive for the namespace where it is located.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfe1-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cfe1-139">See also</span></span>  
 [<span data-ttu-id="2cfe1-140">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="2cfe1-140">LINQ Query Expressions</span></span>](index.md)  
 
