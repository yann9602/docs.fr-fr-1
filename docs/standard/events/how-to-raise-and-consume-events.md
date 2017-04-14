---
title: "Comment&#160;: d&#233;clencher et utiliser des &#233;v&#233;nements | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "événements (.NET Framework), déclencher"
  - "événements (.NET Framework), exemples"
  - "déclencher des événements"
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# Comment&#160;: d&#233;clencher et utiliser des &#233;v&#233;nements
Les exemples de cette rubrique expliquent comment utiliser les événements.  Ils incluent des exemples du délégué <xref:System.EventHandler>, du délégué <xref:System.EventHandler%601>, et d'un délégué personnalisé, pour illustrer vos événements avec et sans données.  
  
 Les exemples utilisent des concepts décrits dans l'article [Événements](../../../docs/standard/events/index.md).  
  
## Exemple  
 Le premier exemple montre comment déclencher et consommer un événement qui n'a pas de données.  Il contient une classe nommée `Counter` qui possède un événement nommé `ThresholdReached`.  Cet événement est déclenché lorsqu'une valeur de compteur égale ou dépasse une valeur seuil.  Le délégué de <xref:System.EventHandler> est associé à l'événement, car aucune donnée d'événement n'est fournie.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## Exemple  
 L'exemple suivant illustre comment déclencher et consommer un événement qui fournit des données.  Le délégué d'<xref:System.EventHandler%601> est associé à l'événement, et une instance d'un objet de données d'événement personnalisée est fournie.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## Exemple  
 L'exemple suivant indique comment déclarer un délégué pour un événement.  Le délégué est nommé `ThresholdReachedEventHandler`.  Il ne s'agit que d'un exemple.  En général, vous ne devez pas déclarer un délégué d'événement, car vous pouvez soit utiliser <xref:System.EventHandler> ou le délégué <xref:System.EventHandler%601>.  Vous ne devez déclarer de délégué que dans de rares scénarios, comme pour rendre votre classe disponible au code hérité qui ne peut pas utiliser des génériques.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## Voir aussi  
 [Événements](../../../docs/standard/events/index.md)