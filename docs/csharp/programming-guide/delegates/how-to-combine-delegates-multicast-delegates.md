---
title: "Comment : combiner des délégués (délégués multicast) (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a>Comment : combiner des délégués (délégués multicast) (Guide de programmation C#)
Cet exemple explique comment créer des délégués multicast. Une propriété utile des objets [délégués](../../../csharp/language-reference/keywords/delegate.md) est que plusieurs objets peuvent être assignés à une instance de délégué à l’aide de l’opérateur `+`. Le délégué multicast contient une liste des délégués assignés. Quand le délégué multicast est appelé, il appelle les délégués dans la liste, dans l’ordre. Seuls des délégués de même type peuvent être combinés.  
  
 Vous pouvez utiliser l’opérateur `-` pour supprimer un délégué de composant d’un délégué multicast.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.MulticastDelegate>  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Événements](../../../csharp/programming-guide/events/index.md)
