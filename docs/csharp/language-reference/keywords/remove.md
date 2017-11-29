---
title: "remove (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: remove_CSharpKeyword
helpviewer_keywords: remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66647dee0c4cc728ae5e19457a4a5ef0e7f72248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="remove-c-reference"></a>remove (Référence C#)
Le mot clé contextuel `remove` est utilisé pour définir un accesseur d’événement personnalisé qui est appelé quand le code client annule son abonnement à votre événement ([event](../../../csharp/language-reference/keywords/event.md)). Si vous fournissez un accesseur `remove` personnalisé, vous devez également fournir un accesseur [add](../../../csharp/language-reference/keywords/add.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un événement qui a des accesseurs [add](../../../csharp/language-reference/keywords/add.md) et `remove` personnalisés. Pour obtenir l’exemple complet, consultez [Guide pratique pour implémenter des événements d’interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 En général, vous n’avez pas besoin de fournir vos propres accesseurs d’événements personnalisés. Les accesseurs générés automatiquement par le compilateur quand vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)
