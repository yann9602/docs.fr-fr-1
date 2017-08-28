---
title: "add (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- add_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
caps.latest.revision: 7
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0171cbb28c7d32cb4f8cad6bd46cd9aeda10fccc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="add-c-reference"></a>add (Référence C#)
Le mot clé contextuel `add` est utilisé pour définir un accesseur d’événement personnalisé qui est appelé quand le code client s’abonne à votre événement ([event](../../../csharp/language-reference/keywords/event.md)). Si vous fournissez un accesseur `add` personnalisé, vous devez également fournir un accesseur [remove](../../../csharp/language-reference/keywords/remove.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un événement qui a des accesseurs `add` et [remove](../../../csharp/language-reference/keywords/remove.md) personnalisés. Pour obtenir l’exemple complet, consultez [Guide pratique pour implémenter des événements d’interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-cs[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 En général, vous n’avez pas besoin de fournir vos propres accesseurs d’événements personnalisés. Les accesseurs générés automatiquement par le compilateur quand vous déclarez un événement sont suffisants pour la plupart des scénarios.  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)

