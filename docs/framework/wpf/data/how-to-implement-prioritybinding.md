---
title: "Comment : implémenter PriorityBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: data binding [WPF], PriorityBinding class
ms.assetid: d63b65ab-b3e9-4322-9aa8-1450f8d89532
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9753462908928eaf177e100a16186826bf4828ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-prioritybinding"></a>Comment : implémenter PriorityBinding
<xref:System.Windows.Data.PriorityBinding>dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fonctionne en spécifiant une liste de liaisons. La liste de liaisons est classée de priorité la plus élevée à la priorité la plus faible. Si la liaison de priorité la plus élevée retourne une valeur avec succès lorsqu’il est traité puis il est jamais nécessaire pour traiter les autres liaisons dans la liste. Il peut être le cas de la liaison de priorité la plus élevée prend beaucoup de temps à évaluer, la priorité la plus élevée suivante qui retourne une valeur avec succès est utilisée jusqu'à ce qu’une liaison d’une priorité plus élevée retourne une valeur avec succès.  
  
## <a name="example"></a>Exemple  
 Pour illustrer comment <xref:System.Windows.Data.PriorityBinding> fonctionne, le `AsyncDataSource` objet a été créé avec les trois propriétés suivantes : `FastDP`, `SlowerDP`, et `SlowestDP`.  
  
 L’accesseur get de `FastDP` retourne la valeur de la `_fastDP` membre de données.  
  
 L’accesseur get de `SlowerDP` attend trois secondes avant de retourner la valeur de la `_slowerDP` membre de données.  
  
 L’accesseur get de `SlowestDP` attend 5 secondes avant de retourner la valeur de la `_slowestDP` membre de données.  
  
> [!NOTE]
>  Cet exemple est uniquement à des fins de démonstration. Le [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] recommandé par rapport à la définition des propriétés qui sont beaucoup plus lente qu’un ensemble de champs. Pour plus d’informations, consultez [NIB : choix entre les propriétés et méthodes](http://msdn.microsoft.com/en-us/55825e8f-7e2e-448a-9505-7217cc91b1af).  
  
 [!code-csharp[PriorityBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[PriorityBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PriorityBinding/VisualBasic/AsyncDataSource.vb#1)]  
  
 Le <xref:System.Windows.Controls.TextBlock.Text%2A> propriété est liée à la liste ci-dessus `AsyncDS` à l’aide de <xref:System.Windows.Data.PriorityBinding>:  
  
 [!code-xaml[PriorityBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PriorityBinding/CSharp/Window1.xaml#2)]  
  
 Lorsque le moteur de liaison traite les <xref:System.Windows.Data.Binding> des objets, il commence par la première <xref:System.Windows.Data.Binding>, qui est lié à la `SlowestDP` propriété. Lorsque cela <xref:System.Windows.Data.Binding> est traité, il ne retourne pas de valeur avec succès, car il est en veille pendant 5 secondes, par conséquent, la prochaine <xref:System.Windows.Data.Binding> élément est traité. La prochaine <xref:System.Windows.Data.Binding> ne retourne pas de valeur avec succès, car il est en veille pendant 3 secondes. Le moteur de liaison, puis déplace sur la prochaine <xref:System.Windows.Data.Binding> élément, qui est lié à la `FastDP` propriété. Cela <xref:System.Windows.Data.Binding> retourne la valeur « rapide ». Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « rapide ».  
  
 Après 3 secondes, la `SlowerDP` propriété retourne la valeur « Valeur plus lent ». Le <xref:System.Windows.Controls.TextBlock> puis affiche la valeur « Valeur plus lent ».  
  
 Après 5 secondes, la `SlowestDP` propriété retourne la valeur « Les plus lents Value ». Cette liaison a la priorité la plus élevée, car elle est répertoriée en premier. Le <xref:System.Windows.Controls.TextBlock> affiche maintenant la valeur « Les plus lents Value ».  
  
 Consultez <xref:System.Windows.Data.PriorityBinding> pour plus d’informations sur ce qui est considéré comme une valeur de retour réussite d’une liaison.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.Binding.IsAsync%2A?displayProperty=nameWithType>  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
