---
title: "Comment : déclencher et utiliser des événements"
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
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a>Comment : déclencher et utiliser des événements
Les exemples de cette rubrique montrent comment utiliser des événements. Ils incluent des exemples de la <xref:System.EventHandler> délégué, le <xref:System.EventHandler%601> délégué et un délégué personnalisé, pour illustrer des événements avec et sans les données.  
  
 Les exemples utilisent les concepts décrits dans le [événements](../../../docs/standard/events/index.md) l’article.  
  
## <a name="example"></a>Exemple  
 Le premier exemple montre comment déclencher et de consommer un événement n’ayant pas de données. Il contient une classe nommée `Counter` qui possède un événement nommé `ThresholdReached`. Cet événement est déclenché lorsqu’une valeur de compteur est égal à ou dépasse un seuil. Le <xref:System.EventHandler> délégué est associé à l’événement, car aucune donnée d’événement n’est fournie.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclencher et de consommer un événement qui fournit des données. Le <xref:System.EventHandler%601> délégué est associé à l’événement, et une instance d’un objet de données d’événement personnalisé est fournie.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déclarer un délégué pour un événement. Le délégué est appelé `ThresholdReachedEventHandler`. Il s’agit d’obtenir une illustration. En règle générale, il est inutile de déclarer un délégué d’un événement, car vous pouvez utiliser soit le <xref:System.EventHandler> ou <xref:System.EventHandler%601> déléguer. Vous devez déclarer un délégué uniquement dans les rares scénarios, par exemple, votre classe disponible pour le code hérité qui ne peut pas utiliser des classes génériques.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../docs/standard/events/index.md)
