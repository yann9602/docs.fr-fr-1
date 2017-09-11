---
title: "Spécifier dynamiquement des filtres de prédicat au moment de l’exécution"
description: "Guide pratique pour spécifier dynamiquement des filtres de prédicat au moment de l’exécution."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e724428bce09e2b2fa20b9391ad131424e16413
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a><span data-ttu-id="301f5-104">Spécifier dynamiquement des filtres de prédicat au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="301f5-104">Dynamically specify predicate filters at runtime</span></span>

<span data-ttu-id="301f5-105">Dans certains cas, ce n’est qu’au moment de l’exécution que vous savez combien de prédicats vous devez appliquer aux éléments source dans la clause `where`.</span><span class="sxs-lookup"><span data-stu-id="301f5-105">In some cases you do not know until run time how many predicates you have to apply to source elements in the `where` clause.</span></span> <span data-ttu-id="301f5-106">L’une des manières de spécifier plusieurs filtres de prédicat de manière dynamique consiste à utiliser la méthode <xref:System.Linq.Enumerable.Contains%2A>, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="301f5-106">One way to dynamically specify multiple predicate filters is to use the <xref:System.Linq.Enumerable.Contains%2A> method, as shown in the following example.</span></span> <span data-ttu-id="301f5-107">L’exemple est construit de deux façons.</span><span class="sxs-lookup"><span data-stu-id="301f5-107">The example is constructed in two ways.</span></span> <span data-ttu-id="301f5-108">Tout d’abord, le projet est exécuté en filtrant les valeurs fournies dans le programme.</span><span class="sxs-lookup"><span data-stu-id="301f5-108">First, the project is run by filtering on values that are provided in the program.</span></span> <span data-ttu-id="301f5-109">Ensuite, le projet est réexécuté à l’aide de l’entrée fournie au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="301f5-109">Then the project is run again by using input provided at run time.</span></span>  
  
## <a name="to-filter-by-using-the-contains-method"></a><span data-ttu-id="301f5-110">Pour filtrer à l’aide de la méthode Contains</span><span class="sxs-lookup"><span data-stu-id="301f5-110">To filter by using the Contains method</span></span>  
  
1.  <span data-ttu-id="301f5-111">Ouvrez une nouvelle application console et nommez-la `PredicateFilters`.</span><span class="sxs-lookup"><span data-stu-id="301f5-111">Open a new console application and name it `PredicateFilters`.</span></span>  
  
2.  <span data-ttu-id="301f5-112">Copiez la classe `StudentClass` à partir de [Interroger une collection d’objets](query-a-collection-of-objects.md) et collez-la dans l’espace de noms `PredicateFilters` sous la classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="301f5-112">Copy the `StudentClass` class from [Query a collection of objects](query-a-collection-of-objects.md) and paste it into namespace `PredicateFilters` underneath class `Program`.</span></span> <span data-ttu-id="301f5-113">`StudentClass` fournit une liste d’objets `Student`.</span><span class="sxs-lookup"><span data-stu-id="301f5-113">`StudentClass` provides a list of `Student` objects.</span></span>  
  
3.  <span data-ttu-id="301f5-114">Commentez la méthode `Main` dans `StudentClass`.</span><span class="sxs-lookup"><span data-stu-id="301f5-114">Comment out the `Main` method in `StudentClass`.</span></span>  
  
4.  <span data-ttu-id="301f5-115">Remplacez la classe `Program` par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="301f5-115">Replace class `Program` with the following code.</span></span>  
  
     <span data-ttu-id="301f5-116">[!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="301f5-116">[!code-cs[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]</span></span>  
  
5.  <span data-ttu-id="301f5-117">Ajoutez la ligne suivante à la méthode `Main` dans la classe `DynamicPredicates`, sous la déclaration de `ids`.</span><span class="sxs-lookup"><span data-stu-id="301f5-117">Add the following line to the `Main` method in class `DynamicPredicates`, under the declaration of `ids`.</span></span>  
  
     ```csharp
     QueryById(ids);
     ```

6.  <span data-ttu-id="301f5-118">Exécutez le projet.</span><span class="sxs-lookup"><span data-stu-id="301f5-118">Run the project.</span></span>  
  
7.  <span data-ttu-id="301f5-119">La sortie suivante s’affiche dans une fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="301f5-119">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="301f5-120">Garcia: 114</span><span class="sxs-lookup"><span data-stu-id="301f5-120">Garcia: 114</span></span>  
  
     <span data-ttu-id="301f5-121">O’Donnell: 112</span><span class="sxs-lookup"><span data-stu-id="301f5-121">O'Donnell: 112</span></span>  
  
     <span data-ttu-id="301f5-122">Omelchenko: 111</span><span class="sxs-lookup"><span data-stu-id="301f5-122">Omelchenko: 111</span></span>  
  
8.  <span data-ttu-id="301f5-123">L’étape suivante consiste à réexécuter le projet, cette fois en utilisant l’entrée saisie au moment de l’exécution plutôt que le tableau `ids`.</span><span class="sxs-lookup"><span data-stu-id="301f5-123">The next step is to run the project again, this time by using input entered at run time instead of array `ids`.</span></span> <span data-ttu-id="301f5-124">Remplacez `QueryByID(ids)` par `QueryByID(args)` dans la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="301f5-124">Change `QueryByID(ids)` to `QueryByID(args)` in the `Main` method.</span></span>  
  
9. <span data-ttu-id="301f5-125">Exécutez le projet avec les arguments de ligne de commande `122 117 120 115`.</span><span class="sxs-lookup"><span data-stu-id="301f5-125">Run the project with the command line arguments `122 117 120 115`.</span></span> <span data-ttu-id="301f5-126">Quand le projet est exécuté, ces valeurs deviennent des éléments de `args`, le paramètre de la méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="301f5-126">When the project is run, those values become elements of `args`, the parameter of the `Main` method..</span></span>  
  
10. <span data-ttu-id="301f5-127">La sortie suivante s’affiche dans une fenêtre de console :</span><span class="sxs-lookup"><span data-stu-id="301f5-127">The following output is displayed in a console window:</span></span>  
  
     <span data-ttu-id="301f5-128">Adams: 120</span><span class="sxs-lookup"><span data-stu-id="301f5-128">Adams: 120</span></span>  
  
     <span data-ttu-id="301f5-129">Feng: 117</span><span class="sxs-lookup"><span data-stu-id="301f5-129">Feng: 117</span></span>  
  
     <span data-ttu-id="301f5-130">Garcia: 115</span><span class="sxs-lookup"><span data-stu-id="301f5-130">Garcia: 115</span></span>  
  
     <span data-ttu-id="301f5-131">Tucker: 122</span><span class="sxs-lookup"><span data-stu-id="301f5-131">Tucker: 122</span></span>  
  
## <a name="to-filter-by-using-a-switch-statement"></a><span data-ttu-id="301f5-132">Pour filtrer à l’aide d’une instruction switch</span><span class="sxs-lookup"><span data-stu-id="301f5-132">To filter by using a switch statement</span></span>  
  
1.  <span data-ttu-id="301f5-133">Vous pouvez utiliser une instruction `switch` pour sélectionner parmi d’autres requêtes prédéterminées.</span><span class="sxs-lookup"><span data-stu-id="301f5-133">You can use a `switch` statement to select among predetermined alternative queries.</span></span> <span data-ttu-id="301f5-134">Dans l’exemple suivant, `studentQuery` utilise une autre clause `where` en fonction du niveau, ou de l’année, spécifié(e) au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="301f5-134">In the following example, `studentQuery` uses a different `where` clause depending on which grade level, or year, is specified at run time.</span></span>  
  
2.  <span data-ttu-id="301f5-135">Copiez la méthode suivante et collez-la dans la classe `DynamicPredicates`.</span><span class="sxs-lookup"><span data-stu-id="301f5-135">Copy the following method and paste it into class `DynamicPredicates`.</span></span>  
  
     <span data-ttu-id="301f5-136">[!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="301f5-136">[!code-cs[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]</span></span>  
  
3.  <span data-ttu-id="301f5-137">Dans la méthode `Main`, remplacez l’appel à `QueryByID` par l’appel suivant, qui envoie le premier élément du tableau `args` comme argument : `QueryByYear(args[0])`.</span><span class="sxs-lookup"><span data-stu-id="301f5-137">In the `Main` method, replace the call to `QueryByID` with the following call, which sends the first element from the `args` array as its argument: `QueryByYear(args[0])`.</span></span>  
  
4.  <span data-ttu-id="301f5-138">Exécutez le projet avec un argument de ligne de commande d’une valeur entière comprise entre 1 et 4.</span><span class="sxs-lookup"><span data-stu-id="301f5-138">Run the project with a command line argument of an integer value between 1 and 4.</span></span>  
  
 
## <a name="see-also"></a><span data-ttu-id="301f5-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="301f5-139">See Also</span></span>  
 <span data-ttu-id="301f5-140">[Expressions de requête LINQ](index.md) </span><span class="sxs-lookup"><span data-stu-id="301f5-140">[LINQ Query Expressions](index.md) </span></span>  
 [<span data-ttu-id="301f5-141">where, clause</span><span class="sxs-lookup"><span data-stu-id="301f5-141">where clause</span></span>](../language-reference/keywords/where-clause.md)

