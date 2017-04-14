---
title: "Comment&#160;: rendre un UIElement transparent ou semi-transparent | Microsoft Docs"
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
  - "opacité, d'UIElements"
  - "transparence d'UIElements"
  - "UIElements, opacité"
  - "UIElements, transparence"
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# Comment&#160;: rendre un UIElement transparent ou semi-transparent
Cet exemple montre comment rendre un <xref:System.Windows.UIElement> transparent ou semi\-transparent.  Pour rendre un élément transparent ou semi\-transparent, vous devez définir sa propriété <xref:System.Windows.UIElement.Opacity%2A>.  Une valeur de `0.0` rend l'élément complètement transparent, tandis que la valeur `1.0` le rend complètement opaque.  Une valeur de `0.5` rend l'élément à moitié opaque, etc.  Par défaut, l'<xref:System.Windows.UIElement.Opacity%2A> d'un élément est définie à la valeur `1.0`.  
  
## Exemple  
 L'exemple suivant affecte la valeur `0.25` à l'<xref:System.Windows.UIElement.Opacity%2A> d'un bouton, de sorte que celui\-ci et son contenu \(dans ce cas, le texte du bouton\) sont opaques à 25 %.  
  
 [!code-xml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Si le contenu d'un élément a ses propres paramètres <xref:System.Windows.UIElement.Opacity%2A>, ces valeurs sont multipliées en fonction de l'<xref:System.Windows.UIElement.Opacity%2A> des éléments contenants.  
  
 L'exemple suivant affecte la valeur `0.25` à l'<xref:System.Windows.UIElement.Opacity%2A> d'un bouton et la valeur `0.5` à l'<xref:System.Windows.UIElement.Opacity%2A> d'un contrôle <xref:System.Windows.Controls.Image> contenu dans le bouton.  L'image ainsi obtenue est opaque à 12,5 % : 0,25 \* 0,5 \= 0,125.  
  
 [!code-xml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Une autre manière de contrôler l'opacité d'un élément consiste à définir l'opacité du <xref:System.Windows.Media.Brush> qui peint l'élément.  Cette approche vous permet de modifier de manière sélective l'opacité de certaines parties d'un élément et présente des avantages en termes de performances par rapport à l'utilisation de la propriété <xref:System.Windows.UIElement.Opacity%2A> de l'élément.  L'exemple suivant affecte la valeur `0.25` à l'<xref:System.Windows.Media.Brush.Opacity%2A> d'un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre l'<xref:System.Windows.Controls.Control.Background%2A> du bouton.  L'arrière\-plan du pinceau est opaque à 25 %, tandis que son contenu \(le texte du bouton\) reste opaque à 100 %.  
  
 [!code-xml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Vous pouvez contrôler également l'opacité de couleurs individuelles d'un pinceau.  Pour plus d'informations sur les couleurs et les pinceaux, consultez [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  Pour un exemple d'animation de l'opacité d'un élément, consultez [Animer l'opacité d'un élément ou d'un pinceau](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).