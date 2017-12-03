---
title: Guide F#
description: "En savoir plus sur F #, un langage de programmation fonctionnels qui s’exécute sur .NET."
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 12/01/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 45f5d2ca794ccea7a35cf6c0bf9d58a3e6500453
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="f-guide"></a><span data-ttu-id="5deac-104">Guide F#</span><span class="sxs-lookup"><span data-stu-id="5deac-104">F# Guide</span></span>

<span data-ttu-id="5deac-105">F # est un langage de programmation fonctionnels qui s’exécute sur .NET.</span><span class="sxs-lookup"><span data-stu-id="5deac-105">F# is a functional programming language which runs on .NET.</span></span>  <span data-ttu-id="5deac-106">En plus des constructions de programmation fonctionnelle prise en charge, il possède également des fonctionnalités de programmation d’objets.</span><span class="sxs-lookup"><span data-stu-id="5deac-106">In addition to supporting functional programming constructs, it also has object programming capabilities.</span></span>  <span data-ttu-id="5deac-107">Cet hybride de la programmation fonctionnelle avec les fonctionnalités orientées objet rend F # une langue pragmatique pour accomplir une tâche.</span><span class="sxs-lookup"><span data-stu-id="5deac-107">This hybrid of functional programming with object-oriented capabilities makes F# a pragmatic language for accomplishing any task.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="5deac-108">Si vous débutez avec F #</span><span class="sxs-lookup"><span data-stu-id="5deac-108">If You're New to F#</span></span> #

<span data-ttu-id="5deac-109">Si vous utilisez F #, commencer par le [visite guidée de F #](tour.md) pour obtenir une vue d’ensemble du langage et certains de ses concepts de programmation.</span><span class="sxs-lookup"><span data-stu-id="5deac-109">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language and some of its programming concepts.</span></span>  <span data-ttu-id="5deac-110">Si vous utilisez Visual Studio, le modèle de projet du didacticiel contient le même contenu.</span><span class="sxs-lookup"><span data-stu-id="5deac-110">If you're using Visual Studio, the Tutorial project template contains the same content.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="5deac-111">Si vous êtes familiarisé avec F #</span><span class="sxs-lookup"><span data-stu-id="5deac-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="5deac-112">Si vous familiariser avec F #, ou que vous souhaitez en savoir plus sur une construction de langage spécifiques, consultez la [référence du langage](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="5deac-112">If you know your way around F#, or want to learn more about a specific language construct, see the [Language Reference](language-reference/index.md).</span></span>  <span data-ttu-id="5deac-113">Il s’agit d’un guide complet de toutes les fonctionnalités du langage F #.</span><span class="sxs-lookup"><span data-stu-id="5deac-113">It's a thorough guide of all F# language capabilities.</span></span>

<span data-ttu-id="5deac-114">En outre, le [référence de bibliothèque F # Core](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) est un bon point de départ pour en savoir plus sur FSharp.Core, la bibliothèque principale qui fait partie de F #.</span><span class="sxs-lookup"><span data-stu-id="5deac-114">Additionally, the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is a great resource for learning about FSharp.Core, the core library which is a part of F#.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="5deac-115">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="5deac-115">The F# Software Foundation</span></span>

<span data-ttu-id="5deac-116">Bien que Microsoft est le principal développeur du langage F # et ses outils, F # est soutenu par une base indépendante, le F # Software Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="5deac-116">Although Microsoft is the primary developer of the F# language and its tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="5deac-117">La FSSF a pour but non seulement de promouvoir, protéger et développer le langage de programmation F#, mais aussi de soutenir et d’étendre la communauté internationale et diversifiée de programmeurs F#.</span><span class="sxs-lookup"><span data-stu-id="5deac-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="5deac-118">Pour en savoir plus et vous impliquer, consultez [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="5deac-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="5deac-119">Documentation</span><span class="sxs-lookup"><span data-stu-id="5deac-119">Documentation</span></span>

* [<span data-ttu-id="5deac-120">Didacticiels</span><span class="sxs-lookup"><span data-stu-id="5deac-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="5deac-121">[Fonctions comme valeurs de première classe](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="5deac-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="5deac-122">Informations de référence sur le langage</span><span class="sxs-lookup"><span data-stu-id="5deac-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="5deac-123">Informations de référence sur la bibliothèque principale F#</span><span class="sxs-lookup"><span data-stu-id="5deac-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="5deac-124">Ressources à lire en ligne</span><span class="sxs-lookup"><span data-stu-id="5deac-124">Online Reading Resources</span></span>

* [<span data-ttu-id="5deac-125">F # et bénéfices Gitbook</span><span class="sxs-lookup"><span data-stu-id="5deac-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="5deac-126">F# Programming Wikibook</span><span class="sxs-lookup"><span data-stu-id="5deac-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="5deac-127">Ressources vidéo</span><span class="sxs-lookup"><span data-stu-id="5deac-127">Video Learning Resources</span></span>

* [<span data-ttu-id="5deac-128">Série « Introduction to Functional Programming with F# » sur YouTube</span><span class="sxs-lookup"><span data-stu-id="5deac-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="5deac-129">Série « Introduction to F# » sur FSharpTV</span><span class="sxs-lookup"><span data-stu-id="5deac-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="5deac-130">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="5deac-130">Further Resources</span></span>

* [<span data-ttu-id="5deac-131">Ressources destinées à apprendre F# sur fsharp.org</span><span class="sxs-lookup"><span data-stu-id="5deac-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="5deac-132">Site web d’extraits de code en F#</span><span class="sxs-lookup"><span data-stu-id="5deac-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="5deac-133">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="5deac-133">F# Software Foundation</span></span>](http://fsharp.org)