---
title: Guide F#
description: "En savoir plus sur F # langage de programmation, un langage open source de .NET qui fournit la prise en charge de première classe de la programmation fonctionnelle."
keywords: .NET, .NET Core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="8b42f-104">Guide F#</span><span class="sxs-lookup"><span data-stu-id="8b42f-104">F# Guide</span></span>

<span data-ttu-id="8b42f-105">F# est un langage de programmation multiplateforme et open source pour .NET qui offre une prise en charge de première classe de la programmation fonctionnelle. F# prend également en charge la programmation orientée objet et impérative.</span><span class="sxs-lookup"><span data-stu-id="8b42f-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="8b42f-106">Grâce au compilateur et aux outils Visual F# implémentés par Microsoft, le langage de programmation F# fait partie intégrante de .NET.</span><span class="sxs-lookup"><span data-stu-id="8b42f-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="8b42f-107">Si vous débutez avec F #</span><span class="sxs-lookup"><span data-stu-id="8b42f-107">If You're New to F#</span></span> #

<span data-ttu-id="8b42f-108">Si vous utilisez F #, commencer par le [visite guidée de F #](tour.md) pour obtenir une vue d’ensemble du langage.</span><span class="sxs-lookup"><span data-stu-id="8b42f-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="8b42f-109">Il est également recommandé que vous parcourez les [fonctionne comme valeurs de première classe](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> pour apprendre les concepts de programmation fonctionnelle qui sont essentielles à l’utilisation de F #.</span><span class="sxs-lookup"><span data-stu-id="8b42f-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="8b42f-110">Les [didacticiels](tutorials/getting-started/index.md) comprennent également des guides pas à pas couvrant les fonctionnalités du langage pour différents niveaux de compétence.</span><span class="sxs-lookup"><span data-stu-id="8b42f-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="8b42f-111">Si vous êtes familiarisé avec F #</span><span class="sxs-lookup"><span data-stu-id="8b42f-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="8b42f-112">Si vous utilisez régulièrement F#, les [informations de référence sur le langage](language-reference/index.md) vous seront d’une grande utilité. Cette rubrique présente de manière approfondie chaque aspect du langage et propose de nombreux exemples de code.</span><span class="sxs-lookup"><span data-stu-id="8b42f-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="8b42f-113">Vous trouverez aussi beaucoup à découvrir dans les [informations de référence sur la bibliothèque principale F#](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span><span class="sxs-lookup"><span data-stu-id="8b42f-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="8b42f-114">La référence de bibliothèque F # Core déplacera finalement en s’éloignant de MSDN et dans ces documents en cours.</span><span class="sxs-lookup"><span data-stu-id="8b42f-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="8b42f-115">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="8b42f-115">The F# Software Foundation</span></span>

<span data-ttu-id="8b42f-116">Bien que Microsoft soit le principal développeur du langage F# et des outils Visual F#, F# bénéficie également de l’appui d’une organisation indépendante, la FSSF (F# Software Foundation).</span><span class="sxs-lookup"><span data-stu-id="8b42f-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="8b42f-117">La FSSF a pour but non seulement de promouvoir, protéger et développer le langage de programmation F#, mais aussi de soutenir et d’étendre la communauté internationale et diversifiée de programmeurs F#.</span><span class="sxs-lookup"><span data-stu-id="8b42f-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="8b42f-118">Pour en savoir plus et vous impliquer, consultez [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="8b42f-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="8b42f-119">Documentation</span><span class="sxs-lookup"><span data-stu-id="8b42f-119">Documentation</span></span>

* [<span data-ttu-id="8b42f-120">Didacticiels</span><span class="sxs-lookup"><span data-stu-id="8b42f-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="8b42f-121">[Fonctions comme valeurs de première classe](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="8b42f-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="8b42f-122">Informations de référence sur le langage</span><span class="sxs-lookup"><span data-stu-id="8b42f-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="8b42f-123">Informations de référence sur la bibliothèque principale F#</span><span class="sxs-lookup"><span data-stu-id="8b42f-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="8b42f-124">Ressources à lire en ligne</span><span class="sxs-lookup"><span data-stu-id="8b42f-124">Online Reading Resources</span></span>

* [<span data-ttu-id="8b42f-125">F # et bénéfices Gitbook</span><span class="sxs-lookup"><span data-stu-id="8b42f-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="8b42f-126">F# Programming Wikibook</span><span class="sxs-lookup"><span data-stu-id="8b42f-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="8b42f-127">Ressources vidéo</span><span class="sxs-lookup"><span data-stu-id="8b42f-127">Video Learning Resources</span></span>

* [<span data-ttu-id="8b42f-128">Série « Introduction to Functional Programming with F# » sur YouTube</span><span class="sxs-lookup"><span data-stu-id="8b42f-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="8b42f-129">Série « Introduction to F# » sur FSharpTV</span><span class="sxs-lookup"><span data-stu-id="8b42f-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="8b42f-130">Ressources supplémentaires</span><span class="sxs-lookup"><span data-stu-id="8b42f-130">Further Resources</span></span>

* [<span data-ttu-id="8b42f-131">Ressources destinées à apprendre F# sur fsharp.org</span><span class="sxs-lookup"><span data-stu-id="8b42f-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="8b42f-132">Site web d’extraits de code en F#</span><span class="sxs-lookup"><span data-stu-id="8b42f-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="8b42f-133">F# Software Foundation</span><span class="sxs-lookup"><span data-stu-id="8b42f-133">F# Software Foundation</span></span>](http://fsharp.org)
