---
title: "Vue d’ensemble d’async"
description: "Découvrez dans quelle mesure la programmation asynchrone est une technique clé qui facilite le blocage des E/S et des opérations simultanées sur plusieurs cœurs."
keywords: .NET, .NET Core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.translationtype: HT
ms.sourcegitcommit: ef6d1bf9a7153f7adf635d13b4dcfb7647ed2e33
ms.openlocfilehash: bf0cc4ed21c92a57f3f5b2cfa27ac1f054e15172
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---

# <a name="async-overview"></a><span data-ttu-id="2c0a1-104">Vue d’ensemble d’async</span><span class="sxs-lookup"><span data-stu-id="2c0a1-104">Async Overview</span></span>

<span data-ttu-id="2c0a1-105">Il n’y a pas si longtemps, il suffisait d’acheter un PC ou un serveur plus récent pour que les applications soient plus rapides. Mais ce n’est plus le cas maintenant.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-105">Not so long ago, apps got faster simply by buying a newer PC or server and then that trend stopped.</span></span> <span data-ttu-id="2c0a1-106">En fait, c’est même tout le contraire.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-106">In fact, it reversed.</span></span> <span data-ttu-id="2c0a1-107">Les téléphones mobiles utilisent des processeurs ARM 1 GHz à cœur unique et les charges de travail serveur sont passées aux machines virtuelles.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-107">Mobile phones appeared with 1ghz single core ARM chips and server workloads transitioned to VMs.</span></span> <span data-ttu-id="2c0a1-108">Les utilisateurs veulent toujours une interface utilisateur réactive et les chefs d’entreprise veulent des serveurs qui s’adaptent à leur activité.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-108">Users still want responsive UI and business owners want servers that scale with their business.</span></span> <span data-ttu-id="2c0a1-109">La transition vers le mobile et le cloud ainsi qu’une population de plus de 3 milliards d’utilisateurs connectés à Internet ont donné naissance à un nouvel ensemble de modèles logiciels.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-109">The transition to mobile and cloud and an internet-connected population of >3B users has resulted in a new set of software patterns.</span></span> 

* <span data-ttu-id="2c0a1-110">Les applications clientes doivent être toujours actives, toujours connectées, constamment réactives à l’interaction de l’utilisateur (interface tactile, par exemple) et en haut du classement des magasins d’applications !</span><span class="sxs-lookup"><span data-stu-id="2c0a1-110">Client applications are expected to be always-on, always-connected and constantly responsive to user interaction (for example, touch) with high app store ratings!</span></span>
* <span data-ttu-id="2c0a1-111">Les services doivent gérer les pics de trafic en ayant la possibilité de monter et descendre en puissance facilement.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-111">Services are expected to handle spikes in traffic by gracefully scaling up and down.</span></span> 

<span data-ttu-id="2c0a1-112">La programmation asynchrone est une technique clé qui facilite le blocage des E/S et des opérations simultanées sur plusieurs cœurs.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-112">Async programming is a key technique that makes it straightforward to handle blocking I/O and concurrent operations on multiple cores.</span></span> <span data-ttu-id="2c0a1-113">.NET offre aux applications et services la possibilité d’être réactifs et élastiques avec des modèles de programmation en C#, VB et F# asynchrones au niveau du langage et faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-113">.NET provides the capability for apps and services to be responsive and elastic with easy-to-use, language-level asynchronous programming models in C#, VB, and F#.</span></span>

## <a name="why-write-async-code"></a><span data-ttu-id="2c0a1-114">Pourquoi écrire du code asynchrone ?</span><span class="sxs-lookup"><span data-stu-id="2c0a1-114">Why Write Async Code?</span></span>

<span data-ttu-id="2c0a1-115">Les applications modernes utilisent beaucoup d’E/S de fichier et de réseau.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-115">Modern apps make extensive use of file and networking I/O.</span></span> <span data-ttu-id="2c0a1-116">Les API d’E/S se bloquent par défaut, ce qui se traduit par une expérience utilisateur et une utilisation du matériel médiocres, sauf si vous avez l’intention d’apprendre et d’utiliser des modèles complexes.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-116">I/O APIs traditionally block by default, resulting in poor user experiences and hardware utilization unless you want to learn and use challenging patterns.</span></span> <span data-ttu-id="2c0a1-117">Les API asynchrones basées sur des tâches et le modèle de programmation asynchrone au niveau du langage inversent ce modèle en faisant de l’exécution asynchrone la valeur par défaut avec quelques nouveaux concepts à découvrir.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-117">Task-based async APIs and the language-level asynchronous programming model invert this model, making async execution the default with few new concepts to learn.</span></span>

<span data-ttu-id="2c0a1-118">Le code asynchrone présente les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="2c0a1-118">Async code has the following characteristics:</span></span>

* <span data-ttu-id="2c0a1-119">Il gère davantage de demandes de serveur en cédant des threads pour traiter plus de demandes quand il attend le retour des demande d’E/S.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-119">Handles more server requests by yielding threads to handle more requests while waiting for I/O requests to return.</span></span>
* <span data-ttu-id="2c0a1-120">Il permet aux interfaces utilisateur d’être plus réactives en cédant des threads à l’interaction de l’interface utilisateur quand il attend les demandes d’E/S et en transmettant les tâches d’exécution longue aux autres cœurs de processeur.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-120">Enables UIs to be more responsive by yielding threads to UI interaction while waiting for I/O requests and by transitioning long-running work to other CPU cores.</span></span>
* <span data-ttu-id="2c0a1-121">De nombreuses API .NET plus récentes sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="2c0a1-121">Many of the newer .NET APIs are asynchronous.</span></span>
* <span data-ttu-id="2c0a1-122">Il est facile d’écrire du code asynchrone dans .NET !</span><span class="sxs-lookup"><span data-stu-id="2c0a1-122">It's easy to write async code in .NET!</span></span>

## <a name="whats-next"></a><span data-ttu-id="2c0a1-123">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2c0a1-123">What's next?</span></span>

<span data-ttu-id="2c0a1-124">Pour une présentation détaillée des concepts et de la programmation asynchrones, consultez [Async en détail](async-in-depth.md) et [Programmation asynchrone basée sur des tâches](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="2c0a1-124">For a deep dive into async concepts and programming, see [Async in depth](async-in-depth.md) and [Task-based asynchronous programming](~/docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>

