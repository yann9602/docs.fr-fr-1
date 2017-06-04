---
title: "Comment&#160;: personnaliser les graduations sur un curseur | Microsoft Docs"
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
  - "TickBar"
  - "Contrôle Slider, créer avec un TickBar"
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# Comment&#160;: personnaliser les graduations sur un curseur
Cet exemple montre comment créer un <xref:System.Windows.Controls.Slider> contrôle qui a des graduations.  
  
## <a name="example"></a>Exemple  
 Le <xref:System.Windows.Controls.Primitives.TickBar> s’affiche lorsque vous définissez la <xref:System.Windows.Controls.Slider.TickPlacement%2A> propriété une valeur autre que <xref:System.Windows.Controls.Primitives.TickPlacement>, qui est la valeur par défaut.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Slider> avec un <xref:System.Windows.Controls.Primitives.TickBar> affiche les marques de graduation. Le <xref:System.Windows.Controls.Slider.TickPlacement%2A> et <xref:System.Windows.Controls.Slider.TickFrequency%2A> propriétés définissent l’emplacement des graduations et l’intervalle entre eux. Lorsque vous déplacez le <xref:System.Windows.Controls.Primitives.Thumb>, info-bulles affichent la valeur de la <xref:System.Windows.Controls.Slider>. Le <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> propriété définit où les info-bulles s’affichent. Le <xref:System.Windows.Controls.Primitives.Thumb> mouvements correspondent à l’emplacement des graduations car <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> est défini sur `true`.  
  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.Controls.Slider.Ticks%2A> propriété pour créer des graduations le long de la <xref:System.Windows.Controls.Slider> à intervalles irréguliers.  
  
 [!code-xml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Slider>   
 <xref:System.Windows.Controls.Primitives.TickBar>   
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>   
 [Rubriques de procédures de curseur](http://msdn.microsoft.com/fr-fr/534be86c-afb2-425d-8186-631278a9925e)