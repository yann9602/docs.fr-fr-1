---
title: "Comment&#160;: animer l&#39;opacit&#233; d&#39;un &#233;l&#233;ment ou d&#39;un pinceau | Microsoft Docs"
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
  - "animation, Opacity (propriété)"
  - "opacité, animer"
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Comment&#160;: animer l&#39;opacit&#233; d&#39;un &#233;l&#233;ment ou d&#39;un pinceau
Pour faire apparaître et disparaître un élément d'infrastructure en fondu dans une vue, vous pouvez animer sa propriété <xref:System.Windows.UIElement.Opacity%2A> ou la propriété <xref:System.Windows.Media.Brush.Opacity%2A> de <xref:System.Windows.Media.Brush> \(ou des pinceaux\) servant à le peindre.  L'animation de l'opacité de l'élément le fait apparaître et disparaître en fondu dans la vue, ainsi que ses enfants ; toutefois, l'animation du pinceau servant à le peindre vous permet de sélectionner plus précisément la partie à faire apparaître ou disparaître en fondu.  Par exemple, vous pouvez animer l'opacité d'un pinceau utilisé pour peindre l'arrière\-plan d'un bouton.  Cela entraînera l'apparition et la disparition en fondu de l'arrière\-plan du bouton dans la vue, tout en laissant son texte complètement opaque.  
  
> [!NOTE]
>  L'animation du <xref:System.Windows.Media.Brush.Opacity%2A> d'un <xref:System.Windows.Media.Brush> offre des avantages en termes de performances par rapport à l'animation de la propriété <xref:System.Windows.UIElement.Opacity%2A> d'un élément.  
  
 Dans l'exemple suivant, deux boutons sont animés de sorte à apparaître et disparaître en fondu dans la vue.  L'opacité du premier <xref:System.Windows.Controls.Button> est animée de `1.0` à `0.0` sur un <xref:System.Windows.Media.Animation.Timeline.Duration%2A> de cinq secondes.  Le deuxième bouton est également animé, mais l'opacité de SolidColorBrush utilisé pour peindre son <xref:System.Windows.Controls.Control.Background%2A> est animée plutôt que l'opacité du bouton entier.  Lors de l'exécution de l'exemple, le premier bouton apparaît et disparaît complètement en fondu dans la vue, alors que seul l'arrière\-plan du deuxième bouton apparaît et disparaît en fondu dans la vue.  Son texte et sa bordure restent complètement opaques.  
  
## Exemple  
 [!code-xml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 Le code a été omis de cet exemple.  L'exemple entier indique également comment animer l'opacité d'un <xref:System.Windows.Media.Color> dans un <xref:System.Windows.Media.LinearGradientBrush>.  Pour obtenir l'exemple complet, consultez [Animation de l'opacité d'un élément, exemple](http://go.microsoft.com/fwlink/?LinkID=159968).