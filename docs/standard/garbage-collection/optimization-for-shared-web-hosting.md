---
title: "Optimisation de l'hébergement Web partagé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- garbage collection, Web hosting
- garbage collection, optimizing
- garbage collection, shared Web hosting
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1f423d867d4fada075800650627c94f9d09e9e7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="optimization-for-shared-web-hosting"></a><span data-ttu-id="7538f-102">Optimisation de l'hébergement Web partagé</span><span class="sxs-lookup"><span data-stu-id="7538f-102">Optimization for Shared Web Hosting</span></span>
<span data-ttu-id="7538f-103">Si vous êtes l’administrateur pour un serveur qui est partagé en hébergeant plusieurs petits sites Web, vous pouvez optimiser les performances et augmenter la capacité du site en ajoutant le code suivant `gcTrimCommitOnLowMemory` affectant le `runtime` nœud dans le fichier Aspnet.config dans .NET répertoire :</span><span class="sxs-lookup"><span data-stu-id="7538f-103">If you are the administrator for a server that is shared by hosting several small Web sites, you can optimize performance and increase site capacity by adding the following `gcTrimCommitOnLowMemory` setting to the `runtime` node in the Aspnet.config file in the .NET directory:</span></span>  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  <span data-ttu-id="7538f-104">Ce paramètre est recommandé uniquement pour le Web partagé scénarios d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="7538f-104">This setting is recommended only for shared Web hosting scenarios.</span></span>  
  
 <span data-ttu-id="7538f-105">Étant donné que le garbage collector conserve la mémoire pour les futures allocations, l’espace alloué peut être supérieur à ce qui est strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7538f-105">Because the garbage collector retains memory for future allocations, its committed space can be more than what is strictly needed.</span></span> <span data-ttu-id="7538f-106">Vous pouvez réduire cet espace pour faire face aux situations lorsqu’il existe une charge importante sur la mémoire système.</span><span class="sxs-lookup"><span data-stu-id="7538f-106">You can reduce this space to accommodate times when there is a heavy load on system memory.</span></span> <span data-ttu-id="7538f-107">Cette diminution améliore les performances et développe la capacité d’héberger plusieurs sites.</span><span class="sxs-lookup"><span data-stu-id="7538f-107">Reducing this committed space improves performance and expands the capacity to host more sites.</span></span>  
  
 <span data-ttu-id="7538f-108">Lorsque le `gcTrimCommitOnLowMemory` est activé, le garbage collector évalue la charge de mémoire système et entre un mode de suppression lorsque la charge atteint 90 %.</span><span class="sxs-lookup"><span data-stu-id="7538f-108">When the `gcTrimCommitOnLowMemory` setting is enabled, the garbage collector evaluates the system memory load and enters a trimming mode when the load reaches 90%.</span></span> <span data-ttu-id="7538f-109">Il conserve le mode de suppression jusqu'à ce que la charge soit inférieure à 85 %.</span><span class="sxs-lookup"><span data-stu-id="7538f-109">It maintains the trimming mode until the load drops under 85%.</span></span>  
  
 <span data-ttu-id="7538f-110">Lorsque les conditions le permettent, le garbage collector peut décider que la `gcTrimCommitOnLowMemory` paramètre pas aider à l’application actuelle et l’ignorer.</span><span class="sxs-lookup"><span data-stu-id="7538f-110">When conditions permit, the garbage collector can decide that the `gcTrimCommitOnLowMemory` setting will not help the current application and ignore it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7538f-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="7538f-111">Example</span></span>  
 <span data-ttu-id="7538f-112">Le fragment XML suivant montre comment activer la `gcTrimCommitOnLowMemory` paramètre.</span><span class="sxs-lookup"><span data-stu-id="7538f-112">The following XML fragment shows how to enable the `gcTrimCommitOnLowMemory` setting.</span></span> <span data-ttu-id="7538f-113">Points de suspension indiquent d’autres paramètres qui seraient dans le `runtime` nœud.</span><span class="sxs-lookup"><span data-stu-id="7538f-113">Ellipses indicate other settings that would be in the `runtime` node.</span></span>  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7538f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7538f-114">See Also</span></span>  
 [<span data-ttu-id="7538f-115">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="7538f-115">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
