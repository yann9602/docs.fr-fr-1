---
title: "Optimization for Shared Web Hosting | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "garbage collection, Web hosting"
  - "garbage collection, optimizing"
  - "garbage collection, shared Web hosting"
ms.assetid: be98c0ab-7ef8-409f-8a0d-cb6e5b75ff20
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Optimization for Shared Web Hosting
Si vous êtes l'administrateur d'un serveur qui est partagé en hébergeant plusieurs petits sites Web, vous pouvez optimiser ses performances et augmenter la capacité des sites en ajoutant le paramètre `gcTrimCommitOnLowMemory` suivant au nœud `runtime` dans le fichier Aspnet.config du répertoire .NET Framework :  
  
 `<gcTrimCommitOnLowMemory enabled="true|false"/>`  
  
> [!NOTE]
>  Ce paramètre est recommandé uniquement dans le cas de scénarios d'hébergement Web partagés.  
  
 Comme le garbage collector conserve la mémoire en vue de l'allouer ultérieurement, l'espace alloué peut être supérieur aux besoins.  Vous pouvez réduire cet espace pour faire face aux situations de surcharge de la mémoire système.  Cette diminution améliore les performances et permet d'héberger davantage de sites.  
  
 Lorsque le paramètre `gcTrimCommitOnLowMemory` est activé, le garbage collector évalue la charge de mémoire système et entre un mode de suppression lorsque la charge atteint 90 %.  Il maintient le mode de suppression jusqu'à ce que la charge passe au\-dessous de 85 %.  
  
 Si les conditions le permettent, le garbage collector peut décider que le paramètre `gcTrimCommitOnLowMemory` n'aidera pas l'application actuelle et qu'il peut donc l'ignorer.  
  
## Exemple  
 Le fragment XML suivant indique comment activer le paramètre `gcTrimCommitOnLowMemory`.  Les points de suspension indiquent d'autres paramètres du nœud `runtime`.  
  
```  
<?xml version="1.0" encoding="UTF-8"?>  
<configuration>  
    <runtime>  
    . . .  
    <gcTrimCommitOnLowMemory enabled="true"/>  
    </runtime>  
    . . .  
</configuration>  
```  
  
## Voir aussi  
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)