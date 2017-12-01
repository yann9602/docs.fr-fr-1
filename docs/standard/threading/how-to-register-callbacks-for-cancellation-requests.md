---
title: "Comment : enregistrer des rappels pour les demandes d'annulation"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Comment : enregistrer des rappels pour les demandes d'annulation
L’exemple suivant montre comment inscrire un délégué qui sera appelé quand un <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriété prend la valeur true en raison d’un appel à <xref:System.Threading.CancellationTokenSource.Cancel%2A> sur l’objet qui a créé le jeton. Utilisez cette technique pour l'annulation des opérations asynchrones qui ne prennent pas en charge l'infrastructure d'annulation unifiée en mode natif, ainsi que pour le déblocage des méthodes qui peuvent attendre la fin d'une opération asynchrone.  
  
> [!NOTE]
>  Quand l'option Uniquement mon code est activée, Visual Studio, dans certains cas, peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur indiquant que l'exception n'est pas gérée par le code utilisateur. Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s’arrêter sur la première erreur, il suffit de désactiver la case à cocher « Uniquement mon Code » sous **outils, Options, débogage, général**.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, la méthode <xref:System.Net.WebClient.CancelAsync%2A> est enregistrée comme la méthode à appeler quand une annulation est demandée via le jeton d'annulation.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Si l'annulation a déjà été demandée quand le rappel est enregistré, le rappel sera malgré tout appelé. Dans ce cas particulier, la méthode <xref:System.Net.WebClient.CancelAsync%2A> ne fera rien si aucune opération asynchrone n'est en cours. Il est donc sans risque d'appeler la méthode.  
  
## <a name="see-also"></a>Voir aussi  
 [Annulation dans les threads managés](../../../docs/standard/threading/cancellation-in-managed-threads.md)
