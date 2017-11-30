---
title: "Comment : animer dans un style"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10cd243c633e7a7e458d2026fc5e3d91d2996427
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-in-a-style"></a>Comment : animer dans un style
Cet exemple montre comment animer des propriétés dans un style. Lors de l’animation dans un style, seul l’élément framework pour laquelle le style est défini peut être directement ciblé. Pour cibler un objet freezable, vous devez « point vers le bas » à partir d’une propriété de l’élément style.  
  
 Dans l’exemple suivant, plusieurs animations sont définies dans un style et appliquées à un <xref:System.Windows.Controls.Button>. Lorsque l’utilisateur déplace la souris sur le bouton, il passe d’opaque à partiellement transparent et vice à nouveau, à plusieurs reprises. Lorsque l’utilisateur déplace la souris hors du bouton, il est complètement opaque. Lorsque le bouton est activé, sa couleur d’arrière-plan passe d’orange à blanc et vice versa. Étant donné que la <xref:System.Windows.Media.SolidColorBrush> utilisé pour peindre le bouton ne peut pas être ciblé directement, il est accessible par pointillage au bas à partir du bouton <xref:System.Windows.Controls.Control.Background%2A> propriété.  
  
## <a name="example"></a>Exemple  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Notez que lors de l’animation dans un style, il est possible de cibler des objets qui n’existent pas. Par exemple, supposons que votre style utilise un <xref:System.Windows.Media.SolidColorBrush> pour définir la propriété d’arrière-plan d’un bouton, mais à un moment donné le style est remplacé et l’arrière-plan du bouton est défini avec un <xref:System.Windows.Media.LinearGradientBrush>.  Lors de la tentative animer la <xref:System.Windows.Media.SolidColorBrush> ne lève pas d’exception ; l’animation échouera en mode silencieux.  
  
 Pour plus d’informations sur le plan conceptuel de la syntaxe de ciblage, consultez le [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Pour plus d’informations sur l’animation, consultez le [vue d’ensemble de l’Animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Pour plus d’informations sur les styles, consultez le [styles et modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).
