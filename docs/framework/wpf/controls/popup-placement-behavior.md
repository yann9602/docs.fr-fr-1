---
title: "Comportement de positionnement de Popup | Microsoft Docs"
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
  - "Popup"
  - "Contrôle Popup, placer"
  - "placer des menus contextuels"
  - "positionner des menus contextuels"
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Comportement de positionnement de Popup
A <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre distincte qui flotte au-dessus d’une application. Vous pouvez spécifier la position d’un <xref:System.Windows.Controls.Primitives.Popup> par rapport à un contrôle, la souris ou l’écran à l’aide de la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés.  Ces propriétés fonctionnent ensemble pour vous donner la souplesse pour spécifier la position de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  Le <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ContextMenu> classes également définir ces cinq propriétés et se comportent de la même façon.  
  
   
  
<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Positionnement Popup  
 Le placement d’un <xref:System.Windows.Controls.Primitives.Popup> peut être relatif à un <xref:System.Windows.UIElement> ou à tout l’écran.  L’exemple suivant crée quatre <xref:System.Windows.Controls.Primitives.Popup> les contrôles relatif à un <xref:System.Windows.UIElement>: dans ce cas, une image. Tous les <xref:System.Windows.Controls.Primitives.Popup> contrôles ont le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété la valeur `image1`, mais chaque <xref:System.Windows.Controls.Primitives.Popup> a une valeur différente pour la propriété de positionnement.  
  
 [!code-xml[PopupPositionSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 L’illustration suivante montre l’image et le <xref:System.Windows.Controls.Primitives.Popup> contrôles  
  
 ![Image avec quatre contrôles popup](../../../../docs/framework/wpf/controls/media/popupplacementintro.png "PopupPlacementIntro")  
Image avec quatre contrôles Popup  
  
 Cet exemple simple montre comment définir le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriétés, mais à l’aide de la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés, vous avez davantage de contrôle sur l’emplacement le <xref:System.Windows.Controls.Primitives.Popup> est positionné.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Définitions de termes : anatomie d’une fenêtre contextuelle  
 Les termes suivants sont utiles pour comprendre comment la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés sont liés entre eux et <xref:System.Windows.Controls.Primitives.Popup>:  
  
-   Objet cible  
  
-   Zone de la cible  
  
-   Origine de la cible  
  
-   Point d’alignement  
  
 Ces termes fournissent un moyen pratique pour faire référence aux différents aspects de la <xref:System.Windows.Controls.Primitives.Popup> et le contrôle auquel il est associé.  
  
### <a name="target-object"></a>Objet cible  
 Le *objet cible* est l’élément qui le <xref:System.Windows.Controls.Primitives.Popup> est associé. Si le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est définie, elle spécifie l’objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> n’est pas définie et la <xref:System.Windows.Controls.Primitives.Popup> a un parent, le parent est l’objet cible.  S’il existe aucune <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> valeur et aucun parent, il n’existe aucun objet de la cible et le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à l’écran.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>.  L’exemple ne définit pas la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété sur le <xref:System.Windows.Controls.Primitives.Popup>. La valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode?displayProperty=fullName>, le <xref:System.Windows.Controls.Primitives.Popup> apparaît sous le <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xml[PopupPositionSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à la <xref:System.Windows.Controls.Canvas>.  
  
 ![Contrôle Popup sans PlacementTarget](../../../../docs/framework/wpf/controls/media/popupplacementnoplacementtarget.png "PopupPlacementNoPlacementTarget")  
Popup sans PlacementTarget  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>, mais cette fois le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est défini sur `ellipse1`, de sorte que la fenêtre contextuelle apparaît sous le <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xml[PopupPositionSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à la <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Popup positionné par rapport à une ellipse](../../../../docs/framework/wpf/controls/media/popupplacementwithplacementtarget.png "PopupPlacementWithPlacementTarget")  
Popup avec PlacementTarget  
  
> [!NOTE]
>  Pour <xref:System.Windows.Controls.ToolTip>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>.  Pour <xref:System.Windows.Controls.ContextMenu>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>. Ces valeurs sont expliquées plus loin, dans « Comment les propriétés fonctionnent ensemble ».  
  
### <a name="target-area"></a>Zone de la cible  
 Le *cibler zone* est la zone de l’écran qui la <xref:System.Windows.Controls.Primitives.Popup> est relative. Dans les exemples précédents, le <xref:System.Windows.Controls.Primitives.Popup> est aligné sur les limites de l’objet cible, mais dans certains cas, le <xref:System.Windows.Controls.Primitives.Popup> est aligné sur d’autres limites, même si le <xref:System.Windows.Controls.Primitives.Popup> a un objet cible.  Si le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est définie, la zone de la cible est différente des limites de l’objet cible.  
  
 L’exemple suivant crée deux <xref:System.Windows.Controls.Canvas> d’objets, chacun d’eux contenant un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Primitives.Popup>.  Dans les deux cas, la cible de l’objet pour le <xref:System.Windows.Controls.Primitives.Popup> est la <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.Controls.Primitives.Popup> dans la première <xref:System.Windows.Controls.Canvas> a le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> défini, avec ses <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, et <xref:System.Windows.Rect.Height%2A> propriétés la valeur 50, 50, 50 et 100, respectivement. Le <xref:System.Windows.Controls.Primitives.Popup> dans la seconde <xref:System.Windows.Controls.Canvas> n’a pas la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> définie.  Par conséquent, la première <xref:System.Windows.Controls.Primitives.Popup> se trouve sous le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> et le second <xref:System.Windows.Controls.Primitives.Popup> se trouve sous le <xref:System.Windows.Controls.Canvas>. Chaque <xref:System.Windows.Controls.Canvas> contient également un <xref:System.Windows.Shapes.Rectangle> qui a les mêmes limites que le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pour la première <xref:System.Windows.Controls.Primitives.Popup>.  Notez que la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ne crée pas d’élément visible dans l’application, l’exemple crée un <xref:System.Windows.Shapes.Rectangle> pour représenter la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xml[PopupPositionSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Popup avec et sans PlacementRectangle](../../../../docs/framework/wpf/controls/media/popupplacementplacementrectangle.png "PopupPlacementPlacementRectangle")  
Popup avec et sans PlacementRectangle  
  
### <a name="target-origin-and-popup-alignment-point"></a>Origine de la cible et le Point d’alignement  
 Le *cible d’origine* et *alignement Popup* sont des points de référence de la zone cible et le menu contextuel, respectivement, qui sont utilisés pour le positionnement. Vous pouvez utiliser la <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés pour décaler la fenêtre contextuelle de la zone cible.  Le <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont relatives à l’origine de la cible et le point d’alignement. La valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété détermine où se trouvent le point d’alignement cible origine et la fenêtre contextuelle.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> et définit les <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 20 aux propriétés.  Le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode> (la valeur par défaut), donc l’origine cible est le coin inférieur gauche de la zone cible et le point d’alignement contextuel est le coin supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xml[PopupPositionSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Positionnement Popup avec point d’alignement original cible](../../../../docs/framework/wpf/controls/media/popupplacementtargetoriginalignmentpoint.PNG "PopupPlacementTargetOriginAlignmentPoint")  
Popup avec HorizontalOffset et VerticalOffset  
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Comment les propriétés opèrent ensemble  
 Les valeurs de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> nécessitent d’être considérées ensemble pour déterminer la zone de la cible, l’origine de la cible et son point d’alignement.  Par exemple, si la valeur de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>, il n’existe aucun objet de cible, le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré, et la zone cible correspond aux limites du pointeur de la souris. En revanche, si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>, le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou le parent détermine l’objet cible et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> détermine la zone cible.  
  
 Le tableau suivant décrit l’objet cible, zone de la cible, origine de la cible et son point d’alignement et indique si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sont utilisés pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur d’énumération.  
  
|PlacementMode|Objet cible|Zone de la cible|Origine de la cible|Point d’alignement|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|Le coin supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|Le coin supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin inférieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le centre de la zone cible.|Le centre de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin supérieur gauche de la zone cible.|Le coin supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de la souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|Le coin inférieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de la souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|Le coin supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin supérieur droit de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le coin supérieur gauche de la zone cible.|Le coin inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Les illustrations suivantes montrent le <xref:System.Windows.Controls.Primitives.Popup>, du point pour chaque zone de la cible, l’origine de la cible et alignement de la fenêtre contextuelle <xref:System.Windows.Controls.Primitives.PlacementMode> valeur. Dans chacune des figures, la zone de la cible est en jaune et le <xref:System.Windows.Controls.Primitives.Popup> est bleu.  
  
 ![Popup avec positionnement Absolute ou AbsolutePoint](../../../../docs/framework/wpf/controls/media/popupplacementabsolute.png "PopupPlacementAbsolute")  
Est de positionnement Absolute ou AbsolutePoint  
  
 ![Popup avec positionnement Bottom](../../../../docs/framework/wpf/controls/media/popupplacementbottom.png "PopupPlacementBottom")  
La sélection élective est bas  
  
 ![Popup avec positionnement Center](../../../../docs/framework/wpf/controls/media/popupplacementcenter.png "PopupPlacementCenter")  
La sélection élective est Center  
  
 ![Popup avec positionnement Left](../../../../docs/framework/wpf/controls/media/popupplacementleft.png "PopupPlacementLeft")  
La sélection élective est gauche  
  
 ![Popup avec positionnement Mouse](../../../../docs/framework/wpf/controls/media/popupplacementmouse.png "PopupPlacementMouse")  
Positionnement est la souris  
  
 ![Popup avec positionnement MousePoint](../../../../docs/framework/wpf/controls/media/popupplacementmousepoint.png "PopupPlacementMousePoint")  
Placement a la valeur MousePoint  
  
 ![Popup avec positionnement relative ou RelativePoint](../../../../docs/framework/wpf/controls/media/popupplacementrelative.png "PopupPlacementRelative")  
La sélection élective est Relative ou RelativePoint  
  
 ![Popup avec positionnement Right](../../../../docs/framework/wpf/controls/media/popupplacementright.png "PopupPlacementRight")  
La sélection élective est droite  
  
 ![Popup avec positionnement Top](../../../../docs/framework/wpf/controls/media/popupplacementtop.png "PopupPlacementTop")  
La sélection élective est haut  
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Lorsque la fenêtre contextuelle rencontre le bord de l’écran  
 Pour des raisons de sécurité, un <xref:System.Windows.Controls.Primitives.Popup> ne peut pas être masqué par le bord de l’écran. Une des trois actions suivantes se produit lorsque le <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord de l’écran :  
  
-   La fenêtre contextuelle aligne le long du bord de l’écran qui la <xref:System.Windows.Controls.Primitives.Popup>.  
  
-   La fenêtre contextuelle utilise un point d’alignement différents.  
  
-   La fenêtre contextuelle utilise un point d’alignement origine et popup cible différent.  
  
 Ces options sont décrites plus loin dans cette section.  
  
 Le comportement de la <xref:System.Windows.Controls.Primitives.Popup> lorsqu’il rencontre un bord de l’écran dépend de la valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété et qui écran de bord de la fenêtre contextuelle rencontre. Le tableau suivant récapitule le comportement lors de la <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord de l’écran pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur.  
  
|PlacementMode|Bord supérieur|Bord inférieur|Bord gauche|Bord droit|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Aligne le bord inférieur.|Aligne le bord gauche.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Le point d’alignement se transforme en bas à gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord gauche.|Le point d’alignement se transforme en haut à droite de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement se transforme en bas à gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord gauche.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Aligne le bord inférieur.|Aligne le bord gauche.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Aligne le bord inférieur.|L’origine de la cible devient l’angle supérieur droit de la zone cible et le point d’alignement passe à l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement se transforme en bas à gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord gauche.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Le point d’alignement se transforme en bas à gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord gauche.|L’alignement du menu contextuel point devient le coin supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Aligne le bord inférieur.|Aligne le bord gauche.|Aligne le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Le point d’alignement se transforme en bas à gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Aligne le bord gauche.|L’alignement du menu contextuel point devient le coin supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|Aligne sur le bord supérieur.|Aligne le bord inférieur.|Aligne le bord gauche.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement se transforme en haut à droite de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode>|L’origine de la cible devient l’angle inférieur gauche de la zone cible et le point d’alignement passe à l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>. En effet, il s’agit du même que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>.|Aligne le bord inférieur.|Aligne le bord gauche.|Aligne le bord droit.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alignement sur le bord de l’écran  
 A <xref:System.Windows.Controls.Primitives.Popup> peut s’aligner sur le bord de l’écran en se repositionnant donc l’ensemble <xref:System.Windows.Controls.Primitives.Popup> est visible à l’écran.  Lorsque cela se produit, la distance entre le point d’alignement origine et popup cible peut-être différer des valeurs de <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Lors de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>, <xref:System.Windows.Controls.Primitives.PlacementMode>, ou <xref:System.Windows.Controls.Primitives.PlacementMode>, le <xref:System.Windows.Controls.Primitives.Popup> s’aligne sur chaque bord de l’écran.  Par exemple, supposons qu’un <xref:System.Windows.Controls.Primitives.Popup> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la valeur <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> défini à 100.  Si le bord inférieur de l’écran masque tout ou partie de la <xref:System.Windows.Controls.Primitives.Popup>, le <xref:System.Windows.Controls.Primitives.Popup> se repositionne le long du bord inférieur de l’écran et la distance verticale entre l’origine de la cible et la fenêtre contextuelle, le point d’alignement est inférieur à 100. L’illustration suivante montre cela.  
  
 ![Popup aligné sur le bord de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementrelativescreenedge.png "PopupPlacementRelativeScreenEdge")  
Popup aligné sur le bord de l’écran  
  
### <a name="changing-the-popup-alignment-point"></a>Modifier le Point d’alignement  
 Si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>, <xref:System.Windows.Controls.Primitives.PlacementMode>, ou <xref:System.Windows.Controls.Primitives.PlacementMode>, le point d’alignement change lorsque la fenêtre contextuelle rencontre du bord inférieur ou droit de l’écran.  
  
 L’illustration suivante montre que lorsque le bord d’écran inférieur masque tout ou partie de la <xref:System.Windows.Controls.Primitives.Popup>, le point d’alignement contextuel est le coin inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointscreenedge.png "PopupPlacementRelativePointScreenEdge")  
Fenêtre contextuelle rencontre le bord inférieur de l’écran et modifie le point d’alignement  
  
 L’illustration suivante montre que lorsque la <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord droit de l’écran, le point d’alignement contextuel est le coin supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouvel alignement Popup en raison du bord de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementrelativepointrightscreenedge.png "PopupPlacementRelativePointRightScreenEdge")  
Fenêtre contextuelle rencontre le bord droit de l’écran et modifie le point d’alignement  
  
 Si le <xref:System.Windows.Controls.Primitives.Popup> rencontre les bords inférieur et droit de l’écran, le point d’alignement contextuel est le coin inférieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Modification de l’origine de la cible et le Point d’alignement  
 Lors de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode>, <xref:System.Windows.Controls.Primitives.PlacementMode>, <xref:System.Windows.Controls.Primitives.PlacementMode>, <xref:System.Windows.Controls.Primitives.PlacementMode>, ou <xref:System.Windows.Controls.Primitives.PlacementMode>, l’alignement d’origine et la fenêtre contextuelle cible du point de modification si un certain bord de l’écran est rencontré.  Le bord de l’écran qui provoque la modification de position varie selon le <xref:System.Windows.Controls.Primitives.PlacementMode> valeur.  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est le coin supérieur gauche de la zone cible et le point d’alignement contextuel est le coin inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementbottomscreenedge.png "PopupPlacementBottomScreenEdge")  
Placement a la valeur Bottom et la fenêtre contextuelle rencontre le bord inférieur de l’écran  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord gauche de l’écran, l’origine de la cible est le coin supérieur droit de la zone cible et le point d’alignement est l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord gauche de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementleftscreenedge.png "PopupPlacementLeftScreenEdge")  
Placement a gauche et la fenêtre contextuelle rencontre le bord gauche de l’écran  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord droit de l’écran, l’origine de la cible est le coin supérieur gauche de la zone cible et le point d’alignement contextuel est le coin supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord droit de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementrightscreenedge.png "PopupPlacementRightScreenEdge")  
Placement a droite et la fenêtre contextuelle rencontre le bord droit de l’écran  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord supérieur de l’écran, l’origine de la cible est le coin inférieur gauche de la zone cible et le point d’alignement est l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord supérieur de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementtopscreenedge.png "PopupPlacementTopScreenEdge")  
La sélection élective est Top et la fenêtre contextuelle rencontre le bord supérieur de l’écran  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est le coin supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement contextuel est le coin inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nouveau point d’alignement en raison de la souris vers le bord de l’écran](../../../../docs/framework/wpf/controls/media/popupplacementmousescreenedge.png "PopupPlacementMouseScreenEdge")  
Placement a la souris et la fenêtre contextuelle rencontre le bord inférieur de l’écran  
  
### <a name="customizing-popup-placement"></a>Personnalisation de positionnement de Popup  
 Vous pouvez personnaliser la cible origine et menu contextuel point d’alignement en définissant le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété <xref:System.Windows.Controls.Primitives.PlacementMode>. Définissez ensuite un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué qui retourne un ensemble de points de positionnement possibles et les axes principaux (par ordre de préférence) pour le <xref:System.Windows.Controls.Primitives.Popup>. Le point qui montre la plus grande partie de la <xref:System.Windows.Controls.Primitives.Popup> est sélectionnée.  La position de la <xref:System.Windows.Controls.Primitives.Popup> est ajustée automatiquement si le <xref:System.Windows.Controls.Primitives.Popup> est caché par le bord de l’écran. Pour obtenir un exemple, consultez [spécifier une Position de menu contextuel personnalisé](../../../../docs/framework/wpf/controls/how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Positionnement de Popup, exemple](http://go.microsoft.com/fwlink/?LinkID=160032)