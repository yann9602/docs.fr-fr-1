---
title: "Programmation simultanée - Guide C#"
description: "Découvrez des techniques pour l’exécution de tâches (probablement liées à l’UC) en parallèle"
keywords: "C#, async, utilisation de l’UC, utilisation du réseau"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0f8b42de-858a-44a3-87d9-998211f26377
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00cf3b04178ca48c9f8f35eb16bc216389e6b272
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="-concurrent-programming"></a><span data-ttu-id="b53e3-104">🔧 Programmation simultanée</span><span class="sxs-lookup"><span data-stu-id="b53e3-104">🔧 Concurrent Programming</span></span>

> <span data-ttu-id="b53e3-105">**Remarque**</span><span class="sxs-lookup"><span data-stu-id="b53e3-105">**Note**</span></span>
> 
> <span data-ttu-id="b53e3-106">Cette rubrique n’a pas encore été rédigée !</span><span class="sxs-lookup"><span data-stu-id="b53e3-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="b53e3-107">Votre aide pour en définir le cadre et l’approche est la bienvenue.</span><span class="sxs-lookup"><span data-stu-id="b53e3-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="b53e3-108">Vous pouvez suivre la progression de ce [problème](https://github.com/dotnet/docs/issues/953) et y apporter vos commentaires dans GitHub.</span><span class="sxs-lookup"><span data-stu-id="b53e3-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/953) at GitHub.</span></span>
> 
> <span data-ttu-id="b53e3-109">Si vous voulez consulter les premières ébauches et le plan de cette rubrique, laissez une note avec vos coordonnées.</span><span class="sxs-lookup"><span data-stu-id="b53e3-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="b53e3-110">Découvrez comment vous pouvez apporter votre contribution sur [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="b53e3-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

