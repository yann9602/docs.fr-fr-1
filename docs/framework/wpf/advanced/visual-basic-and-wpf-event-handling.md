---
title: "Gestion des événements Visual Basic et WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca55e31060388012e6bb94e40159c2e602484911
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-and-wpf-event-handling"></a>Gestion des événements Visual Basic et WPF
Pour le [!INCLUDE[TLA#tla_visualbnet](../../../../includes/tlasharptla-visualbnet-md.md)] langage en particulier, vous pouvez utiliser spécifique au langage `Handles` mot clé à associer des gestionnaires d’événements avec des instances, au lieu d’attacher des gestionnaires d’événements avec des attributs ou à l’aide de la <xref:System.Windows.UIElement.AddHandler%2A> (méthode). La technique `Handles` présente toutefois quelques limitations, car la syntaxe de `Handles` ne prend pas en charge certaines fonctionnalités d’événement routé spécifiques du système d’événement [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="using-handles-in-a-wpf-application"></a>Utilisation de « handles » dans une application WPF  
 Les gestionnaires d’événements connectés à des instances et à des événements par le biais de `Handles` doivent être définis dans la déclaration de classe partielle de l’instance. C’est également le cas des gestionnaires d’événements assignés par le biais de valeurs d’attribut sur les éléments. Vous ne pouvez spécifier `Handles` d’un élément sur la page qui comporte un <xref:System.Windows.FrameworkContentElement.Name%2A> valeur de la propriété (ou [Directive x : Name](../../../../docs/framework/xaml-services/x-name-directive.md) déclaré). C’est parce que le <xref:System.Windows.FrameworkContentElement.Name%2A> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] crée la référence d’instance qui est nécessaire pour prendre en charge la *instance.événement* au format de référence requis par le `Handles` syntaxe. Le seul élément qui peut être utilisé pour `Handles` sans un <xref:System.Windows.FrameworkContentElement.Name%2A> référence est l’instance de l’élément racine qui définit la classe partielle.  
  
 Vous pouvez assigner le même gestionnaire à plusieurs éléments en séparant les références *Instance.Event* après `Handles` par des virgules.  
  
 Vous pouvez utiliser `Handles` pour assigner plusieurs gestionnaires à la même référence *Instance.Event*. Ne vous préoccupez pas de l’ordre dans lequel les gestionnaires sont introduits dans la référence `Handles` ; considérez que les gestionnaires qui gèrent le même événement peuvent être appelés dans n’importe quel ordre.  
  
 Pour supprimer un gestionnaire qui a été ajouté avec `Handles` dans la déclaration, vous pouvez appeler <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Vous pouvez utiliser `Handles` pour joindre des gestionnaires pour des événements routés, pour autant que vous joignez les gestionnaires à des instances qui définissent l’événement géré dans leurs tables de membres. Pour les événements routés, les gestionnaires qui sont attachés avec `Handles` suivent les mêmes règles de routage comme gestionnaires qui sont attachés en tant que [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributs, ou avec la signature commune de <xref:System.Windows.UIElement.AddHandler%2A>. Cela signifie que si l’événement est déjà marqué comme géré (la <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété dans les données d’événement est `True`), puis les gestionnaires joints avec `Handles` ne sont pas appelés en réponse à cette instance d’événement. L’événement peut être marqué comme géré par des gestionnaires d’instance sur un autre élément sur l’itinéraire, ou par la gestion de classe sur l’élément actuel ou sur des éléments antérieurs le long de l’itinéraire. Dans le cas d’événements d’entrée prenant en charge des événements de tunneling/propagation couplés, il est possible que l’itinéraire de tunneling ait marqué la paire d’événements comme gérée. Pour plus d’informations sur les événements routés, consultez [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Limitations de « Handles » dans le cadre de l’ajout de gestionnaires  
 `Handles` ne peut pas référencer de gestionnaires pour des événements attachés. Vous devez utiliser la méthode d’accesseur `add` pour cet événement attaché ou des attributs d’événement *nom_type.nom_événement* en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Pour plus d’informations, consultez [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Pour les événements routés, vous pouvez uniquement utiliser `Handles` pour assigner des gestionnaires aux instances où cet événement apparaît dans la table de membres. Dans le cas des événements routés en général, un élément parent peut toutefois jouer le rôle d’écouteur pour un événement des éléments enfants, même si ce dernier ne figure pas dans la table de membres de l’événement parent. Dans la syntaxe d’attribut, vous pouvez spécifier cela à l’aide d’une forme d’attribut *nom_type.nom_événement* qui qualifie le type qui définit réellement l’événement que vous souhaitez gérer. Par exemple, un parent `Page` (sans aucune `Click` événement défini) peut écouter des événements de clic de bouton en assignant un gestionnaire d’attribut sous la forme `Button.Click`. `Handles` ne prend cependant pas en charge le format *nom_type.nom_événement*, car il doit prendre en charge un format *instance.événement* incompatible. Pour plus d’informations, consultez [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 `Handles` ne peut pas joindre des gestionnaires appelés pour des événements déjà marqués comme gérés. Au lieu de cela, vous devez utiliser le code et appeler le `handledEventsToo` surcharge de <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  N’utilisez pas la syntaxe `Handles` dans le code [!INCLUDE[vb_current_short](../../../../includes/vb-current-short-md.md)] quand vous spécifiez un gestionnaire d’événements pour le même événement en XAML. Dans ce cas, le gestionnaire d’événements est appelé deux fois.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Implémentation de la fonctionnalité « Handles » par WPF  
 Quand un [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] page est compilée, le fichier intermédiaire déclare `Friend` `WithEvents` des références à tous les éléments sur la page qui comporte un <xref:System.Windows.FrameworkContentElement.Name%2A> jeu de propriétés (ou [Directive x : Name](../../../../docs/framework/xaml-services/x-name-directive.md) déclaré). Chaque instance nommée est un élément susceptible d’être assigné à un gestionnaire par le biais de `Handles`.  
  
> [!NOTE]
>  Dans [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] peut vous montrer la complétion pour laquelle des éléments sont disponibles pour une référence `Handles` dans une page. Une étape de compilation peut toutefois s’avérer nécessaire pour permettre au fichier intermédiaire de remplir toutes les références `Friends`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [Marquage des événements routés comme gérés et gestion de classe](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Vue d’ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
