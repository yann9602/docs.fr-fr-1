---
title: "Comment&#160;: ajouter un gestionnaire d&#39;&#233;v&#233;nements &#224; l&#39;aide de code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "gestionnaires d'événements, ajouter"
  - "XAML, ajouter des gestionnaires d'événements"
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Comment&#160;: ajouter un gestionnaire d&#39;&#233;v&#233;nements &#224; l&#39;aide de code
Cet exemple montre comment ajouter un gestionnaire d'événements à un élément à l'aide de code.  
  
 Si vous souhaitez ajouter un gestionnaire d'événements à un élément [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], et que la page avec balise contenant l'élément a déjà été chargée, vous devez ajouter le gestionnaire à l'aide de code.  Ou bien, si vous développez l'arborescence d'éléments pour une application uniquement à l'aide de code et que vous ne déclarez aucun élément à l'aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], vous pouvez appeler des méthodes spécifiques pour ajouter des gestionnaires d'événements à l'arborescence d'éléments construite.  
  
## Exemple  
 L'exemple suivant ajoute un nouveau <xref:System.Windows.Controls.Button> à une page existante définie initialement dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Un fichier code\-behind implémente une méthode de gestionnaire d'événements puis ajoute cette méthode sous forme de nouveau gestionnaire d'événements sur le <xref:System.Windows.Controls.Button>.  
  
 L'exemple [!INCLUDE[TLA2#tla_cshrp](../../../../includes/tla2sharptla-cshrp-md.md)] utilise l'opérateur `+=` pour assigner un gestionnaire à un événement.  Il s'agit du même opérateur que celui utilisé pour assigner un gestionnaire dans le modèle de gestion des événements de [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] ne prend pas en charge cet opérateur comme moyen permettant d'ajouter des gestionnaires d'événements.  Il requiert à la place l'une des deux techniques suivantes :  
  
-   Utilisez la méthode <xref:System.Windows.UIElement.AddHandler%2A>, associée à un opérateur `AddressOf`, pour référencer l'implémentation du gestionnaire d'événements.  
  
-   Utilisez le mot clé `Handles` dans le cadre de la définition du gestionnaire d'événements.  Cette technique n'est pas indiquée ici ; consultez [Gestion des événements Visual Basic et WPF](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 [!code-xml[RoutedEventAddRemoveHandler#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
>  L'ajout d'un gestionnaire d'événements dans la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] analysée initialement est beaucoup plus simple.  Dans l'élément objet où vous souhaitez ajouter le gestionnaire d'événements, ajoutez un attribut correspondant au nom de l'événement que vous souhaitez gérer.  Spécifiez ensuite la valeur de cet attribut comme nom de la méthode de gestionnaire d'événements que vous avez définie dans le fichier code\-behind de la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Pour plus d'informations, consultez [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) ou [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## Voir aussi  
 [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)