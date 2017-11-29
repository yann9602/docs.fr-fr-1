---
title: "Comment : utiliser un dictionnaire pour stocker des instances d'événements (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0304f04233151d35c8ee18fe09feac91fbd0879b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Comment : utiliser un dictionnaire pour stocker des instances d'événements (Guide de programmation C#)
Une des façons d’utiliser `accessor-declarations` consiste à exposer un grand nombre d’événements sans allouer de champ à chaque événement, mais en utilisant à la place un dictionnaire pour stocker les instances d’événements. Cette méthode n’est utile qu’en présence d’un grand nombre d’événements dont la plupart ne seront pas implémentés.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Événements](../../../csharp/programming-guide/events/index.md)  
 [Délégués](../../../csharp/programming-guide/delegates/index.md)
