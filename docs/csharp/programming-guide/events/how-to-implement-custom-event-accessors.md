---
title: "Guide pratique pour implémenter des accesseurs d’événement personnalisés (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
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
ms.openlocfilehash: 71e1c16c9c6426ffb95020e4d7211dc1000f6796
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Guide pratique pour implémenter des accesseurs d’événement personnalisés (Guide de programmation C#)
Un événement constitue un genre spécial de délégué multicast qui peut être appelé uniquement à partir de la classe dans laquelle il est déclaré. Le code client s’abonne à l’événement en fournissant une référence à une méthode qui doit être appelée quand l’événement est déclenché. Ces méthodes sont ajoutées à la liste d’invocation du délégué par le biais des accesseurs d’événement, qui ressemblent aux accesseurs de propriété, sauf que les accesseurs d’événement sont nommés `add` et `remove`. Dans la plupart des cas, vous n’avez pas à fournir d’accesseurs d’événement personnalisés. Quand aucun accesseur d’événement personnalisé n’est fourni dans votre code, le compilateur les ajoute automatiquement. Toutefois, vous devez parfois fournir un comportement personnalisé. Ce genre de cas est illustré dans la rubrique [Guide pratique pour implémenter des événements d’interface](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant indique comment implémenter des accesseurs d’événement add et remove. Même si vous pouvez remplacer le code à l’intérieur des accesseurs, nous vous recommandons de verrouiller l’événement avant d’ajouter ou de supprimer une nouvelle méthode de gestionnaire d’événements.  
  
```  
event EventHandler IDrawingObject.OnDraw  
        {  
            add  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent += value;  
                }  
            }  
            remove  
            {  
                lock (PreDrawEvent)  
                {  
                    PreDrawEvent -= value;  
                }  
            }  
        }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [event](../../../csharp/language-reference/keywords/event.md)

