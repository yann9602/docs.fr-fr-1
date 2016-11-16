---
title: "Vue d’ensemble d’async"
description: "Vue d’ensemble d’async"
keywords: .NET, .NET Core
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
translationtype: Human Translation
ms.sourcegitcommit: 9abc4879533074e6830a7343123b139e912d239b
ms.openlocfilehash: 39dc9e8599daea86b48d864179c13c5ae965876b

---

# <a name="async-overview"></a>Vue d’ensemble d’async

Il n’y a pas si longtemps, il suffisait d’acheter un PC ou un serveur plus récent pour que les applications soient plus rapides. Mais ce n’est plus le cas maintenant. En fait, c’est même tout le contraire. Les téléphones mobiles utilisent des processeurs ARM 1 GHz à cœur unique et les charges de travail serveur sont passées aux machines virtuelles. Les utilisateurs veulent toujours une interface utilisateur réactive et les chefs d’entreprise veulent des serveurs qui s’adaptent à leur activité. La transition vers le mobile et le cloud ainsi qu’une population de plus de 3 milliards d’utilisateurs connectés à Internet ont donné naissance à un nouvel ensemble de modèles logiciels. 

* Les applications clientes doivent être toujours actives, toujours connectées, constamment réactives à l’interaction de l’utilisateur (interface tactile, par exemple) et en haut du classement des magasins d’applications !
* Les services doivent gérer les pics de trafic en ayant la possibilité de monter et descendre en puissance facilement. 

La programmation asynchrone est une technique clé qui facilite le blocage des E/S et des opérations simultanées sur plusieurs cœurs. .NET offre aux applications et services la possibilité d’être réactifs et élastiques avec des modèles de programmation en C#, VB et F# asynchrones au niveau du langage et faciles à utiliser.

## <a name="why-write-async-code"></a>Pourquoi écrire du code asynchrone ?

Les applications modernes utilisent beaucoup d’E/S de fichier et de réseau. Les API d’E/S se bloquent par défaut, ce qui se traduit par une expérience utilisateur et une utilisation du matériel médiocres, sauf si vous avez l’intention d’apprendre et d’utiliser des modèles complexes. Les API asynchrones et le modèle de programmation asynchrone au niveau du langage inversent ce modèle en faisant de l’exécution asynchrone la valeur par défaut avec quelques nouveaux concepts à découvrir.

Le code asynchrone présente les caractéristiques suivantes :

* Il gère davantage de demandes de serveur en cédant des threads pour traiter plus de demandes quand il attend le retour des demande d’E/S.
* Il permet aux interfaces utilisateur d’être plus réactives en cédant des threads à l’interaction de l’interface utilisateur quand il attend les demandes d’E/S et en transmettant les tâches d’exécution longue aux autres cœurs de processeur.
* De nombreuses API .NET plus récentes sont asynchrones.
* Il est très facile d’écrire du code asynchrone dans .NET !

## <a name="whats-next"></a>Quelle est la suite ?

Pour une présentation détaillée des concepts et de la programmation asynchrones, consultez [Async en détail](async-in-depth.md).




<!--HONumber=Nov16_HO1-->


