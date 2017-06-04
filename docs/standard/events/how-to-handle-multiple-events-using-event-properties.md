---
title: "Comment&#160;: g&#233;rer plusieurs &#233;v&#233;nements &#224; l&#39;aide des propri&#233;t&#233;s d&#39;&#233;v&#233;nements | Microsoft Docs"
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
  - "gestion des événements (.NET Framework), avec plusieurs événements"
  - "propriétés d'événement (.NET Framework)"
  - "événements (.NET Framework), multiples"
  - "événements multiples (.NET Framework)"
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: g&#233;rer plusieurs &#233;v&#233;nements &#224; l&#39;aide des propri&#233;t&#233;s d&#39;&#233;v&#233;nements
Pour utiliser des propriétés d'événements, définissez les propriétés d'événements dans la classe qui déclenche les événements, puis affectez les délégués pour les propriétés d'événements dans les classes qui gèrent les événements.  Pour implémenter plusieurs propriétés d'événements dans une classe, la classe doit stocker et maintenir le délégué défini pour chaque événement en interne.  Une approche courante consiste à implémenter une collection de délégués indexée par une clé d'événement.  
  
 Pour stocker les délégués pour chaque événement, vous pouvez utiliser la classe <xref:System.ComponentModel.EventHandlerList> ou implémenter votre propre collection.  La classe de collection doit fournir des méthodes pour le paramétrage, l'accès et la récupération du délégué de gestionnaire d'événements selon la clé d'événement.  Par exemple, vous pouvez utiliser une classe <xref:System.Collections.Hashtable> ou dériver une classe personnalisée de la classe <xref:System.Collections.DictionaryBase>.  Les détails de l'implémentation de la collection de délégués ne doivent pas être exposés à l'extérieur de votre classe.  
  
 Chaque propriété d'événement dans la classe définit une méthode d'accesseur add et une méthode d'accesseur remove.  L'accesseur add pour une propriété d'événement ajoute l'instance de délégué d'entrée à la collection de délégués.  L'accesseur remove pour une propriété d'événement supprime l'instance de délégué d'entrée de la collection de délégués.  Les accesseurs de propriété d'événement utilisent la clé prédéfinie pour la propriété d'événement pour ajouter et supprimer des instances de la collection de délégués.  
  
### Pour gérer plusieurs événements à l'aide de propriétés d'événements  
  
1.  Définissez une collection de délégués dans la classe qui déclenche les événements.  
  
2.  Définissez une clé pour chaque événement.  
  
3.  Définissez les propriétés d'événements dans la classe qui déclenche les événements.  
  
4.  Utilisez la collection de délégués pour implémenter les méthodes d'accesseur add et remove pour les propriétés d'événements.  
  
5.  Utilisez les propriétés d'événements publiques pour ajouter et supprimer des délégués de gestionnaire d'événements dans les classes qui gèrent les événements.  
  
## Exemple  
 L'exemple C\# suivant implémente les propriétés d'événements `MouseDown` et `MouseUp`, à l'aide d'un <xref:System.ComponentModel.EventHandlerList> pour stocker le délégué de chaque événement.  Les mots clés des constructions des propriétés d'événements sont en gras.  
  
> [!NOTE]
>  Les propriétés d'événements ne sont pas prises en charge dans [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## Voir aussi  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=fullName>   
 [Événements](../../../docs/standard/events/index.md)   
 [System.Web.UI.Control.Events](frlrfSystemWebUIControlClassEventsTopic)   
 [How to: Declare Custom Events To Conserve Memory](../Topic/How%20to:%20Declare%20Custom%20Events%20To%20Conserve%20Memory%20\(Visual%20Basic\).md)