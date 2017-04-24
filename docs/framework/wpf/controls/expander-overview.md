---
title: "Vue d&#39;ensemble de l&#39;expanseur | Microsoft Docs"
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
  - "contrôles, Expander"
  - "Expander (contrôle), à propos du contrôle Expander"
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Vue d&#39;ensemble de l&#39;expanseur
Le contrôle <xref:System.Windows.Controls.Expander> offre une façon de fournir du contenu dans une zone développable qui ressemble à une fenêtre et inclut un en\-tête.  
  
   
  
<a name="CreatinganExpanderinXAML"></a>   
## Création d'un expanseur simple  
 L'exemple suivant montre comment créer un contrôle <xref:System.Windows.Controls.Expander> simple.  Cet exemple crée un <xref:System.Windows.Controls.Expander> qui ressemble à l'illustration précédente.  
  
 [!code-xml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 Les <xref:System.Windows.Controls.ContentControl.Content%2A> et <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> d'un <xref:System.Windows.Controls.Expander> peuvent également contenir un contenu complexe, tel que des objets <xref:System.Windows.Controls.RadioButton> et <xref:System.Windows.Controls.Image>.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## Définition de la direction de la zone de contenu développée  
 Vous pouvez définir la zone de contenu d'un contrôle <xref:System.Windows.Controls.Expander> pour qu'elle se développe dans l'une des quatre directions \(<xref:System.Windows.Controls.ExpandDirection>, <xref:System.Windows.Controls.ExpandDirection>, <xref:System.Windows.Controls.ExpandDirection> ou <xref:System.Windows.Controls.ExpandDirection>\) à l'aide de la propriété <xref:System.Windows.Controls.ExpandDirection>.  Lorsque la zone de contenu est réduite, seul l'<xref:System.Windows.Controls.HeaderedContentControl.Header%2A> de l'<xref:System.Windows.Controls.Expander> et son bouton bascule apparaissent.  Un contrôle <xref:System.Windows.Controls.Button> qui affiche une flèche directionnelle est utilisé comme bouton bascule pour développer ou réduire la zone de contenu.  Lorsqu'il est développé, l'<xref:System.Windows.Controls.Expander> essaie d'afficher tout son contenu dans une zone similaire à une fenêtre.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## Contrôle de la taille d'un expanseur dans un panneau  
 Si un contrôle <xref:System.Windows.Controls.Expander> se trouve à l'intérieur d'un contrôle de disposition qui hérite d'un <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.StackPanel>, ne spécifiez pas de <xref:System.Windows.FrameworkElement.Height%2A> dans l'<xref:System.Windows.Controls.Expander> lorsque la propriété <xref:System.Windows.Controls.Expander.ExpandDirection%2A> a la valeur <xref:System.Windows.Controls.ExpandDirection> ou <xref:System.Windows.Controls.ExpandDirection>.  De la même façon, ne spécifiez pas de <xref:System.Windows.FrameworkElement.Width%2A> dans l'<xref:System.Windows.Controls.Expander> lorsque la propriété <xref:System.Windows.Controls.Expander.ExpandDirection%2A> a la valeur <xref:System.Windows.Controls.ExpandDirection> ou <xref:System.Windows.Controls.ExpandDirection>.  
  
 Lorsque vous définissez une dimension sur un contrôle <xref:System.Windows.Controls.Expander> dans la direction dans laquelle s'affiche le contenu développé, <xref:System.Windows.Controls.Expander> prend le contrôle de la zone utilisée par le contenu et affiche une bordure tout autour.  La bordure s'affiche même lorsque le contenu est réduit.  Pour définir la taille de la zone de contenu développée, définissez des dimensions dans le contenu de l'<xref:System.Windows.Controls.Expander> ou, si vous préférez, faites défiler les possibilités dans le <xref:System.Windows.Controls.ScrollViewer> qui comprend le contenu.  
  
 Lorsqu'un contrôle <xref:System.Windows.Controls.Expander> est le dernier élément d'un <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit automatiquement les dimensions <xref:System.Windows.Controls.Expander> pour qu'elles correspondent à la zone restante du <xref:System.Windows.Controls.DockPanel>.  Pour empêcher ce comportement par défaut, affectez à la propriété <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> de l'objet <xref:System.Windows.Controls.DockPanel> la valeur `false` ou assurez\-vous que l'<xref:System.Windows.Controls.Expander> n'est pas le dernier élément d'un <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## Création du contenu déroulant  
 Si le contenu est trop grand par rapport à la taille de la zone de contenu, vous pouvez encapsuler le contenu d'un <xref:System.Windows.Controls.Expander> dans un <xref:System.Windows.Controls.ScrollViewer> pour obtenir un contenu déroulant.  Le contrôle <xref:System.Windows.Controls.Expander> ne fournit pas automatiquement la fonction de défilement.  L'illustration suivante montre un contrôle <xref:System.Windows.Controls.Expander> qui contient un contrôle <xref:System.Windows.Controls.ScrollViewer>.  
  
 **Expanseur dans un ScrollViewer**  
  
 ![Expander avec barre de défilement](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Lorsque vous placez un contrôle <xref:System.Windows.Controls.Expander> dans un <xref:System.Windows.Controls.ScrollViewer>, affectez à la propriété de dimension <xref:System.Windows.Controls.ScrollViewer> qui correspond à la direction dans laquelle le contenu <xref:System.Windows.Controls.Expander> s'ouvre la taille de la zone de contenu <xref:System.Windows.Controls.Expander>.  Par exemple, si la propriété <xref:System.Windows.Controls.Expander.ExpandDirection%2A> de <xref:System.Windows.Controls.Expander> a la valeur <xref:System.Windows.Controls.ExpandDirection> \(la zone de contenu s'ouvre vers le bas\), affectez à la propriété <xref:System.Windows.FrameworkElement.Height%2A> du contrôle <xref:System.Windows.Controls.ScrollViewer> la hauteur requise pour la zone de contenu.  Si, en revanche, vous définissez la hauteur sur le contenu lui\-même, <xref:System.Windows.Controls.ScrollViewer> ne reconnaît pas ce paramètre et, par conséquent, ne fournit pas de contenu déroulant.  
  
 L'exemple suivant montre comment créer un contrôle <xref:System.Windows.Controls.Expander> avec un contenu complexe et contenant un contrôle <xref:System.Windows.Controls.ScrollViewer>.  Cet exemple crée un <xref:System.Windows.Controls.Expander> identique à l'illustration située au début de cette section.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## Utilisation des propriétés d'alignement  
 Vous pouvez aligner le contenu en définissant les propriétés <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> sur le contrôle <xref:System.Windows.Controls.Expander>.  Lorsque vous définissez ces propriétés, l'alignement s'applique à l'en\-tête ainsi qu'au contenu développé.  
  
## Voir aussi  
 <xref:System.Windows.Controls.Expander>   
 <xref:System.Windows.Controls.ExpandDirection>   
 [Rubriques Comment](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)