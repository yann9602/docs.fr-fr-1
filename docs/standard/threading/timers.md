---
title: Minuteries
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
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fca27cf5261e253c2bb3d3a10fa3db31f28a2415
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="timers"></a>Minuteries
Les minuteurs sont des objets légers qui vous permettent de spécifier un délégué est appelé à une heure spécifiée. Un thread dans le pool de threads effectue l’opération d’attente.  
  
 À l’aide de la <xref:System.Threading.Timer?displayProperty=nameWithType> classe est simple. Vous créez un **Timer**, en passant un <xref:System.Threading.TimerCallback> délégué à la méthode de rappel, un objet représentant l’état qui sera passé au rappel, un temps de déclenchement initial et un temps représentant l’intervalle entre les appels de rappel. Pour annuler une minuterie en attente, appelez le **Timer.Dispose** (fonction).  
  
> [!NOTE]
>  Il existe deux autres classes de minuterie. La <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> classe est un contrôle qui fonctionne avec les concepteurs visuels et est destiné à être utilisé dans des contextes d’interface utilisateur ; il déclenche des événements sur le thread d’interface utilisateur. Le <xref:System.Timers.Timer?displayProperty=nameWithType> dérive de la classe <xref:System.ComponentModel.Component>, par conséquent, il peut être utilisé avec les concepteurs visuels ; il déclenche également des événements, mais elle déclenche les sur un <xref:System.Threading.ThreadPool> thread. Le <xref:System.Threading.Timer?displayProperty=nameWithType> classe effectue des rappels sur un <xref:System.Threading.ThreadPool> de thread et n’utilise pas le modèle d’événement du tout. Il fournit également un objet d’état à la méthode de rappel, qui n’exécutent pas les autres minuteurs. Il est très légère.  
  
 L’exemple de code suivant démarre une minuterie déclenche après une seconde (1000 millisecondes) et marque chaque seconde jusqu'à ce que vous appuyez sur la **entrée** clé. La variable contenant la référence à la minuterie est un champ de niveau classe, pour vous assurer que le minuteur n’est pas soumis au garbage collection pendant son exécution. Pour plus d’informations sur un garbage collection agressif, consultez <xref:System.GC.KeepAlive%2A>.  
  
 [!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
 [!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Timer>  
 [Fonctionnalités et objets de threading](../../../docs/standard/threading/threading-objects-and-features.md)
