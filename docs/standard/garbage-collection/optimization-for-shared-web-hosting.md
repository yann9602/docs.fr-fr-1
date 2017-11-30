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
# <a name="optimization-for-shared-web-hosting"></a>Optimisation de l'hébergement Web partagé
Si vous êtes l’administrateur pour un serveur qui est partagé en hébergeant plusieurs petits sites Web, vous pouvez optimiser les performances et augmenter la capacité du site en ajoutant le code suivant `gcTrimCommitOnLowMemory` affectant le `runtime` nœud dans le fichier Aspnet.config dans .NET répertoire :  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Ce paramètre est recommandé uniquement pour le Web partagé scénarios d’hébergement.  
  
 Étant donné que le garbage collector conserve la mémoire pour les futures allocations, l’espace alloué peut être supérieur à ce qui est strictement nécessaire. Vous pouvez réduire cet espace pour faire face aux situations lorsqu’il existe une charge importante sur la mémoire système. Cette diminution améliore les performances et développe la capacité d’héberger plusieurs sites.  
  
 Lorsque le `gcTrimCommitOnLowMemory` est activé, le garbage collector évalue la charge de mémoire système et entre un mode de suppression lorsque la charge atteint 90 %. Il conserve le mode de suppression jusqu'à ce que la charge soit inférieure à 85 %.  
  
 Lorsque les conditions le permettent, le garbage collector peut décider que la `gcTrimCommitOnLowMemory` paramètre pas aider à l’application actuelle et l’ignorer.  
  
## <a name="example"></a>Exemple  
 Le fragment XML suivant montre comment activer la `gcTrimCommitOnLowMemory` paramètre. Points de suspension indiquent d’autres paramètres qui seraient dans le `runtime` nœud.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Nettoyage de la mémoire](../../../docs/standard/garbage-collection/index.md)
