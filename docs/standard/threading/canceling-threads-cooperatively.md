---
title: "Annulation de threads de façon coopérative"
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
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 482f48b347af1a4f76231abcb15abc2f4dba168b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="canceling-threads-cooperatively"></a>Annulation de threads de façon coopérative
Avant [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework n’offrait aucune fonction intégrée permettant d’annuler, de manière coopérative, un thread après son démarrage. Toutefois, dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez utiliser des jetons d’annulation pour annuler les threads, tout comme vous pouvez les utiliser pour annuler <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objets ou des requêtes PLINQ. Bien que le <xref:System.Threading.Thread?displayProperty=nameWithType> classe n’offre pas de prise en charge intégrée pour les jetons d’annulation, vous pouvez passer un jeton à une procédure de thread à l’aide de la <xref:System.Threading.Thread> constructeur qui accepte un <xref:System.Threading.ParameterizedThreadStart> déléguer. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des threads et du threading](../../../docs/standard/threading/using-threads-and-threading.md)
