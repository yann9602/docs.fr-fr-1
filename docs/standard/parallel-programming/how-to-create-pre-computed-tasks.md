---
title: "Comment : créer des tâches précalculées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a>Comment : créer des tâches précalculées
Ce document décrit comment utiliser le <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> méthode pour récupérer les résultats des opérations de téléchargement asynchrones qui sont conservées dans un cache. Le <xref:System.Threading.Tasks.Task.FromResult%2A> méthode retourne un fini <xref:System.Threading.Tasks.Task%601> objet qui contient la valeur fournie en tant que son <xref:System.Threading.Tasks.Task%601.Result%2A> propriété. Cette méthode est utile lorsque vous exécutez une opération asynchrone qui retourne un objet <xref:System.Threading.Tasks.Task%601>, et que le résultat de cet objet <xref:System.Threading.Tasks.Task%601> est déjà calculé.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant télécharge des chaînes à partir du web. Il définit le `DownloadStringAsync` (méthode). Cette méthode télécharge des chaînes à partir du web de façon asynchrone. Cet exemple utilise également un <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objet à mettre en cache les résultats des opérations précédentes. Si l’adresse d’entrée est maintenue dans ce cache, `DownloadStringAsync` utilise le <xref:System.Threading.Tasks.Task.FromResult%2A> méthode pour produire un <xref:System.Threading.Tasks.Task%601> objet qui contient le contenu à l’adresse. Dans le cas contraire, `DownloadStringAsync` télécharge le fichier à partir du web et ajoute le résultat dans le cache.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Cet exemple calcule le temps nécessaire pour télécharger plusieurs chaînes deux fois. Le deuxième ensemble d’opérations de téléchargement doit-elle prendre moins de temps que le premier jeu parce que les résultats sont conservés dans le cache. Le <xref:System.Threading.Tasks.Task.FromResult%2A> méthode permet le `DownloadStringAsync` méthode pour créer <xref:System.Threading.Tasks.Task%601> objets qui contiennent ces précalculée résultats.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `CachedDownloads.cs` (`CachedDownloads.vb` pour [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe CachedDownloads.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe CachedDownloads.vb**  
  
## <a name="robust-programming"></a>Programmation fiable  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone basée sur les tâches](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
