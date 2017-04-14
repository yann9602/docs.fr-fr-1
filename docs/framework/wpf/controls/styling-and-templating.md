---
title: "Application d&#39;un style et cr&#233;ation de mod&#232;les | Microsoft Docs"
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
  - "déclencheurs"
  - "styles, référence"
  - "déclencheurs d'événements"
  - "styles, configuration requise"
  - "styles, déclaration"
  - "styles, vue d’ensemble"
  - "styles, extension"
  - "styles, déclencheurs"
  - "styles, les déclencheurs d’événements"
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Application d&#39;un style et cr&#233;ation de mod&#232;les
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]styles et modèles font référence à une suite de fonctionnalités (styles, modèles, déclencheurs et storyboards) qui permettent aux développeurs et concepteurs pour créer des effets visuellement attrayants et une apparence cohérente pour leur produit. Bien que les développeurs et ou les concepteurs peuvent personnaliser l’apparence largement sur une base application-par-application, un modèle fort est nécessaire pour permettre la maintenance et le partage de l’apparence dans et entre les applications. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]fournit ce modèle.  
  
 Une autre fonctionnalité de la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de style est la séparation de la présentation et logique. Cela signifie que les concepteurs peuvent travailler sur l’apparence d’une application en utilisant uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] en même temps que les développeurs travaillent sur la programmation logique à l’aide de c# ou Visual Basic.  
  
 Cette présentation se concentre sur les aspects de style et de création de l’application et ne traite pas les concepts de liaison de données. Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 En outre, il est important de comprendre les ressources, qui permettent que les styles et modèles à réutiliser. Pour plus d’informations sur les ressources, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Styles et modèles, exemple  
 Les exemples de code utilisés dans cette vue d’ensemble sont basés sur un exemple de photo simple affiché dans l’illustration suivante :  
  
 ![Le style du ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Cet exemple de photo simple utilise des styles et modèles pour créer une expérience utilisateur visuellement attrayante. L’exemple a deux <xref:System.Windows.Controls.TextBlock> éléments et un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste d’images. Pour l’exemple complet, consultez la page [Introduction aux styles et modèles exemple](http://go.microsoft.com/fwlink/?LinkID=160010).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Principes fondamentaux de style  
 Vous pouvez considérer un <xref:System.Windows.Style> comme un moyen pratique pour appliquer un ensemble de valeurs de propriété à plusieurs éléments. Par exemple, considérez les éléments suivants <xref:System.Windows.Controls.TextBlock> éléments et leur apparence par défaut :  
  
 [!code-xml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")  
  
 Vous pouvez modifier l’apparence par défaut en définissant les propriétés, telles que <xref:System.Windows.Controls.Control.FontSize%2A> et <xref:System.Windows.Controls.Control.FontFamily%2A>, sur chaque <xref:System.Windows.Controls.TextBlock> élément directement. Toutefois, si vous souhaitez que votre <xref:System.Windows.Controls.TextBlock> éléments partagent certaines propriétés, vous pouvez créer un <xref:System.Windows.Style> dans les `Resources` section de votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de fichiers, comme illustré ici :  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Lorsque vous définissez la <xref:System.Windows.Style.TargetType%2A> de votre style pour le <xref:System.Windows.Controls.TextBlock> type, le style est appliqué à tous les le <xref:System.Windows.Controls.TextBlock> éléments dans la fenêtre.  
  
 Maintenant le <xref:System.Windows.Controls.TextBlock> éléments apparaissent comme suit :  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Extension de Styles  
 Vous pouvez choisir de vos deux <xref:System.Windows.Controls.TextBlock> éléments partagent certaines valeurs de propriété, tels que les <xref:System.Windows.Controls.Control.FontFamily%2A> et le texte centré <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, mais vous souhaitez également le texte « Mes images » ait quelques propriétés supplémentaires. Que faire en créant un nouveau style est basé sur le premier style, comme illustré ici :  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Notez que le style précédent reçoit un `x:Key`. Pour appliquer le style, vous définissez la <xref:System.Windows.FrameworkElement.Style%2A> propriété sur votre <xref:System.Windows.Controls.TextBlock> à la `x:Key` valeur, comme illustré ici :  
  
 [!code-xml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 Cela <xref:System.Windows.Controls.TextBlock> style a maintenant un <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valeur <xref:System.Windows.HorizontalAlignment>, un <xref:System.Windows.Controls.TextBlock.FontFamily%2A> valeur de `Comic Sans MS`, un <xref:System.Windows.Controls.TextBlock.FontSize%2A> valeur 26 et un <xref:System.Windows.Controls.TextBlock.Foreground%2A> la valeur la <xref:System.Windows.Media.LinearGradientBrush> indiqué dans l’exemple. Notez qu’il remplace le <xref:System.Windows.Controls.Control.FontSize%2A> valeur du style de base. S’il existe plusieurs <xref:System.Windows.Setter> définissent la même propriété un <xref:System.Windows.Style>, le <xref:System.Windows.Setter> qui est déclaré dernière est prioritaire.  
  
 L’exemple suivant montre que la <xref:System.Windows.Controls.TextBlock> éléments maintenant ressembler à :  
  
 ![Un style TextBlocks](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 Cela `TitleText` style étend le style qui a été créé pour le <xref:System.Windows.Controls.TextBlock> type. Vous pouvez également étendre un style qui a un `x:Key` à l’aide de la `x:Key` valeur. Pour obtenir un exemple, consultez l’exemple fourni pour la <xref:System.Windows.Style.BasedOn%2A> propriété.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relation entre la propriété TargetType et de l’attribut x : Key  
 Comme indiqué dans le premier exemple, la définition du <xref:System.Windows.Style.TargetType%2A> propriété `TextBlock` sans affecter le style un `x:Key` provoque le style à appliquer à tous les <xref:System.Windows.Controls.TextBlock> éléments. Dans ce cas, le `x:Key` a implicitement la valeur `{x:Type TextBlock}`. Cela signifie que si vous définissez explicitement la `x:Key` valeur autre que n’importe quoi `{x:Type TextBlock}`, le <xref:System.Windows.Style> n’est pas appliquée à tous les <xref:System.Windows.Controls.TextBlock> éléments automatiquement. Au lieu de cela, vous devez appliquer le style (à l’aide de la `x:Key` valeur) à la <xref:System.Windows.Controls.TextBlock> éléments explicitement. Si votre style se trouve dans la section ressources et vous ne définissez pas la <xref:System.Windows.Style.TargetType%2A> propriété sur votre style, vous devez fournir un `x:Key`.  
  
 En plus de fournir une valeur par défaut pour le `x:Key`, le <xref:System.Windows.Style.TargetType%2A> propriété spécifie le type auquel s’appliquent les propriétés d’accesseur Set. Si vous ne spécifiez pas un <xref:System.Windows.Style.TargetType%2A>, vous devez qualifier les propriétés dans votre <xref:System.Windows.Setter> objets avec un nom de classe à l’aide de la syntaxe `Property="ClassName.Property"`. Par exemple, au lieu de définir `Property="FontSize"`, vous devez définir <xref:System.Windows.Setter.Property%2A> à `"TextBlock.FontSize"` ou `"Control.FontSize"`.  
  
 Notez également que de nombreuses [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles se composent d’une combinaison d’autres [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] contrôles. Si vous créez un style qui s’applique à tous les contrôles d’un type, vous pouvez obtenir des résultats inattendus. Par exemple, si vous créez un style qui cible le <xref:System.Windows.Controls.TextBlock> type dans un <xref:System.Windows.Window>, le style est appliqué à tous les <xref:System.Windows.Controls.TextBlock> contrôles dans la fenêtre, même si le <xref:System.Windows.Controls.TextBlock> fait partie d’un autre contrôle, tel qu’un <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Styles et ressources  
 Vous pouvez utiliser un style sur tout élément qui dérive de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. La plus courante pour déclarer un style consiste en tant que ressource dans le `Resources` section dans un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de fichiers, comme indiqué dans les exemples précédents. Étant donné que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources ; Lorsque vous déclarez un style affecte où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine de votre définition d’application [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier, le style peut être utilisé n’importe où dans votre application. Si vous créez une application de navigation et déclarez le style dans un de l’application [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichiers, le style peuvent être utilisés que dans ce [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] fichier. Pour plus d’informations sur les règles relatives aux ressources de portée, consultez [ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 En outre, vous trouverez plus d’informations sur les styles et les ressources dans [ressources partagées et thèmes](#styling_themes) plus loin dans cette vue d’ensemble.  
  
### <a name="setting-styles-programmatically"></a>Définir des Styles par programmation  
 Pour attribuer un style nommé à un élément par programmation, obtenez le style de la collection de ressources et l’assigner à l’élément <xref:System.Windows.FrameworkElement.Style%2A> propriété. Notez que les éléments dans une collection de ressources sont de type <xref:System.Object>. Par conséquent, vous devez effectuer un cast du style extrait un <xref:System.Windows.Style> avant de l’assigner à la <xref:System.Windows.FrameworkElement.Style%2A> propriété. Par exemple, pour définir la période définie par `TitleText` style sur un <xref:System.Windows.Controls.TextBlock> nommé `textblock1`, procédez comme suit :  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Notez qu’une fois qu’un style a été appliqué, il est scellé et ne peut pas être modifié. Si vous souhaitez modifier dynamiquement un style qui a déjà été appliqué, vous devez créer un nouveau style pour remplacer celui-ci. Pour plus d’informations, consultez la <xref:System.Windows.Style.IsSealed%2A> propriété.  
  
 Vous pouvez créer un objet qui choisit un style à appliquer selon une logique personnalisée. Pour obtenir un exemple, consultez l’exemple fourni pour la <xref:System.Windows.Controls.StyleSelector> (classe).  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Liaisons, ressources dynamiques et gestionnaires d’événements  
 Notez que vous pouvez utiliser la `Setter.Value` pour spécifier un [Extension de balisage Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) ou un [Extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Pour plus d’informations, consultez les exemples fournis pour la <xref:System.Windows.Setter.Value%2A?displayProperty=fullName> propriété.  
  
 Jusqu'à présent, cette présentation décrit uniquement l’utilisation de méthodes setter pour définir la valeur de la propriété. Vous pouvez également spécifier des gestionnaires d’événements dans un style. Pour plus d’informations, consultez <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Modèles de données  
 Dans cet exemple d’application, il existe un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste de photos :  
  
 [!code-xml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 Cela <xref:System.Windows.Controls.ListBox> actuellement ressemble à ceci :  
  
 ![ListBox avant application du modèle](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 La plupart des contrôles ont un type de contenu, et ce contenu vient souvent des données que vous liez à. Dans cet exemple, les données sont la liste des photos. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous utilisez un <xref:System.Windows.DataTemplate> pour définir la représentation visuelle des données. En fait, vous placez dans un <xref:System.Windows.DataTemplate> détermine à quoi ressemblent les données dans l’application rendue.  
  
 Dans notre exemple d’application, chaque personnalisé `Photo` objet a un `Source` propriété de type chaîne qui spécifie le chemin d’accès de l’image. Actuellement, les objets photo apparaissent sous forme de chemins d’accès.  
  
 Pour les photos apparaissent comme des images, vous créez un <xref:System.Windows.DataTemplate> en tant que ressource :  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Notez que la <xref:System.Windows.DataTemplate.DataType%2A> propriété est très similaire à la <xref:System.Windows.Style.TargetType%2A> propriété de la <xref:System.Windows.Style>. Si votre <xref:System.Windows.DataTemplate> est dans la section ressources, lorsque vous spécifiez le <xref:System.Windows.DataTemplate.DataType%2A> à un type de propriété et ne lui assignez un `x:Key`, le <xref:System.Windows.DataTemplate> est appliqué chaque fois que ce type apparaît. Vous avez toujours la possibilité pour affecter le <xref:System.Windows.DataTemplate> avec un `x:Key` et définissez-le en tant qu’un `StaticResource` des propriétés qui acceptent <xref:System.Windows.DataTemplate> types, tels que les <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété ou le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
 Essentiellement, le <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus définit chaque fois qu’il est un `Photo` de l’objet, elle doit apparaître comme un <xref:System.Windows.Controls.Image> dans un <xref:System.Windows.Controls.Border>. Avec cette <xref:System.Windows.DataTemplate>, notre application se présente maintenant comme suit :  
  
 ![Image photo](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Le modèle de création de modèles fournit d’autres fonctionnalités. Par exemple, si vous affichez les données de collection qui contient d’autres collections à l’aide un <xref:System.Windows.Controls.HeaderedItemsControl> tapez comme un <xref:System.Windows.Controls.Menu> ou <xref:System.Windows.Controls.TreeView>, est la <xref:System.Windows.HierarchicalDataTemplate>. Une autre fonctionnalité de création de modèles de données est la <xref:System.Windows.Controls.DataTemplateSelector>, qui vous permet de choisir un <xref:System.Windows.DataTemplate> à utiliser selon une logique personnalisée. Pour plus d’informations, consultez [vue d’ensemble de la création de modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md), qui fournit une discussion plus approfondie sur les fonctionnalités de création de modèles de données différents.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Modèles de contrôle  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle définit l’apparence du contrôle. Vous pouvez modifier la structure et l’apparence d’un contrôle en définissant un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le contrôle. Dans de nombreux cas, cela vous donne suffisamment de souplesse afin que vous n’avez pas à écrire vos propres contrôles personnalisés. Pour plus d’informations, consultez [personnalisation de l’apparence d’un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Déclencheurs  
 Un déclencheur définit des propriétés ou démarre des actions, comme une animation, lorsqu’une valeur de propriété change ou lorsqu’un événement est déclenché. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, et <xref:System.Windows.DataTemplate> ont toutes un `Triggers` propriété pouvant contenir un jeu de déclencheurs. Il existe différents types de déclencheurs.  
  
### <a name="property-triggers"></a>Déclencheurs de propriété  
 A <xref:System.Windows.Trigger> que jeux de valeurs de propriété ou démarre des actions selon la valeur d’une propriété est appelé un déclencheur de propriété.  
  
 Pour illustrer l’utilisation de déclencheurs de propriété, vous pouvez rendre chaque <xref:System.Windows.Controls.ListBoxItem> partiellement transparents, sauf si elle est activée. Le style suivant affecte la <xref:System.Windows.UIElement.Opacity%2A> valeur un <xref:System.Windows.Controls.ListBoxItem> à `0.5`. Lors de la <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> propriété est `true`, toutefois, le <xref:System.Windows.UIElement.Opacity%2A> est défini sur `1.0`:  
  
 [!code-xml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Cet exemple utilise un <xref:System.Windows.Trigger> pour définir une valeur de propriété, mais notez que la <xref:System.Windows.Trigger> classe a également la <xref:System.Windows.TriggerBase.EnterActions%2A> et <xref:System.Windows.TriggerBase.ExitActions%2A> propriétés qui permettent à un déclencheur effectuer des actions.  
  
 Notez que la <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriétés de la <xref:System.Windows.Controls.ListBoxItem> est défini sur `75`. Dans l’illustration suivante, le troisième élément est l’élément sélectionné :  
  
 ![Le style du ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers et tables de montage séquentiel  
 Un autre type de déclencheur est le <xref:System.Windows.EventTrigger>, qui lance un ensemble d’actions en fonction de l’occurrence d’un événement. Par exemple, les éléments suivants <xref:System.Windows.EventTrigger> objets spécifient que lorsque le pointeur de la souris entre dans le <xref:System.Windows.Controls.ListBoxItem>, le <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété s’anime à la valeur `90` sur une `0.2` seconde période. Lorsque la souris se déplace loin de l’élément, la propriété retourne la valeur d’origine pendant une période de `1` seconde. Notez qu’il n’est pas nécessaire de spécifier un <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> la valeur pour le <xref:System.Windows.ContentElement.MouseLeave> animation. Il s’agit, car l’animation est capable d’effectuer le suivi de la valeur d’origine.  
  
 [!code-xml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Pour plus d’informations, consultez la [Storyboards Overview](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Dans l’illustration suivante, la souris pointe sur le troisième élément :  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers et MultiDataTriggers  
 En plus de <xref:System.Windows.Trigger> et <xref:System.Windows.EventTrigger>, il existe d’autres types de déclencheurs. <xref:System.Windows.MultiTrigger> vous permet de définir des valeurs de propriété selon plusieurs conditions. Vous utilisez <xref:System.Windows.DataTrigger> et <xref:System.Windows.MultiDataTrigger> lorsque la propriété de votre condition est liée aux données.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Ressources partagées et thèmes  
 Un type [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application peut avoir plusieurs ressources d’interface utilisateur utilisateur sont appliqués à l’application. Collectivement, cet ensemble de ressources peut être considéré comme le thème de l’application. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]prend en charge pour l’utilisateur d’empaquetage ressources d’interface utilisateur comme un thème à l’aide d’un dictionnaire de ressources encapsulé en tant que la <xref:System.Windows.ResourceDictionary> classe.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]les thèmes sont définis en utilisant le mécanisme de styles et modèles qui [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] expose pour la personnalisation des visuels de tout élément.  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]ressources de thème sont stockées dans les dictionnaires de ressources incorporées. Ces dictionnaires de ressources doivent être incorporés dans un assembly signé, et peut être incorporé dans le même assembly que le code lui-même ou dans un assembly côte à côte. Dans le cas de PresentationFramework.dll, l’assembly qui contient [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] les contrôles, les ressources de thème sont dans une série d’assemblys côte à côte.  
  
 Le thème devient la dernière place à consulter lors de la recherche du style d’un élément. En règle générale, la recherche commence en remontant l’arborescence d’éléments pour une ressource appropriée, puis rechercher dans la collection de ressources d’application et enfin interroge le système. Cela permet aux développeurs d’applications de redéfinir le style pour tout objet au niveau de l’arborescence ou une application avant d’atteindre le thème.  
  
 Vous pouvez définir des dictionnaires de ressources comme des fichiers individuels qui vous permettent de réutiliser un thème entre plusieurs applications. Vous pouvez également créer des thèmes permutables en définissant plusieurs dictionnaires de ressources qui fournissent les mêmes types de ressources mais avec des valeurs différentes. Redéfinir ces styles ou autres ressources au niveau de l’application est l’approche recommandée pour définir l’apparence une application.  
  
 Pour partager un ensemble de ressources, y compris les styles et modèles, entre les applications, vous pouvez créer un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de fichiers et définir un <xref:System.Windows.ResourceDictionary>. Par exemple, un coup de œil sur l’illustration suivante qui montre une partie de la [style avec ControlTemplates, exemple](http://go.microsoft.com/fwlink/?LinkID=160041):  
  
 ![Exemples de modèle de contrôle](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Si vous examinez la [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] des fichiers de l’exemple, vous remarquerez que tous ont les éléments suivants :  
  
 [!code-xml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 C’est le partage de `shared.xaml`, qui définit un <xref:System.Windows.ResourceDictionary> qui contient un ensemble de ressources de style et un pinceau qui active les contrôles dans l’exemple d’avoir une apparence cohérente.  
  
 Pour plus d’informations, consultez [dictionnaires de ressources fusionnés](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Si vous créez un thème vous contrôle personnalisé, consultez la section bibliothèque de contrôles externes de la [Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [Comment : rechercher des éléments générés par ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [Rechercher des éléments générés par DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)