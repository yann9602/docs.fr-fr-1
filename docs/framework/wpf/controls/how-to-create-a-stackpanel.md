---
title: "Comment&#160;: cr&#233;er un StackPanel | Microsoft Docs"
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
  - "Contrôle StackPanel, création"
ms.assetid: e7ce65cb-720a-4bb6-95b6-286b74488a58
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er un StackPanel
Cet exemple montre comment créer un <xref:System.Windows.Controls.StackPanel>.  
  
## <a name="example"></a>Exemple  
 A <xref:System.Windows.Controls.StackPanel> vous permet d’empiler des éléments dans une direction spécifiée. À l’aide des propriétés qui sont définies sur <xref:System.Windows.Controls.StackPanel>, contenu peut circuler verticalement, qui est le paramètre par défaut, ou horizontalement.  
  
 L’exemple suivant empile verticalement cinq <xref:System.Windows.Controls.TextBlock> des contrôles, chacun avec une autre <xref:System.Windows.Controls.Border> et <xref:System.Windows.Controls.Border.Background%2A>, à l’aide de <xref:System.Windows.Controls.StackPanel>. Les éléments enfants qui n’ont pas spécifié <xref:System.Windows.FrameworkElement.Width%2A> s’étirer pour remplir la fenêtre parente ; Toutefois, les éléments enfants qui ont une certaine <xref:System.Windows.FrameworkElement.Width%2A>, est centré dans la fenêtre.  
  
 La direction de la pile par défaut dans un <xref:System.Windows.Controls.StackPanel> est verticale. Flux de contrôle contenu dans un <xref:System.Windows.Controls.StackPanel>, utiliser le <xref:System.Windows.Controls.StackPanel.Orientation%2A> propriété. Vous pouvez contrôler l’alignement horizontal à l’aide de la <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> propriété.  
  
```xaml  
  
<Page xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation" WindowTitle="StackPanel Sample">  
  <StackPanel>  
    <Border Background="SkyBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="12">Stacked Item #1</TextBlock>  
    </Border>  
    <Border Width="400" Background="CadetBlue" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="14">Stacked Item #2</TextBlock>  
    </Border>  
    <Border Background="LightGoldenRodYellow" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="16">Stacked Item #3</TextBlock>  
    </Border>  
    <Border Width="200" Background="PaleGreen" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="18">Stacked Item #4</TextBlock>  
    </Border>  
    <Border Background="White" BorderBrush="Black" BorderThickness="1">  
      <TextBlock Foreground="Black" FontSize="20">Stacked Item #5</TextBlock>  
    </Border>  
  </StackPanel>  
</Page>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.StackPanel>   
 [Vue d’ensemble des panneaux](../../../../docs/framework/wpf/controls/panels-overview.md)   
 [Rubriques "Comment"](../../../../docs/framework/wpf/controls/stackpanel-how-to-topics.md)