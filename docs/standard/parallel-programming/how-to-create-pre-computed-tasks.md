---
title: "How to: Create Pre-Computed Tasks | Microsoft Docs"
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
  - "tasks, creating pre-computed"
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# How to: Create Pre-Computed Tasks
Ce document décrit comment utiliser la méthode <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=fullName> pour récupérer les résultats d'opérations de téléchargement asynchrones qui sont conservées dans un cache.  La méthode <xref:System.Threading.Tasks.Task.FromResult%2A> retourne un objet de fin <xref:System.Threading.Tasks.Task%601> qui contient la valeur fournie comme sa propriété <xref:System.Threading.Tasks.Task%601.Result%2A>.  Cette méthode est utile lorsque vous exécutez une opération asynchrone qui retourne un objet <xref:System.Threading.Tasks.Task%601>, et que le résultat de cet objet <xref:System.Threading.Tasks.Task%601> est déjà calculé.  
  
## Exemple  
 L'exemple suivant télécharge les chaînes du Web.  Il définit la méthode `DownloadStringAsync`.  Cette méthode télécharge de manière asynchrone des chaînes à partir du web.  Cet exemple utilise également un objet <xref:System.Collections.Concurrent.ConcurrentDictionary%602> pour mettre en cache les résultats des opérations précédentes.  Si l'adresse d'entrée est conservée dans le cache, `DownloadStringAsync` utilise la méthode <xref:System.Threading.Tasks.Task.FromResult%2A> pour créer un objet <xref:System.Threading.Tasks.Task%601> qui contient le contenu à cette adresse.  Sinon, `DownloadStringAsync` télécharge le fichier du Web et ajoute le résultat au cache.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 L'exemple suivant calcule le temps nécessaire pour télécharger les chaînes multiples deux fois.  Le second ensemble d'opérations de téléchargement doit prendre moins de temps que le premier car les résultats sont conservés dans le cache.  La méthode <xref:System.Threading.Tasks.Task.FromResult%2A> permet à la méthode `DownloadStringAsync` de créer les objets <xref:System.Threading.Tasks.Task%601> qui contiennent ces résultats avant calculs.  
  
## Compilation du code  
 Copiez l'exemple de code et collez\-le dans un projet Visual Studio, ou collez\-le dans un fichier nommé `CachedDownloads.cs`\(`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]\), exécutez ensuite la commande suivante dans une fenêtre d'invite de commandes Visual Studio .  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## Programmation fiable  
  
## Voir aussi  
 [Task Parallelism](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)