---
title: "Comment : rendre un UIElement transparent ou semi-transparent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec35ae2e064acf78d1165f64ce8c9e34b153299d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>Comment : rendre un UIElement transparent ou semi-transparent
Cet exemple montre comment rendre un <xref:System.Windows.UIElement> transparent ou semi-transparent. Pour rendre un élément transparent ou semi-transparent, vous définissez son <xref:System.Windows.UIElement.Opacity%2A> propriété. La valeur `0.0` rend l’élément complètement transparent, alors que la valeur `1.0` rend l’élément complètement opaque. La valeur `0.5` rend les 50 % de l’élément opaque et ainsi de suite. D’un élément <xref:System.Windows.UIElement.Opacity%2A> a la valeur `1.0` par défaut.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant définit la <xref:System.Windows.UIElement.Opacity%2A> d’un bouton `0.25`, sorte que celui-ci et son contenu (dans ce cas, le texte du bouton) sont opaques à 25 %.  
  
 [!code-xaml[brushsamples_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 Si le contenu d’un élément ont leurs propres <xref:System.Windows.UIElement.Opacity%2A> paramètres, ces valeurs sont multipliées par les éléments contenant <xref:System.Windows.UIElement.Opacity%2A>.  
  
 L’exemple suivant définit un bouton <xref:System.Windows.UIElement.Opacity%2A> à `0.25`et le <xref:System.Windows.UIElement.Opacity%2A> d’un <xref:System.Windows.Controls.Image> contrôle contenu dans le bouton pour `0.5`. Par conséquent, l’image apparaît 12,5 % opaque : 0,25 * 0,5 = 0,125.  
  
 [!code-xaml[brushsamples_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 Une autre façon de contrôler l’opacité d’un élément consiste à définir l’opacité de la <xref:System.Windows.Media.Brush> qui peint l’élément. Cette approche vous permet de modifier de manière sélective l’opacité de certaines parties d’un élément et offre des avantages de performances principal à l’aide de l’élément <xref:System.Windows.UIElement.Opacity%2A> propriété. L’exemple suivant définit la <xref:System.Windows.Media.Brush.Opacity%2A> d’un <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre du bouton <xref:System.Windows.Controls.Control.Background%2A> a la valeur `0.25`. Par conséquent, l’arrière-plan du pinceau est opaque à 25 %, mais son contenu (le texte du bouton) reste opaque à 100 %.  
  
 [!code-xaml[brushsamples_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 Vous pouvez également contrôler l’opacité des couleurs individuelles au sein d’un pinceau. Pour plus d’informations sur les couleurs et les pinceaux, consultez [peinture avec des couleurs unies et vue d’ensemble des dégradés](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md). Pour obtenir un exemple montrant comment animer l’opacité d’un élément, consultez [animer l’opacité d’un élément ou un pinceau](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md).
