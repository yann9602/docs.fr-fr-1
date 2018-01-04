---
title: Vue d'ensemble de l'expanseur
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f0623ed4c84247cc1759a203e3b95dd895cee2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="expander-overview"></a>Vue d'ensemble de l'expanseur
Un <xref:System.Windows.Controls.Expander> contrôle permet de fournir le contenu d’une zone développable qui ressemble à une fenêtre et inclut un en-tête.  
  
  
<a name="CreatinganExpanderinXAML"></a>   
## <a name="creating-a-simple-expander"></a>Créer un Expander simple  
 L’exemple suivant montre comment créer un simple <xref:System.Windows.Controls.Expander> contrôle. Cet exemple crée un <xref:System.Windows.Controls.Expander> qui ressemble à l’illustration précédente.  
  
 [!code-xaml[ExpanderExample#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 Le <xref:System.Windows.Controls.ContentControl.Content%2A> et <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> d’un <xref:System.Windows.Controls.Expander> peut également contenir un contenu complexe, tel que <xref:System.Windows.Controls.RadioButton> et <xref:System.Windows.Controls.Image> objets.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>   
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Définir la direction de la zone de contenu extensible  
 Vous pouvez définir la zone de contenu d’un <xref:System.Windows.Controls.Expander> contrôle à développer dans une des quatre directions (<xref:System.Windows.Controls.ExpandDirection.Down>, <xref:System.Windows.Controls.ExpandDirection.Up>, <xref:System.Windows.Controls.ExpandDirection.Left>, ou <xref:System.Windows.Controls.ExpandDirection.Right>) à l’aide de la <xref:System.Windows.Controls.ExpandDirection> propriété. Lorsque la zone de contenu est réduite, seul le <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et son bouton bascule apparaissent. A <xref:System.Windows.Controls.Button> contrôle qui affiche une flèche directionnelle est utilisé comme un bouton bascule pour développer ou réduire la zone de contenu. Quand il est développé, le <xref:System.Windows.Controls.Expander> essaie d’afficher tout son contenu dans une zone de fenêtre similaire.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>   
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Contrôler la taille d’un Expander dans un panneau  
 Si un <xref:System.Windows.Controls.Expander> contrôle se trouve dans un contrôle de disposition qui hérite de <xref:System.Windows.Controls.Panel>, tel que <xref:System.Windows.Controls.StackPanel>, ne spécifiez pas un <xref:System.Windows.FrameworkElement.Height%2A> sur le <xref:System.Windows.Controls.Expander> lorsque le <xref:System.Windows.Controls.Expander.ExpandDirection%2A> est définie sur <xref:System.Windows.Controls.ExpandDirection.Down> ou <xref:System.Windows.Controls.ExpandDirection.Up>. De même, ne spécifiez pas un <xref:System.Windows.FrameworkElement.Width%2A> sur la <xref:System.Windows.Controls.Expander> lors de la <xref:System.Windows.Controls.Expander.ExpandDirection%2A> est définie sur <xref:System.Windows.Controls.ExpandDirection.Left> ou <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Lorsque vous définissez une dimension sur un <xref:System.Windows.Controls.Expander> contrôle dans la direction que le contenu développé s’affiche, le <xref:System.Windows.Controls.Expander> prend le contrôle de la zone qui est utilisée par le contenu et affiche une bordure autour de lui. La bordure s’affiche même lorsque le contenu est réduit. Pour définir la taille de la zone de contenu développée, définissez des dimensions dans le contenu de la <xref:System.Windows.Controls.Expander>, ou si vous souhaitez que le défilement de la fonctionnalité, sur le <xref:System.Windows.Controls.ScrollViewer> qui englobe le contenu.  
  
 Lorsqu’un <xref:System.Windows.Controls.Expander> contrôle est le dernier élément dans un <xref:System.Windows.Controls.DockPanel>, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] définit automatiquement le <xref:System.Windows.Controls.Expander> dimensions pour être égale à la zone restante de la <xref:System.Windows.Controls.DockPanel>. Pour éviter ce comportement par défaut, définissez la <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> propriété sur le <xref:System.Windows.Controls.DockPanel> objet `false`, ou assurez-vous que le <xref:System.Windows.Controls.Expander> n’est pas le dernier élément dans un <xref:System.Windows.Controls.DockPanel>.  
  
<a name="CreatingScrollableContent"></a>   
## <a name="creating-scrollable-content"></a>Créer du contenu déroulant  
 Si le contenu est trop grand pour la taille de la zone de contenu, vous pouvez encapsuler le contenu d’un <xref:System.Windows.Controls.Expander> dans un <xref:System.Windows.Controls.ScrollViewer> afin de fournir un contenu déroulant. Le <xref:System.Windows.Controls.Expander> contrôle ne fournit pas automatiquement la fonction de défilement. L’illustration suivante montre un <xref:System.Windows.Controls.Expander> contrôle contenant un <xref:System.Windows.Controls.ScrollViewer> contrôle.  
  
 **Expander dans un ScrollViewer**  
  
 ![Expander avec ScrollBar](../../../../docs/framework/wpf/controls/media/expanderwithscrollbar.JPG "ExpanderWithScrollBar")  
  
 Lorsque vous placez un <xref:System.Windows.Controls.Expander> contrôler dans un <xref:System.Windows.Controls.ScrollViewer>, définissez le <xref:System.Windows.Controls.ScrollViewer> dimension de propriété qui correspond à la direction dans laquelle le <xref:System.Windows.Controls.Expander> contenu s’ouvre à la taille de la <xref:System.Windows.Controls.Expander> zone de contenu. Par exemple, si vous définissez la <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriété sur le <xref:System.Windows.Controls.Expander> à <xref:System.Windows.Controls.ExpandDirection.Down> (la zone de contenu s’ouvre vers le bas), définir le <xref:System.Windows.FrameworkElement.Height%2A> propriété sur le <xref:System.Windows.Controls.ScrollViewer> contrôle la hauteur requise pour la zone de contenu. Si vous définissez à la place la hauteur sur le contenu lui-même, <xref:System.Windows.Controls.ScrollViewer> ne reconnaît pas ce paramètre et par conséquent, ne fournit pas de contenu déroulant.  
  
 L’exemple suivant montre comment créer un <xref:System.Windows.Controls.Expander> contrôle qui a du contenu complexe et contenant un <xref:System.Windows.Controls.ScrollViewer> contrôle. Cet exemple crée un <xref:System.Windows.Controls.Expander> qui ressemble à l’illustration au début de cette section.  
  
 [!code-csharp[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>   
## <a name="using-the-alignment-properties"></a>Utiliser les propriétés d’alignement  
 Vous pouvez aligner le contenu en définissant le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> et <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> propriétés sur le <xref:System.Windows.Controls.Expander> contrôle. Lorsque vous définissez ces propriétés, l’alignement s’applique à l’en-tête ainsi qu’au contenu développé.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Controls.Expander>  
 <xref:System.Windows.Controls.ExpandDirection>  
 [Rubriques de guide pratique](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
