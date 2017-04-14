---
title: "Mod&#232;le de contenu&#160;WPF | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "classes à contenu arbitraire (WPF), modèle de contenu"
  - "affichage du contenu (WPF), contrôles"
  - "modèle de contenu (WPF), contrôles"
  - "ContentControl (classe WPF), afficher un contenu"
  - "contrôles (WPF), afficher du texte"
  - "contrôles (WPF), mettre en forme du texte"
  - "afficher du contenu (WPF)"
  - "UIElement (classe WPF), afficher un contenu"
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Mod&#232;le de contenu&#160;WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est une plateforme de présentation qui fournit de nombreux contrôles et types de contrôles dont l'objectif principal consiste à afficher différents types de contenu.  Pour déterminer le contrôle à utiliser ou le contrôle à partir duquel dériver, vous devez comprendre les genres d'objets qu'un contrôle particulier peut le mieux afficher.  
  
 Cette rubrique résume le modèle de contenu pour le contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les types de contrôle.  Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle. Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu.  Une propriété de contenu est une propriété utilisée pour stocker le contenu d'un objet.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="classes_that_contain_arbitrary_content"></a>   
## Classes qui contiennent du contenu arbitraire  
 Certains contrôles peuvent contenir un objet de tout type, tel qu'une chaîne, un objet <xref:System.DateTime> ou un <xref:System.Windows.UIElement> qui est un conteneur pour les éléments supplémentaires.  Par exemple, un <xref:System.Windows.Controls.Button> peut contenir une image et du texte ; ou un <xref:System.Windows.Controls.CheckBox> peut contenir la valeur de <xref:System.DateTime.Now%2A?displayProperty=fullName>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a quatre classes qui peuvent contenir du contenu arbitraire.  Le tableau suivant répertorie les classes qui héritent de <xref:System.Windows.Controls.Control>.  
  
|Classe qui contient du contenu arbitraire|Contenu|  
|-----------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Objet arbitraire unique.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|En\-tête et élément unique, les deux étant des objets arbitraires.|  
|<xref:System.Windows.Controls.ItemsControl>|Collection d'objets arbitraires.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|En\-tête et collection d'éléments, tous étant des objets arbitraires.|  
  
 Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon.  L'illustration suivante montre un contrôle à partir de chaque modèle de contenu qui contient une image et du texte.  
  
 ![Button, GroupBox, Listbox, TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### Contrôles qui contiennent un objet arbitraire unique  
 La classe <xref:System.Windows.Controls.ContentControl> contient un morceau unique de contenu arbitraire.  Sa propriété de contenu est <xref:System.Windows.Controls.ContentControl.Content%2A>.  Les contrôles suivants héritent de <xref:System.Windows.Controls.ContentControl> et utilisent son modèle de contenu :  
  
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
  
 L'illustration suivante montre quatre boutons dont <xref:System.Windows.Controls.ContentControl.Content%2A> a pour valeur une chaîne, un objet <xref:System.DateTime>, un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Panel> qui contient une <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  
  
 ![Quatre boutons](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.png "ControlContentModelButtons")  
Quatre boutons qui ont différents types de contenu  
  
 Pour obtenir un exemple décrivant comment définir la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>, consultez <xref:System.Windows.Controls.ContentControl>.  
  
### Contrôles qui contiennent un en\-tête et un objet arbitraire unique  
 La classe <xref:System.Windows.Controls.HeaderedContentControl> hérite de <xref:System.Windows.Controls.ContentControl> et affiche le contenu avec un en\-tête.  Elle hérite de la propriété de contenu, <xref:System.Windows.Controls.ContentControl.Content%2A>, à partir de <xref:System.Windows.Controls.ContentControl>, et définit la propriété <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> qui est de type <xref:System.Object> ; par conséquent, les deux peuvent correspondre à un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedContentControl> et utilisent son modèle de contenu :  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 L'illustration suivante présente deux objets <xref:System.Windows.Controls.TabItem>.  Le premier <xref:System.Windows.Controls.TabItem> a des objets <xref:System.Windows.UIElement> comme le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et le <xref:System.Windows.Controls.ContentControl.Content%2A>.  Le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a la valeur d'un <xref:System.Windows.Controls.StackPanel> qui contient une <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  Le <xref:System.Windows.Controls.ContentControl.Content%2A> a la valeur d'un <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Controls.TextBlock> et une <xref:System.Windows.Controls.Label>.  Le deuxième <xref:System.Windows.Controls.TabItem> a une chaîne dans le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et un <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
TabControl qui utilise différents types dans la propriété Header  
  
 Pour obtenir un exemple de création d'objets <xref:System.Windows.Controls.TabItem>, consultez <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### Contrôles qui contiennent une collection d'objets arbitraires  
 La classe <xref:System.Windows.Controls.ItemsControl> hérite de <xref:System.Windows.Controls.Control> et peut contenir des éléments complexes, tels que les chaînes, les objets ou les autres éléments.  Ses propriétés de contenu sont <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>.  <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est généralement utilisée pour remplir le <xref:System.Windows.Controls.ItemsControl> avec une collecte de données.  Si vous ne souhaitez pas utiliser une collection pour remplir le <xref:System.Windows.Controls.ItemsControl>, vous pouvez ajouter des éléments à l'aide de la propriété <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.ItemsControl> et utilisent son modèle de contenu :  
  
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
  
 L'illustration ci\-après montre un contrôle <xref:System.Windows.Controls.ListBox> qui contient ces types d'éléments :  
  
-   une chaîne ;  
  
-   un objet <xref:System.DateTime> ;  
  
-   un <xref:System.Windows.UIElement> ;  
  
-   un <xref:System.Windows.Controls.Panel> qui contient une <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  
  
 ![ListBox avec quatre types de contenu](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
Zone de liste qui contient plusieurs types d'objets  
  
### Contrôles qui contiennent un en\-tête et une collection d'objets arbitraires  
 La classe <xref:System.Windows.Controls.HeaderedItemsControl> hérite de <xref:System.Windows.Controls.ItemsControl> et peut contenir des éléments complexes, tels que des chaînes, des objets ou d'autres éléments, et un en\-tête.  Elle hérite des propriétés de contenu <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>, et définit la propriété <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> qui peut être un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedItemsControl> et utilisent son modèle de contenu :  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## Classes qui contiennent une collection d'objets UIElement  
 La classe <xref:System.Windows.Controls.Panel> positionne et réorganise des objets <xref:System.Windows.UIElement> enfants.  Sa propriété de contenu est <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Les classes suivantes héritent de la classe <xref:System.Windows.Controls.Panel> et utilisent son modèle de contenu :  
  
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
  
 Pour plus d'informations, consultez [Vue d'ensemble de Panel](../../../../docs/framework/wpf/controls/panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## Classes qui affectent l'apparence d'un UIElement  
 La classe <xref:System.Windows.Controls.Decorator> applique des effets visuels sur ou autour d'un enfant unique <xref:System.Windows.UIElement>.  Sa propriété de contenu est <xref:System.Windows.Controls.Decorator.Child%2A>.  Les classes suivantes héritent de <xref:System.Windows.Controls.Decorator> et utilisent son modèle de contenu :  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 L'illustration suivante montre un <xref:System.Windows.Controls.TextBox> qui a \(est décoré avec\) d'un <xref:System.Windows.Controls.Border> autour de lui.  
  
 ![TextBox avec bordure noire](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout\_Border\_around\_TextBox")  
TextBlock qui a une bordure  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## Classes qui fournissent la rétroaction visuelle à propos d'un UIElement  
 La classe <xref:System.Windows.Documents.Adorner> fournit des signaux visuels à un utilisateur.  Par exemple, utilisez un <xref:System.Windows.Documents.Adorner> pour ajouter des handles fonctionnels aux éléments ou fournir les informations d'état à propos d'un contrôle.  La classe <xref:System.Windows.Documents.Adorner> fournit une infrastructure afin que vous puissiez créer vos propres ornements.  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne fournit pas tous les ornements implémentés.  Pour plus d'informations, consultez [Vue d'ensemble des ornements](../../../../docs/framework/wpf/controls/adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## Classes qui permettent à des utilisateurs d'entrer du texte  
 WPF fournit trois contrôles primaires qui permettent aux utilisateurs d'entrer du texte.  Chaque contrôle affiche le texte différemment.  Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lorsqu'ils affichent du texte et leurs propriétés qui contiennent le texte du contrôle.  
  
|Contrôle|Le texte est affiché comme|Propriété de contenu|  
|--------------|--------------------------------|--------------------------|  
|<xref:System.Windows.Controls.TextBox>|Texte brut|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texte mis en forme|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texte masqué \(les caractères sont masqués\)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## Classes qui affichent votre texte  
 Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme.  Vous pouvez utiliser <xref:System.Windows.Controls.TextBlock> pour afficher des petites quantités de texte.  Si vous souhaitez afficher des grandes quantités de texte, utilisez les contrôles <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer> ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 Le <xref:System.Windows.Controls.TextBlock> dispose de deux propriétés de contenu : <xref:System.Windows.Controls.TextBlock.Text%2A> et <xref:System.Windows.Controls.TextBlock.Inlines%2A>.  Lorsque vous souhaitez afficher du texte qui utilise une mise en forme cohérente, la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> est souvent le meilleur choix que vous puissiez faire.  Si vous projetez d'utiliser une mise en forme différente dans tout le texte, utilisez la propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A>.  La propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A> est une collection d'objets <xref:System.Windows.Documents.Inline>, qui spécifie comment mettre en forme du texte.  
  
 Le tableau suivant présente la propriété de contenu associée aux classes <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer> et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
|Contrôle|Propriété de contenu|Type de propriété de contenu|  
|--------------|--------------------------|----------------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> implémente l'interface <xref:System.Windows.Documents.IDocumentPaginatorSource> ; par conséquent, les trois classes peuvent accepter un <xref:System.Windows.Documents.FlowDocument> en tant que contenu.  
  
<a name="classes_that_format_text"></a>   
## Classes qui mettent en forme votre texte  
 <xref:System.Windows.Documents.TextElement> et ses classes connexes vous permettent de mettre en forme du texte.  Les objets <xref:System.Windows.Documents.TextElement> contiennent et mettent en forme du texte dans les objets <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>.  Les deux types principaux d'objets <xref:System.Windows.Documents.TextElement> sont des éléments <xref:System.Windows.Documents.Block> et <xref:System.Windows.Documents.Inline>.  Un élément <xref:System.Windows.Documents.Block> représente un bloc de texte, tel qu'un paragraphe ou une liste.  Un élément <xref:System.Windows.Documents.Inline> représente une partie de texte dans un bloc.  De nombreuses classes <xref:System.Windows.Documents.Inline> spécifient la mise en forme pour le texte auquel elles s'appliquent.  Chaque <xref:System.Windows.Documents.TextElement> a son propre modèle de contenu.  Pour plus d'informations, consultez [Vue d'ensemble du modèle de contenu de TextElement](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md).  
  
## Voir aussi  
 [Avancé](../../../../docs/framework/wpf/advanced/index.md)