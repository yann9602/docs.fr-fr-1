---
title: "Vue d&#39;ensemble de Popup | Microsoft Docs"
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
  - "contrôles, Popup"
  - "Popup (contrôle) (WPF), à propos du contrôle Popup"
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Vue d&#39;ensemble de Popup
Le contrôle <xref:System.Windows.Controls.Primitives.Popup> permet d'afficher le contenu dans une fenêtre séparée qui flotte au\-dessus de la fenêtre d'application actuelle par rapport à un élément désigné ou une coordonnée d'écran.  Cette rubrique présente le contrôle <xref:System.Windows.Controls.Primitives.Popup> et fournit des informations quant à son utilisation.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="What_Is_a_Popup_"></a>   
## Qu'est\-ce qu'un Popup ?  
 Un contrôle <xref:System.Windows.Controls.Primitives.Popup> affiche un contenu dans une fenêtre séparée par rapport à un élément ou un point à l'écran.  Lorsque le contrôle <xref:System.Windows.Controls.Primitives.Popup> est visible, la propriété <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> a la valeur `true`.  
  
> [!NOTE]
>  Un contrôle <xref:System.Windows.Controls.Primitives.Popup> ne s'ouvre pas automatiquement quand le pointeur de la souris se déplace au\-dessus de son objet parent.  Si vous voulez que le contrôle <xref:System.Windows.Controls.Primitives.Popup> s'ouvre automatiquement, utilisez la classe <xref:System.Windows.Controls.ToolTip> ou <xref:System.Windows.Controls.ToolTipService>.  Pour plus d'informations, consultez [Vue d'ensemble de l'info\-bulle](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## Création d'un Popup  
 L'exemple suivant montre comment définir un contrôle <xref:System.Windows.Controls.Primitives.Popup>, qui est un élément enfant d'un contrôle <xref:System.Windows.Controls.Button>.  Dans la mesure où un contrôle <xref:System.Windows.Controls.Button> peut avoir un seul élément enfant, cet exemple place le texte pour les contrôles <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.Primitives.Popup> dans un <xref:System.Windows.Controls.StackPanel>.  Le contenu du contrôle <xref:System.Windows.Controls.Primitives.Popup> apparaît dans un contrôle <xref:System.Windows.Controls.TextBlock>, qui affiche son texte dans une fenêtre séparée qui flotte au\-dessus de la fenêtre d'application près du contrôle associé <xref:System.Windows.Controls.Button>l.  
  
 [!code-xml[PopupSimple#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xml[PopupSimple#CreatePopupCodeXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## Contrôles qui implémentent un Popup  
 Vous pouvez générer des contrôles <xref:System.Windows.Controls.Primitives.Popup> dans d'autres contrôles.  Les contrôles suivants implémentent le contrôle <xref:System.Windows.Controls.Primitives.Popup> pour des utilisations spécifiques :  
  
-   <xref:System.Windows.Controls.ToolTip>.  Si vous souhaitez créer une info\-bulle pour un élément, utilisez les classes <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ToolTipService>.  Pour plus d'informations, consultez [Vue d'ensemble de l'info\-bulle](../../../../docs/framework/wpf/controls/tooltip-overview.md).  
  
-   <xref:System.Windows.Controls.ContextMenu>.  Si vous souhaitez créer un menu contextuel pour un élément, utilisez le contrôle <xref:System.Windows.Controls.ContextMenu>.  Pour plus d'informations, consultez [Vue d'ensemble de ContextMenu](../../../../docs/framework/wpf/controls/contextmenu-overview.md).  
  
-   <xref:System.Windows.Controls.ComboBox>.  Si vous souhaitez créer un contrôle de sélection qui possède une zone de liste déroulante pouvant être affichée ou masquée, utilisez le contrôle <xref:System.Windows.Controls.ComboBox>.  
  
-   <xref:System.Windows.Controls.Expander>.  Si vous souhaitez créer un contrôle qui affiche un en\-tête avec une zone réductible qui affiche du contenu, utilisez le contrôle <xref:System.Windows.Controls.Expander>.  Pour plus d'informations, consultez [Vue d'ensemble de l'expanseur](../../../../docs/framework/wpf/controls/expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## Comportement et apparence de Popup  
 Le contrôle <xref:System.Windows.Controls.Primitives.Popup> fournit des fonctionnalités qui vous permettent de personnaliser son comportement et son apparence.  Par exemple, vous pouvez définir un comportement d'ouverture ou de fermeture, une animation, l'opacité et les effets bitmap, ainsi que la taille et la position du <xref:System.Windows.Controls.Primitives.Popup>.  
  
<a name="OpenandCloseBehavior"></a>   
### Comportement d'ouverture et de fermeture  
 Un contrôle <xref:System.Windows.Controls.Primitives.Popup> affiche son contenu quand la propriété <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> a la valeur `true`.  Par défaut, le contrôle <xref:System.Windows.Controls.Primitives.Popup> reste ouvert jusqu'à ce que la propriété <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> ait la valeur `false`.  Vous pouvez, cependant, modifier ce comportement par défaut en attribuant à la propriété <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> la valeur `false`..  Lorsque vous affectez à cette propriété la valeur `false`, la fenêtre de contenu de <xref:System.Windows.Controls.Primitives.Popup> a la capture de souris.  Le contrôle <xref:System.Windows.Controls.Primitives.Popup> perd la capture de la souris et la fenêtre se ferme quand un événement souris se produit en dehors de la fenêtre <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Les événements <xref:System.Windows.Controls.Primitives.Popup.Opened> et <xref:System.Windows.Controls.Primitives.Popup.Closed> sont générés quand la fenêtre de contenu de <xref:System.Windows.Controls.Primitives.Popup> est ouvert ou fermée.  
  
<a name="Animation"></a>   
### Animation  
 Le contrôle <xref:System.Windows.Controls.Primitives.Popup> assure la prise en charge intégrée des animations qui sont généralement associées à des comportements comme un effet fondu et un effet inséré.  Vous pouvez activer ces animations en affectant à la propriété <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> une valeur d'énumération <xref:System.Windows.Controls.Primitives.PopupAnimation>.  Pour que les animations <xref:System.Windows.Controls.Primitives.Popup> fonctionnent correctement, vous devez attribuer à la propriété <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> la valeur `true`.  
  
 Vous pouvez également appliquer des animations comme <xref:System.Windows.Media.Animation.Storyboard> au contrôle <xref:System.Windows.Controls.Primitives.Popup>.  
  
<a name="OpacityandBitmapEffects"></a>   
### Opacité et effets bitmap  
 La définition de la propriété <xref:System.Windows.UIElement.Opacity%2A> n'a aucun effet sur le contenu du contrôle <xref:System.Windows.Controls.Primitives.Popup>.  Par défaut, la fenêtre de contenu <xref:System.Windows.Controls.Primitives.Popup> est opaque.  Pour créer un transparent <xref:System.Windows.Controls.Primitives.Popup>, affectez à la propriété <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> la valeur `true`.  
  
 Le contenu d'un contrôle <xref:System.Windows.Controls.Primitives.Popup> n'hérite pas les effets bitmap, comme <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>, que vous définissez directement sur le contrôle <xref:System.Windows.Controls.Primitives.Popup> ou tout autre élément dans la fenêtre parent.  Pour que les effets bitmap apparaissent dans le contenu d'un <xref:System.Windows.Controls.Primitives.Popup>, vous devez définir ces effets directement dans son contenu.  Par exemple, si l'enfant d'un <xref:System.Windows.Controls.Primitives.Popup> est un <xref:System.Windows.Controls.StackPanel>, définissez l'effet bitmap sur <xref:System.Windows.Controls.StackPanel>.  
  
<a name="PopupSize"></a>   
### Taille du Popup  
 Par défaut, la taille d'un contrôle <xref:System.Windows.Controls.Primitives.Popup> est automatiquement ajustée à la taille de celui\-ci.  Lorsque l'ajustement automatique de la taille se produit, certains effets bitmap peuvent être masqués car la taille par défaut de la zone d'écran qui est définie pour le contenu de <xref:System.Windows.Controls.Primitives.Popup> ne fournit pas un espace suffisant pour l'affichage des effets bitmap.  
  
 Le contenu du contrôle <xref:System.Windows.Controls.Primitives.Popup> peut être obscurci lorsque vous définissez <xref:System.Windows.UIElement.RenderTransform%2A> sur le contenu.  Dans ce scénario, une partie du contenu peut être masquée si le contenu du <xref:System.Windows.Controls.Primitives.Popup> transformé s'étend au\-delà de la zone du <xref:System.Windows.Controls.Primitives.Popup> d'origine.  Si un effet bitmap ou une transformation requiert de plus d'espace, vous pouvez définir une marge autour du contenu de <xref:System.Windows.Controls.Primitives.Popup> afin de fournir une plus grande zone pour le contrôle.  
  
<a name="DefiningPopupPosition"></a>   
## Définition de la position d'un Popup  
 Vous pouvez positionner un Popup en définissant les propriétés <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty>.  Pour plus d'informations, consultez [Comportement de positionnement de Popup](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  Lorsque <xref:System.Windows.Controls.Primitives.Popup> est affiché à l'écran, il ne se repositionne pas si son parent est repositionné.  
  
<a name="CustomizingPopupPlacement"></a>   
### Personnalisation du positionnement de Popup  
 Vous pouvez personnaliser le placement d'un contrôle <xref:System.Windows.Controls.Primitives.Popup> en spécifiant un jeu de coordonnées qui sont relatives à la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> où vous voulez que le <xref:System.Windows.Controls.Primitives.Popup> apparaisse.  
  
 Pour personnaliser l'emplacement, attribuez à la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la valeur <xref:System.Windows.Controls.Primitives.PlacementMode>.  Définissez ensuite un délégué <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> qui retourne un ensemble de points de positionnement et d'axes primaires possibles \(dans l'ordre de préférence\) pour <xref:System.Windows.Controls.Primitives.Popup>.  Le point qui montre la plus grande partie du <xref:System.Windows.Controls.Primitives.Popup> est automatiquement sélectionné.  Pour obtenir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## Popup et arborescence d'éléments visuels  
 Un contrôle <xref:System.Windows.Controls.Primitives.Popup> ne doit pas nécessairement avoir sa propre [arborescence d'éléments visuels](GTMT) ; il retourne plutôt une taille 0 \(zéro\) quand la méthode <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> pour <xref:System.Windows.Controls.Primitives.Popup> est appelée.  Cependant, quand vous attribuez à la propriété <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> du <xref:System.Windows.Controls.Primitives.Popup> la valeur `true`, une nouvelle fenêtre avec  sa propre arborescence d'éléments visuels est créée.  La nouvelle fenêtre contient le contenu de <xref:System.Windows.Controls.Primitives.Popup.Child%2A> du <xref:System.Windows.Controls.Primitives.Popup>.  La largeur et la hauteur ne peuvent pas dépasser 75 % de la largeur ou de la hauteur de l'écran.  
  
 Le contrôle <xref:System.Windows.Controls.Primitives.Popup> conserve une référence au contenu du <xref:System.Windows.Controls.Primitives.Popup.Child%2A> en tant qu'enfant logique.  Quand la nouvelle fenêtre est créée, le contenu du <xref:System.Windows.Controls.Primitives.Popup> devient un enfant visuel de la fenêtre et reste l'enfant logique de <xref:System.Windows.Controls.Primitives.Popup>.  En revanche, <xref:System.Windows.Controls.Primitives.Popup> reste le parent logique du contenu du <xref:System.Windows.Controls.Primitives.Popup.Child%2A>.  
  
## Voir aussi  
 <xref:System.Windows.Controls.Primitives.Popup>   
 <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>   
 <xref:System.Windows.Controls.Primitives.PlacementMode>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>   
 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>   
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)