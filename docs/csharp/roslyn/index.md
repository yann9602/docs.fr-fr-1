---
title: Utilisation du kit SDK .NET Compiler - Guide C# | Microsoft Docs
description: "Explorez les API Roslyn pour créer des correctifs de code et des diagnostics automatiques."
keywords: .NET, .NET Core, C#, Roslyn,
ms.date: 06/25/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: abed9e00-2ddc-468e-9cca-d033bd6a7e36
redirect_url: /dotnet/csharp/index
ms.translationtype: Human Translation
ms.sourcegitcommit: c844ef1a62f65421c894aa258d64dbe4b51f4cc7
ms.openlocfilehash: a792e1220b18d5da34bb68bd51d069ff0021b063
ms.contentlocale: fr-fr
ms.lasthandoff: 07/19/2017

---

# <a name="-using-the-net-compiler-sdk"></a><span data-ttu-id="1521d-104">🔧 Utilisation du kit SDK .NET Compiler</span><span class="sxs-lookup"><span data-stu-id="1521d-104">🔧 Using the .NET Compiler SDK</span></span>

> <span data-ttu-id="1521d-105">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="1521d-105">**Note**</span></span>
> 
> <span data-ttu-id="1521d-106">Cette rubrique n’a pas encore été rédigée !</span><span class="sxs-lookup"><span data-stu-id="1521d-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="1521d-107">Votre aide pour en définir le cadre et l’approche est la bienvenue.</span><span class="sxs-lookup"><span data-stu-id="1521d-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="1521d-108">Vous pouvez suivre la progression de ce [problème](https://github.com/dotnet/docs/issues/972) et y apporter vos commentaires dans GitHub.</span><span class="sxs-lookup"><span data-stu-id="1521d-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/972) at GitHub.</span></span>
> 
> <span data-ttu-id="1521d-109">Si vous voulez consulter les premières ébauches et le plan de cette rubrique, laissez une note avec vos coordonnées.</span><span class="sxs-lookup"><span data-stu-id="1521d-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="1521d-110">Découvrez comment vous pouvez apporter votre contribution sur [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="1521d-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

<span data-ttu-id="1521d-111">Il s’agit d’une méta-rubrique pour toute une section.</span><span class="sxs-lookup"><span data-stu-id="1521d-111">This is a meta-topic for an entire section.</span></span> <span data-ttu-id="1521d-112">Voici les thèmes qui doivent être abordés :</span><span class="sxs-lookup"><span data-stu-id="1521d-112">Areas that need to be covered here include:</span></span> 
* <span data-ttu-id="1521d-113">Commencer</span><span class="sxs-lookup"><span data-stu-id="1521d-113">Getting Started</span></span>
* <span data-ttu-id="1521d-114">Exemples et didacticiels</span><span class="sxs-lookup"><span data-stu-id="1521d-114">Samples and tutorials</span></span>
* <span data-ttu-id="1521d-115">contenu conceptuel</span><span class="sxs-lookup"><span data-stu-id="1521d-115">conceptual content</span></span>
* <span data-ttu-id="1521d-116">modèle global des API</span><span class="sxs-lookup"><span data-stu-id="1521d-116">overall model of the APIs</span></span>
* <span data-ttu-id="1521d-117">liens vers des exemples du dépôt [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers)</span><span class="sxs-lookup"><span data-stu-id="1521d-117">links to samples on the [roslyn-analyzers](http://github.com/dotnet/roslyn-analyzers) repository</span></span>
* <span data-ttu-id="1521d-118">liens vers d’autres contenus de référence</span><span class="sxs-lookup"><span data-stu-id="1521d-118">links to other reference content</span></span>

