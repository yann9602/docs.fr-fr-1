---
title: "Présentation des délégués"
description: "Explorez les délégués dans cette rubrique de vue d’ensemble qui présente les concepts de base et décrit les objectifs de conception de langage pour les délégués."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="ba471-104">Présentation des délégués</span><span class="sxs-lookup"><span data-stu-id="ba471-104">Introduction to Delegates</span></span>

[<span data-ttu-id="ba471-105">Précédent</span><span class="sxs-lookup"><span data-stu-id="ba471-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="ba471-106">Les délégués fournissent un mécanisme de *liaison tardive* dans .NET.</span><span class="sxs-lookup"><span data-stu-id="ba471-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="ba471-107">La liaison tardive signifie que vous créez un algorithme où l’appelant fournit également au moins une méthode qui implémente une partie de l’algorithme.</span><span class="sxs-lookup"><span data-stu-id="ba471-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="ba471-108">Par exemple, prenez le tri d’une liste d’étoiles dans une application d’astronomie.</span><span class="sxs-lookup"><span data-stu-id="ba471-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="ba471-109">Vous pouvez choisir de trier les étoiles d’après leur distance par rapport à la terre, d’après leur magnitude ou d’après leur luminosité perçue.</span><span class="sxs-lookup"><span data-stu-id="ba471-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="ba471-110">Dans tous ces cas-là, la méthode Sort() effectue essentiellement la même chose : elle organise les éléments dans la liste en se basant sur une comparaison.</span><span class="sxs-lookup"><span data-stu-id="ba471-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="ba471-111">Le code qui compare deux étoiles est différent pour chacun des ordres de tri.</span><span class="sxs-lookup"><span data-stu-id="ba471-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="ba471-112">Ces genres de solutions sont utilisés dans les logiciels depuis un demi siècle.</span><span class="sxs-lookup"><span data-stu-id="ba471-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="ba471-113">Le concept de délégué du langage C# fournit une prise en charge linguistique de première classe et la sécurité de type autour du concept.</span><span class="sxs-lookup"><span data-stu-id="ba471-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="ba471-114">Comme vous le verrez plus loin dans cette série, le code C# que vous écrivez pour des algorithmes comme celui-ci est de type sécurisé. Il s’appuie sur le langage et le compilateur pour s’assurer que les types correspondent à des arguments et des types de retour.</span><span class="sxs-lookup"><span data-stu-id="ba471-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="ba471-115">Objectifs de conception de langage pour les délégués</span><span class="sxs-lookup"><span data-stu-id="ba471-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="ba471-116">Les concepteurs de langage ont énuméré plusieurs objectifs pour la fonctionnalité qui est finalement devenue celle des délégués.</span><span class="sxs-lookup"><span data-stu-id="ba471-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="ba471-117">L’équipe souhaitait une construction de langage commune pouvant être utilisée pour tout algorithme à liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="ba471-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="ba471-118">Cela permet aux développeurs d’apprendre un concept et d’utiliser ce même concept pour résoudre de nombreux problèmes logiciels différents.</span><span class="sxs-lookup"><span data-stu-id="ba471-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="ba471-119">Ensuite, l’équipe souhaitait prendre en charge les appels de méthodes uniques et multicasts.</span><span class="sxs-lookup"><span data-stu-id="ba471-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="ba471-120">(Les délégués multicast sont des délégués où plusieurs méthodes sont chaînées.)</span><span class="sxs-lookup"><span data-stu-id="ba471-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="ba471-121">Vous verrez des exemples [plus loin dans cette série](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="ba471-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="ba471-122">L’équipe souhaitait que les délégués prennent en charge la même sécurité de type que celle attendue par les développeurs pour toutes les constructions C#.</span><span class="sxs-lookup"><span data-stu-id="ba471-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="ba471-123">Pour finir, l’équipe a reconnu qu’un modèle d’événement était un modèle spécifique où les délégués (ou tout algorithme de liaison tardive) étaient très utiles.</span><span class="sxs-lookup"><span data-stu-id="ba471-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="ba471-124">L’équipe souhaitait s’assurer que le code pour les délégués pouvait fournir la base pour le modèle d’événement .NET.</span><span class="sxs-lookup"><span data-stu-id="ba471-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="ba471-125">Le résultat de tout ce travail est la prise en charge des délégués et des événements en C# et .NET.</span><span class="sxs-lookup"><span data-stu-id="ba471-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="ba471-126">Les autres articles de cette section traitent des fonctionnalités de langage, de la prise en charge de la bibliothèque, et des idiomes courants utilisés quand vous travaillez avec des délégués.</span><span class="sxs-lookup"><span data-stu-id="ba471-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="ba471-127">Vous découvrirez le mot clé `delegate` et le code qu’il génère.</span><span class="sxs-lookup"><span data-stu-id="ba471-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="ba471-128">Vous découvrirez les fonctionnalités de la classe `System.Delegate` et comment elles sont utilisées.</span><span class="sxs-lookup"><span data-stu-id="ba471-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="ba471-129">Vous découvrirez comment créer des délégués de type sécurisé et comment créer des méthodes qui peuvent être appelées par l’intermédiaire de délégués.</span><span class="sxs-lookup"><span data-stu-id="ba471-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="ba471-130">Vous découvrirez aussi comment utiliser des délégués et des événements à l’aide d’expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="ba471-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="ba471-131">Vous verrez où les délégués deviennent l’un des blocs de construction de LINQ.</span><span class="sxs-lookup"><span data-stu-id="ba471-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="ba471-132">Vous découvrirez que les délégués sont la base du modèle d’événement .NET, et comment ils diffèrent.</span><span class="sxs-lookup"><span data-stu-id="ba471-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="ba471-133">Globalement, vous verrez comment les délégués forment une partie intégrante de la programmation dans .NET et de l’utilisation des API du framework.</span><span class="sxs-lookup"><span data-stu-id="ba471-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="ba471-134">Allons-y.</span><span class="sxs-lookup"><span data-stu-id="ba471-134">Let's get started.</span></span>

[<span data-ttu-id="ba471-135">Suivant</span><span class="sxs-lookup"><span data-stu-id="ba471-135">Next</span></span>](delegate-class.md)
