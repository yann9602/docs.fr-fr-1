---
title: "Vue d&#39;ensemble des effets bitmap | Microsoft Docs"
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
  - "effets bitmap"
ms.assetid: 23cb338e-4b59-4b52-b294-96431f9c9568
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 31
---
# Vue d&#39;ensemble des effets bitmap
Les effets bitmap permettent aux concepteurs et développeurs d'appliquer des effets visuels au contenu [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] rendu.  Par exemple, les effets bitmap vous permettent d'appliquer facilement un effet <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> ou un effet flou à une image ou un bouton.  
  
> [!IMPORTANT]
>  Dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] et les versions ultérieures, la classe <xref:System.Windows.Media.Effects.BitmapEffect> est obsolète.  Si vous essayez d'utiliser la classe <xref:System.Windows.Media.Effects.BitmapEffect>, vous obtiendrez une exception obsolète.  L'alternative non obsolète à la classe<xref:System.Windows.Media.Effects.BitmapEffect> est la classe <xref:System.Windows.Media.Effects.Effect>.  Dans la plupart des cas, la classe <xref:System.Windows.Media.Effects.Effect> est nettement plus rapide.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="wpf_effects"></a>   
## Effets bitmap WPF  
 Les effets bitmap \(objet <xref:System.Windows.Media.Effects.BitmapEffect>\) sont des opérations de traitement de pixels simples.  Un effet bitmap prend un <xref:System.Windows.Media.Imaging.BitmapSource> comme entrée et produit un nouveau <xref:System.Windows.Media.Imaging.BitmapSource> après avoir appliqué l'effet, tel qu'un flou ou une ombre portée.  Chaque effet bitmap expose des propriétés qui peuvent contrôler les propriétés de filtrage, telles que <xref:System.Windows.Media.Effects.BlurBitmapEffect.Radius%2A> de <xref:System.Windows.Media.Effects.BlurBitmapEffect>.  
  
 Dans certains cas, dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les effets peuvent être définis comme propriétés sur des objets <xref:System.Windows.Media.Visual> actifs, tels qu'un <xref:System.Windows.Controls.Button> ou <xref:System.Windows.Controls.TextBox>.  Le traitement de pixels est appliqué et restitué au moment de l'exécution.  Dans ce cas, au moment du rendu, un <xref:System.Windows.Media.Visual> est converti automatiquement à son <xref:System.Windows.Media.Imaging.BitmapSource> équivalent et acheminé comme entrée au <xref:System.Windows.Media.Effects.BitmapEffect>.  La sortie remplace le comportement de rendu par défaut de l'objet <xref:System.Windows.Media.Visual>.  C'est pourquoi les objets <xref:System.Windows.Media.Effects.BitmapEffect> forcent le rendu des visuels uniquement dans les logiciels, c.\-à\-d.  sans aucune accélération matérielle sur les visuels lorsque des effets sont appliqués.  
  
-   <xref:System.Windows.Media.Effects.BlurBitmapEffect> simule un objet qui s'affiche hors du focus.  
  
-   <xref:System.Windows.Media.Effects.OuterGlowBitmapEffect> crée un halo de couleur autour du périmètre d'un objet.  
  
-   <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> crée une ombre derrière un objet.  
  
-   <xref:System.Windows.Media.Effects.BevelBitmapEffect> crée un biseau qui déclenche la surface d'une image d'après une courbe spécifiée.  
  
-   <xref:System.Windows.Media.Effects.EmbossBitmapEffect> crée un placage de relief pour un <xref:System.Windows.Media.Visual> afin de donner une impression de profondeur et de texture comme avec une source de lumière artificielle.  
  
> [!NOTE]
>  Les effets bitmap [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont restitués en mode logiciel.  Tout objet qui applique un effet est également restitué dans le logiciel.  Les performances sont les plus dégradées lors de l'utilisation d'effets bitmap sur de grands visuels ou de l'animation de propriétés d'un effet bitmap.  Il ne s'agit pas de vous dire de ne pas utiliser du tout les effets bitmap de cette façon, mais vous devez être prudent et effectuer des tests approfondis pour garantir que vos utilisateurs obtiennent l'expérience que vous attendez.  
  
> [!NOTE]
>  Les effets bitmap de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ne prennent pas en charge l'exécution de confiance partielle.  Une application doit avoir des autorisations de confiance totale pour utiliser des effets bitmap.  
  
<a name="applyeffects"></a>   
## Comment appliquer un effet  
 <xref:System.Windows.Media.Effects.BitmapEffect> est une propriété sur <xref:System.Windows.Media.Visual>.  Par conséquent, l'application d'effets aux visuels, tels qu'un <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Image>, <xref:System.Windows.Media.DrawingVisual>ou <xref:System.Windows.UIElement>, est aussi simple que la définition d'une propriété.  <xref:System.Windows.UIElement.BitmapEffect%2A> peut avoir pour valeur un objet <xref:System.Windows.Media.Effects.BitmapEffect> unique ou plusieurs effets peuvent être chaînés à l'aide de l'objet <xref:System.Windows.Media.Effects.BitmapEffectGroup>.  
  
 L'exemple suivant montre comment appliquer un <xref:System.Windows.Media.Effects.BitmapEffect> en [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
 [!code-xml[EffectsGallery_snip#BlurSimpleExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blursimpleexample.xaml#blursimpleexampleinline)]  
  
 L'exemple suivant montre comment appliquer un <xref:System.Windows.Media.Effects.BitmapEffect> dans le code.  
  
 [!code-csharp[EffectsGallery_snip#CodeBehindBlurCodeBehindExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/EffectsGallery_snip/CSharp/blurcodebehindexample.xaml.cs#codebehindblurcodebehindexampleinline)]  
  
> [!NOTE]
>  Lorsqu'un <xref:System.Windows.Media.Effects.BitmapEffect> est appliqué à un conteneur de disposition, tel que <xref:System.Windows.Controls.DockPanel> ou <xref:System.Windows.Controls.Canvas>, l'effet est appliqué à l'arborescence visuelle de l'élément ou du visuel, y compris tous ses éléments enfants.  
  
<a name="customeffects"></a>   
## Création d'effets personnalisés  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] fournit également des interfaces non managées pour créer des effets personnalisés qui peuvent être utilisés dans les applications [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] managées.  Pour obtenir une documentation de référence supplémentaire sur la création d'effets bitmap personnalisés, consultez la documentation [Effet de bitmap WPF non managé](_wibe_lh).  
  
## Voir aussi  
 <xref:System.Windows.Media.Effects.BitmapEffectGroup>   
 <xref:System.Windows.Media.Effects.BitmapEffectInput>   
 <xref:System.Windows.Media.Effects.BitmapEffectCollection>   
 [Unmanaged WPF Bitmap Effect](_wibe_lh)   
 [Vue d'ensemble de la création d'images](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)   
 [Sécurité](../../../../docs/framework/wpf/security-wpf.md)   
 [Vue d'ensemble du rendu graphique de WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)