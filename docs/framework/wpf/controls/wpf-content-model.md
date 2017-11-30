---
title: "Modèle de contenu WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52cb3a5391d6e24643b03a880d3695a11baceca3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wpf-content-model"></a>Modèle de contenu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu. Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.  
  
 Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle. Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu. Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.  
  
 
  
<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Classes qui contiennent du contenu arbitraire  
 Certains contrôles peuvent contenir un objet de tout type, tel qu’une chaîne, un <xref:System.DateTime> objet, ou un <xref:System.Windows.UIElement> qui est un conteneur pour d’autres éléments. Par exemple, un <xref:System.Windows.Controls.Button> peut contenir une image et du texte ; ou une <xref:System.Windows.Controls.CheckBox> peut contenir la valeur de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proposent quatre classes qui contiennent du contenu arbitraire. Le tableau suivant répertorie les classes qui héritent de <xref:System.Windows.Controls.Control>.  
  
|Classe qui contient du contenu arbitraire|Contenu|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Objet arbitraire unique.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|En-tête et élément unique, correspondant tous deux à des objets arbitraires.|  
|<xref:System.Windows.Controls.ItemsControl>|Collection d’objets arbitraires.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.|  
  
 Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon. L’illustration suivante montre un contrôle dérivé de chaque modèle de contenu qui contient une image et du texte.  
  
 ![Button, GroupBox, Listbax, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Contrôles qui contiennent un objet arbitraire unique  
 La <xref:System.Windows.Controls.ContentControl> classe contient un morceau unique de contenu arbitraire. Sa propriété de contenu est <xref:System.Windows.Controls.ContentControl.Content%2A>. Les contrôles suivants héritent de <xref:System.Windows.Controls.ContentControl> et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 L’illustration suivante montre quatre boutons dont <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une chaîne, un <xref:System.DateTime> objet, un <xref:System.Windows.Shapes.Rectangle>et un <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  
  
 ![Quatre boutons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.PNG "ControlContentModelButtons")  
Quatre boutons ayant différents types de contenu  
  
 Pour obtenir un exemple montrant comment définir le <xref:System.Windows.Controls.ContentControl.Content%2A> propriété, consultez <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Contrôles qui contiennent un en-tête et un objet arbitraire unique  
 Le <xref:System.Windows.Controls.HeaderedContentControl> hérite de la classe <xref:System.Windows.Controls.ContentControl> et affiche le contenu avec un en-tête. Il hérite de la propriété de contenu, <xref:System.Windows.Controls.ContentControl.Content%2A>, à partir de <xref:System.Windows.Controls.ContentControl> et définit les <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> propriété qui est de type <xref:System.Object>; par conséquent, les deux peuvent être un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedContentControl> et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 L’illustration suivante montre deux <xref:System.Windows.Controls.TabItem> objets. La première <xref:System.Windows.Controls.TabItem> a <xref:System.Windows.UIElement> des objets en tant que le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et <xref:System.Windows.Controls.ContentControl.Content%2A>. Le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>. Le <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Controls.TextBlock> et un <xref:System.Windows.Controls.Label>. La seconde <xref:System.Windows.Controls.TabItem> a une chaîne le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et un <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl qui utilise différents types dans la propriété d’en-tête  
  
 Pour obtenir un exemple montrant comment créer <xref:System.Windows.Controls.TabItem> , consultez <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent une collection d’objets arbitraires  
 Le <xref:System.Windows.Controls.ItemsControl> hérite de la classe <xref:System.Windows.Controls.Control> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou des autres éléments. Ses propriétés de contenu sont <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>est généralement utilisé pour remplir le <xref:System.Windows.Controls.ItemsControl> avec une collection de données. Si vous ne souhaitez pas utiliser une collection pour remplir le <xref:System.Windows.Controls.ItemsControl>, vous pouvez ajouter des éléments à l’aide de la <xref:System.Windows.Controls.ItemsControl.Items%2A> propriété.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.ItemsControl> et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.ListBox> qui contient ces types d’éléments :  
  
-   Chaîne.  
  
-   Objet <xref:System.DateTime>.  
  
-   <xref:System.Windows.UIElement>  
  
-   A <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  
  
 ![ListBox avec quatre types de contenu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
ListBox contenant plusieurs types de contenu  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent un en-tête et une collection d’objets arbitraires  
 Le <xref:System.Windows.Controls.HeaderedItemsControl> hérite de la classe <xref:System.Windows.Controls.ItemsControl> et peut contenir plusieurs éléments, tels que des chaînes, objets, ou autres éléments et un en-tête. Elle hérite la <xref:System.Windows.Controls.ItemsControl> propriétés, du contenu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, et <xref:System.Windows.Controls.ItemsControl.Items%2A>, et définit le <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> propriété qui peut être un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedItemsControl> et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes qui contiennent une collection d’objets UIElement  
 Le <xref:System.Windows.Controls.Panel> classe positionne et réorganise les enfants <xref:System.Windows.UIElement> objets. Sa propriété de contenu est <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Les classes suivantes héritent de la <xref:System.Windows.Controls.Panel> classe et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Classes qui affectent l’apparence d’un UIElement  
 Le <xref:System.Windows.Controls.Decorator> classe applique des effets visuels sur ou autour d’un seul enfant <xref:System.Windows.UIElement>. Sa propriété de contenu est <xref:System.Windows.Controls.Decorator.Child%2A>. Les classes suivantes héritent de <xref:System.Windows.Controls.Decorator> et utiliser son modèle de contenu :  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.TextBox> qui a (est décoré avec) un <xref:System.Windows.Controls.Border> autour de lui.  
  
 ![TextBox avec bordure noire](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock avec une bordure  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes qui fournissent des commentaires visuels sur un UIElement  
 La <xref:System.Windows.Documents.Adorner> classe fournit des signaux visuels à un utilisateur. Par exemple, utiliser un <xref:System.Windows.Documents.Adorner> pour ajouter des handles fonctionnels aux éléments ou fournir les informations d’état sur un contrôle. La <xref:System.Windows.Documents.Adorner> classe fournit une infrastructure afin que vous pouvez créer vos propres ornements. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne fournit aucun ornement implémenté. Pour plus d’informations, consultez [Vue d’ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Classes qui permettent aux utilisateurs d’entrer du texte  
 WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte. Chaque contrôle affiche le texte de manière différente. Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.  
  
|Contrôle|Texte affiché en tant que|Propriété de contenu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Texte brut|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texte mis en forme|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texte masqué (les caractères sont masqués)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Classes qui affichent votre texte  
 Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme. Vous pouvez utiliser <xref:System.Windows.Controls.TextBlock> pour afficher de petites quantités de texte. Si vous souhaitez afficher de grandes quantités de texte, utilisez la <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> contrôles.  
  
 Le <xref:System.Windows.Controls.TextBlock> a deux propriétés de contenu : <xref:System.Windows.Controls.TextBlock.Text%2A> et <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Lorsque vous souhaitez afficher du texte qui utilise la mise en forme cohérente, la <xref:System.Windows.Controls.TextBlock.Text%2A> propriété est souvent le meilleur choix. Si vous envisagez d’utiliser la mise en forme différente dans tout le texte, utilisez le <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété. Le <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété est une collection de <xref:System.Windows.Documents.Inline> objets, qui spécifient la mise en forme de texte.  
  
 Le tableau suivant répertorie la propriété de contenu pour <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.  
  
|Contrôle|Propriété de contenu|Type de propriété de contenu|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 Le <xref:System.Windows.Documents.FlowDocument> implémente la <xref:System.Windows.Documents.IDocumentPaginatorSource> interface ; par conséquent, les trois classes peuvent accepter un <xref:System.Windows.Documents.FlowDocument> en tant que contenu.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Classes de mise en forme du texte  
 <xref:System.Windows.Documents.TextElement>et ses classes connexes vous permettent de mettre en forme texte. <xref:System.Windows.Documents.TextElement>les objets contiennent et mettre en forme le texte dans <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument> objets. Les deux principaux types de <xref:System.Windows.Documents.TextElement> sont des objets <xref:System.Windows.Documents.Block> éléments et <xref:System.Windows.Documents.Inline> éléments. A <xref:System.Windows.Documents.Block> élément représente un bloc de texte, tel qu’un paragraphe ou d’une liste. Un <xref:System.Windows.Documents.Inline> élément représente une partie du texte dans un bloc. Nombreux <xref:System.Windows.Documents.Inline> classes spécifient la mise en forme du texte dans lequel ils sont appliqués. Chaque <xref:System.Windows.Documents.TextElement> possède son propre modèle de contenu. Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Avancé](../../../../docs/framework/wpf/advanced/index.md)
