---
title: "Comment : gérer l'événement ContextMenuOpening"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ContextMenuOpening properties [WPF]
ms.assetid: 789652fb-1951-4217-934a-7843e355adf4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec8646a48f94fb9ffdcad14849416732618a06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-the-contextmenuopening-event"></a>Comment : gérer l'événement ContextMenuOpening
Le <xref:System.Windows.FrameworkElement.ContextMenuOpening> événement peut être géré dans une application pour ajuster un menu contextuel existant avant son pour afficher ou supprimer un menu qui serait affiché en définissant le <xref:System.Windows.RoutedEventArgs.Handled%2A> propriété `true` dans les données d’événement. La raison par défaut pour le paramètre <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true` de l’événement sont de données pour remplacer le menu entièrement avec un nouveau <xref:System.Windows.Controls.ContextMenu> de l’objet, qui requiert parfois l’annulation de l’opération et le démarrage d’une nouvelle ouverture. Si vous écrivez des gestionnaires pour les <xref:System.Windows.FrameworkElement.ContextMenuOpening> événement, vous devez être conscient des problèmes de synchronisation entre un <xref:System.Windows.Controls.ContextMenu> contrôle et le service est responsable de l’ouvrir et de positionner les menus contextuels pour les contrôles en général. Cette rubrique illustre quelques-unes des techniques de codage pour le menu contextuel de différents scénarios d’ouverture et présente un cas où le problème de synchronisation entre en jeu.  
  
 Il existe plusieurs scénarios pour gérer la <xref:System.Windows.FrameworkElement.ContextMenuOpening> événement :  
  
-   Ajuster les éléments de menu avant l’affichage.  
  
-   Remplacement de l’intégralité du menu avant l’affichage.  
  
-   Suppression d’un menu contextuel existant et ne rien afficher complètement.  
  
## <a name="example"></a>Exemple  
  
## <a name="adjusting-the-menu-items-before-display"></a>Ajuster les éléments de Menu avant l’affichage  
 Ajustement des éléments de menu existants est relativement simple et est probablement le scénario le plus courant. Vous pouvez procéder ainsi afin d’ajouter ou soustraire des options du menu contextuel en réponse à des informations d’état actuelles dans votre application ou les informations d’état particulier est disponibles en tant que propriété sur l’objet sur lequel le menu contextuel est demandé.  
  
 La technique générale consiste à obtenir la source de l’événement, qui est le contrôle qui a été clic, et obtenir le <xref:System.Windows.FrameworkElement.ContextMenu%2A> propriété à partir de celui-ci. Vous souhaitez généralement vérifier les <xref:System.Windows.Controls.ItemsControl.Items%2A> collection pour déterminer les éléments de menu contextuel existe dans le menu, déjà et puis ajoutez ou supprimez de nouveau approprié <xref:System.Windows.Controls.MenuItem> éléments vers ou à partir de la collection.  
  
 [!code-csharp[ContextMenuOpeningHandlers#AddItemNoHandle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#additemnohandle)]  
  
## <a name="replacing-the-entire-menu-before-display"></a>Remplacement de l’intégralité du Menu avant l’affichage  
 Un autre scénario est que si vous souhaitez remplacer l’intégralité du menu contextuel. Bien sûr vous pourriez également utiliser une variation du code précédent, pour supprimer chaque élément d’un menu contextuel existant et ajouter de nouveaux, en commençant par l’élément zéro. Mais l’approche la plus intuitive pour remplacer tous les éléments dans le menu contextuel consiste à créer un nouveau <xref:System.Windows.Controls.ContextMenu>, remplir avec des éléments, puis définissez le <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriété d’un contrôle à la nouvelle <xref:System.Windows.Controls.ContextMenu>.  
  
 Voici le code de gestionnaire simple pour remplacer un <xref:System.Windows.Controls.ContextMenu>. Le code fait référence à une personnalisée `BuildMenu` (méthode), qui est séparée car elle est appelée par plusieurs des exemples de gestionnaires.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceNoReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacenoreopen)]  
  
 [!code-csharp[ContextMenuOpeningHandlers#BuildMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#buildmenu)]  
  
 Toutefois, si vous utilisez ce style de gestionnaire pour <xref:System.Windows.FrameworkElement.ContextMenuOpening>, vous pouvez exposer un problème de synchronisation si l’objet sur lequel vous définissez la <xref:System.Windows.Controls.ContextMenu> n’a pas de menu contextuel préexistant. Lorsqu’un utilisateur clique sur un contrôle, <xref:System.Windows.FrameworkElement.ContextMenuOpening> est déclenché même si existants <xref:System.Windows.Controls.ContextMenu> est vide ou null. Mais dans ce cas, quelle que soit de nouveau <xref:System.Windows.Controls.ContextMenu> vous définissez sur la source élément arrive trop tard pour être affichées. En outre, si l’utilisateur se produit avec le bouton droit une deuxième fois, cette fois votre nouveau <xref:System.Windows.Controls.ContextMenu> s’affiche, la valeur est non null, votre gestionnaire remplacer correctement et afficher le menu lorsqu’il s’exécute une deuxième fois. Il propose deux solutions de contournement possibles :  
  
1.  Vérifiez que <xref:System.Windows.FrameworkElement.ContextMenuOpening> gestionnaires s’exécutent toujours sur des contrôles qui ont au moins un espace réservé <xref:System.Windows.Controls.ContextMenu> disponibles, que vous souhaitez remplacer par le code du gestionnaire. Dans ce cas, vous pouvez toujours utiliser le gestionnaire indiqué dans l’exemple précédent, mais vous souhaiterez généralement affecter un espace réservé <xref:System.Windows.Controls.ContextMenu> dans la balise initiale :  
  
     [!code-xaml[ContextMenuOpeningHandlers#XAMLWithInitCM](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml#xamlwithinitcm)]  
  
2.  Supposons que la première <xref:System.Windows.Controls.ContextMenu> valeur peut être null, selon une logique provisoire. Impossible de vérifier <xref:System.Windows.Controls.ContextMenu> pour valeur null ou utiliser un indicateur dans votre code pour vérifier si votre gestionnaire a été exécuté au moins une fois. Comme vous supposez que le <xref:System.Windows.Controls.ContextMenu> sur soit affiché, votre gestionnaire puis définit <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true` dans les données d’événement. Pour le <xref:System.Windows.Controls.ContextMenuService> qui est responsable de l’affichage du menu contextuel, un `true` valeur <xref:System.Windows.RoutedEventArgs.Handled%2A> dans l’événement données représentent une demande d’annulation de l’affichage pour le menu contextuel combinaison / contrôle qui a déclenché l’événement.  
  
 Maintenant que vous avez supprimé le menu contextuel potentiellement suspect, l’étape suivante consiste à fournir un nouveau, alors l’afficher. Définition du nouveau est fondamentalement identique à celle du gestionnaire précédent : vous générez un nouveau <xref:System.Windows.Controls.ContextMenu> et définissez la source de contrôle <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType> propriété avec lui. Cette étape supplémentaire est que vous devez maintenant forcer l’affichage du menu contextuel, car vous avez supprimé la première tentative. Pour forcer l’affichage, vous définissez la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A?displayProperty=nameWithType> propriété `true` dans le gestionnaire. Soyez prudent lorsque vous effectuez cette opération, car l’ouverture du menu contextuel dans le gestionnaire déclenche le <xref:System.Windows.FrameworkElement.ContextMenuOpening> à nouveau les événements. Si vous entrez à nouveau votre gestionnaire, il devient à l’infini récursive. C’est pourquoi vous devez toujours vérifier pour `null` ou utiliser un indicateur si vous ouvrez un menu contextuel à partir d’un <xref:System.Windows.FrameworkElement.ContextMenuOpening> Gestionnaire d’événements.  
  
## <a name="suppressing-any-existing-context-menu-and-displaying-no-context-menu"></a>Suppression d’un Menu contextuel existant et ne rien afficher  
 Le dernier scénario, l’écriture d’un gestionnaire qui supprime la totalité, un menu est rare. Si un contrôle donné n’est pas censé pour afficher un menu contextuel, il existe probablement plus appropriés façons de garantir que, en supprimant le menu uniquement quand un utilisateur le demande. Toutefois, si vous souhaitez utiliser le gestionnaire pour supprimer un menu contextuel et ne rien afficher, votre gestionnaire doit simplement définir <xref:System.Windows.RoutedEventArgs.Handled%2A> à `true` dans les données d’événement. Le <xref:System.Windows.Controls.ContextMenuService> qui est chargé pour afficher un menu contextuel vérifie les données d’événement de l’événement, il est déclenché sur le contrôle. Si l’événement a été marqué comme <xref:System.Windows.RoutedEventArgs.Handled%2A> n’importe où sur l’itinéraire, puis l’action d’ouverture menu contextuel qui a déclenché l’événement est supprimée.  
  
 [!code-csharp[ContextMenuOpeningHandlers#ReplaceReopen](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ContextMenuOpeningHandlers/CSharp/Pane1.xaml.cs#replacereopen)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.ContextMenu>  
 <xref:System.Windows.FrameworkElement.ContextMenu%2A?displayProperty=nameWithType>  
 [Vue d’ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)  
 [Vue d’ensemble de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md)
