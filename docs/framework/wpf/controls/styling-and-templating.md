---
title: "Application d'un style et création de modèles"
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
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c33739d0e753146ffdc8b825d88c6ca7ba63fa1a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="styling-and-templating"></a>Application d'un style et création de modèles
L’application d'un style et la création de modèles [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] font référence à une suite de fonctionnalités (styles, modèles, déclencheurs et tables de montage séquentiel) qui permettent aux développeurs et aux concepteurs de créer des effets visuellement attrayants et un aspect cohérent pour leur produit. Bien que les développeurs et/ou les concepteurs puissent largement personnaliser une à une l’apparence de leur application, il est essentiel d’utiliser un modèle de création de style et de modèle suffisamment robuste pour conserver et partager l’apparence dans une même application et entre différentes applications. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit ce modèle.  
  
 La séparation de la présentation et de la logique est une autre fonctionnalité du modèle d’application de style [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Les concepteurs peuvent ainsi travailler sur l’apparence d’une application en utilisant uniquement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], tout en laissant les développeurs travailler sur la logique de programmation à l’aide de C# ou de Visual Basic.  
  
 Cette présentation se concentre sur les aspects liés à la création de style et de modèle pour l’application et ne traite pas des concepts de liaison de données. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 En outre, il est important de comprendre les ressources qui permettent de réutiliser les styles et les modèles. Pour plus d’informations sur les ressources, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>Exemple de style et de modèle  
 Les exemples de code utilisés dans cette présentation s’appuient sur un exemple de photo simple affiché dans l’illustration suivante :  
  
 ![Styled ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 Cet exemple de photo simple utilise des styles et des modèles pour créer une expérience utilisateur visuellement attrayante. L’exemple a deux <xref:System.Windows.Controls.TextBlock> éléments et un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste d’images. Pour accéder à l’exemple complet, consultez la page [Introduction to Styling and Templating Sample](http://go.microsoft.com/fwlink/?LinkID=160010) (Présentation d’un exemple de création de style et de modèle).  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>Principes de base d’un style  
 Vous pouvez considérer un <xref:System.Windows.Style> comme un moyen pratique d’appliquer un ensemble de valeurs de propriété à plusieurs éléments. Par exemple, considérez les éléments suivants <xref:System.Windows.Controls.TextBlock> éléments et leur apparence par défaut :  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 Vous pouvez modifier l’apparence par défaut en définissant des propriétés, telles que <xref:System.Windows.Controls.Control.FontSize%2A> et <xref:System.Windows.Controls.Control.FontFamily%2A>, sur chaque <xref:System.Windows.Controls.TextBlock> élément directement. Toutefois, si vous souhaitez que votre <xref:System.Windows.Controls.TextBlock> éléments partagent certaines propriétés, vous pouvez créer un <xref:System.Windows.Style> dans les `Resources` section de votre [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de fichiers, comme indiqué ici :  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Lorsque vous définissez la <xref:System.Windows.Style.TargetType%2A> de votre style pour le <xref:System.Windows.Controls.TextBlock> type, le style est appliqué à tous les le <xref:System.Windows.Controls.TextBlock> éléments dans la fenêtre.  
  
 Maintenant le <xref:System.Windows.Controls.TextBlock> éléments apparaissent comme suit :  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>Extension des styles  
 Vous pouvez choisir de vos deux <xref:System.Windows.Controls.TextBlock> éléments partagent certaines valeurs de propriétés, telles que la <xref:System.Windows.Controls.Control.FontFamily%2A> et le texte centré <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, mais que vous voulez également le texte « Mes images » ont des propriétés supplémentaires. Vous pouvez procéder en créant un nouveau style dérivé du premier style, comme illustré ici :  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Notez que le style précédent est affecté à un `x:Key`. Pour appliquer le style, vous définissez la <xref:System.Windows.FrameworkElement.Style%2A> propriété sur votre <xref:System.Windows.Controls.TextBlock> à la `x:Key` valeur, comme indiqué ici :  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 Cela <xref:System.Windows.Controls.TextBlock> style a maintenant un <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> valeur de <xref:System.Windows.HorizontalAlignment.Center>, un <xref:System.Windows.Controls.TextBlock.FontFamily%2A> valeur `Comic Sans MS`, un <xref:System.Windows.Controls.TextBlock.FontSize%2A> valeur 26 et un <xref:System.Windows.Controls.TextBlock.Foreground%2A> la valeur la <xref:System.Windows.Media.LinearGradientBrush> indiqué dans l’exemple. Notez qu’il remplace le <xref:System.Windows.Controls.Control.FontSize%2A> valeur du style de base. S’il existe plusieurs <xref:System.Windows.Setter> définissent la même propriété un <xref:System.Windows.Style>, le <xref:System.Windows.Setter> qui est déclaré dernière est prioritaire.  
  
 L’exemple suivant montre ce que le <xref:System.Windows.Controls.TextBlock> éléments maintenant ressembler à :  
  
 ![Blocs de texte mis en forme avec des styles](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 Cela `TitleText` style étend le style qui a été créé pour le <xref:System.Windows.Controls.TextBlock> type. Vous pouvez également étendre un style qui comporte un `x:Key` à l’aide de la valeur `x:Key`. Pour obtenir un exemple, consultez l’exemple fourni pour la <xref:System.Windows.Style.BasedOn%2A> propriété.  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>Relation entre la propriété TargetType et l’attribut x: Key  
 Comme indiqué dans le premier exemple, la définition du <xref:System.Windows.Style.TargetType%2A> propriété `TextBlock` sans affecter le style une `x:Key` provoque le style à appliquer à tous les <xref:System.Windows.Controls.TextBlock> éléments. Dans ce cas, l’attribut `x:Key` a implicitement la valeur `{x:Type TextBlock}`. Cela signifie que si vous définissez explicitement la `x:Key` valeur autre que `{x:Type TextBlock}`, le <xref:System.Windows.Style> n’est pas appliquée à tous les <xref:System.Windows.Controls.TextBlock> éléments automatiquement. Au lieu de cela, vous devez appliquer le style (à l’aide de la `x:Key` valeur) à la <xref:System.Windows.Controls.TextBlock> éléments explicitement. Si votre style se trouve dans la section ressources et que vous ne définissez pas le <xref:System.Windows.Style.TargetType%2A> propriété de votre style, puis vous devez fournir un `x:Key`.  
  
 En plus de fournir une valeur par défaut pour le `x:Key`, le <xref:System.Windows.Style.TargetType%2A> propriété spécifie le type auquel s’appliquent les propriétés d’accesseur Set. Si vous ne spécifiez pas un <xref:System.Windows.Style.TargetType%2A>, vous devez qualifier les propriétés dans votre <xref:System.Windows.Setter> objets avec un nom de classe à l’aide de la syntaxe `Property="ClassName.Property"`. Par exemple, au lieu de paramètre `Property="FontSize"`, vous devez définir <xref:System.Windows.Setter.Property%2A> à `"TextBlock.FontSize"` ou `"Control.FontSize"`.  
  
 Notez également que de nombreux contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se composent d’une combinaison d’autres contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Si vous créez un style qui s’applique à tous les contrôles d’un type, vous pouvez obtenir des résultats inattendus. Par exemple, si vous créez un style qui cible le <xref:System.Windows.Controls.TextBlock> de type dans un <xref:System.Windows.Window>, le style est appliqué à tous les <xref:System.Windows.Controls.TextBlock> contrôles dans la fenêtre, même si le <xref:System.Windows.Controls.TextBlock> fait partie d’un autre contrôle, tel qu’un <xref:System.Windows.Controls.ListBox>.  
  
### <a name="styles-and-resources"></a>Styles et ressources  
 Vous pouvez utiliser un style sur tout élément qui dérive de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>. Le moyen le plus courant de déclarer un style consiste à le déclarer en tant que ressource dans la section `Resources` d’un fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme indiqué dans les exemples précédents. Étant donné que les styles sont des ressources, ils obéissent aux mêmes règles de portée qui s’appliquent à toutes les ressources ; l’emplacement où vous déclarez un style affecte l’endroit où le style peut être appliqué. Par exemple, si vous déclarez le style dans l’élément racine du fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de votre définition d’application, le style peut être utilisé n’importe où dans votre application. Si vous créez une application de navigation et que vous déclarez le style dans un des fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de l’application, le style ne pourra être utilisé que dans ce fichier [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Pour plus d’informations sur les règles de portée des ressources, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 Vous trouverez également d’autres informations sur les styles et les ressources dans la section [Ressources et thèmes partagés](#styling_themes) plus loin dans cette vue d’ensemble.  
  
### <a name="setting-styles-programmatically"></a>Définir des styles par programmation  
 Pour affecter un style nommé à un élément par programmation, obtenez le style de la collection de ressources et l’affecter à l’élément <xref:System.Windows.FrameworkElement.Style%2A> propriété. Notez que les éléments dans une collection de ressources sont de type <xref:System.Object>. Par conséquent, vous devez effectuer un cast du style extrait un <xref:System.Windows.Style> avant de l’assigner à la <xref:System.Windows.FrameworkElement.Style%2A> propriété. Par exemple, pour définir la période définie par `TitleText` sous un <xref:System.Windows.Controls.TextBlock> nommé `textblock1`, procédez comme suit :  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 Notez qu’une fois qu’un style a été appliqué, il est scellé et ne peut pas être modifié. Si vous souhaitez modifier dynamiquement un style qui a déjà été appliqué, vous devez créer un nouveau style pour le remplacer. Pour plus d'informations, consultez la propriété <xref:System.Windows.Style.IsSealed%2A>.  
  
 Vous pouvez créer un objet qui choisit un style à appliquer selon une logique personnalisée. Pour obtenir un exemple, consultez l’exemple fourni pour la <xref:System.Windows.Controls.StyleSelector> classe.  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>Liaisons, ressources dynamiques et gestionnaires d’événements  
 Notez que vous pouvez utiliser la propriété `Setter.Value` pour spécifier une [extension de balisage Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md) ou une [extension de balisage DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md). Pour plus d’informations, consultez les exemples fournis pour la <xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType> propriété.  
  
 Jusqu'à présent, cette présentation décrivait uniquement l’utilisation de méthodes setter pour définir la valeur de la propriété. Vous pouvez également spécifier des gestionnaires d’événements dans un style. Pour plus d'informations, consultez <xref:System.Windows.EventSetter>.  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>Modèles de données  
 Dans cet exemple d’application, il existe un <xref:System.Windows.Controls.ListBox> contrôle qui est lié à une liste de photos :  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 Cela <xref:System.Windows.Controls.ListBox> actuellement présente l’aspect suivant :  
  
 ![ListBox avant application du modèle](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 La plupart des contrôles ont un type de contenu, et ce contenu provient souvent des données que vous liez à ces contrôles. Dans cet exemple, les données sont la liste de photos. Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vous utilisez un <xref:System.Windows.DataTemplate> pour définir la représentation visuelle des données. En fait, ce que vous placez dans un <xref:System.Windows.DataTemplate> détermine ce que les données apparaissent comme dans l’application rendue.  
  
 Dans notre exemple d’application, chaque objet `Photo` personnalisé a une propriété `Source` de type chaîne qui spécifie le chemin d’accès à l’image. Actuellement, les objets photo apparaissent sous forme de chemins d’accès.  
  
 Pour les photos apparaissent comme des images, vous créez un <xref:System.Windows.DataTemplate> en tant que ressource :  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 Notez que la <xref:System.Windows.DataTemplate.DataType%2A> propriété est très similaire à la <xref:System.Windows.Style.TargetType%2A> propriété de la <xref:System.Windows.Style>. Si votre <xref:System.Windows.DataTemplate> est dans la section de ressources, lorsque vous spécifiez la <xref:System.Windows.DataTemplate.DataType%2A> à un type de propriété et lui n'assignez pas une `x:Key`, le <xref:System.Windows.DataTemplate> est appliqué à chaque fois que ce type s’affiche. Vous pouvez toujours affecter la <xref:System.Windows.DataTemplate> avec un `x:Key` et définissez-le en tant qu’un `StaticResource` des propriétés qui acceptent <xref:System.Windows.DataTemplate> types, tels que le <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> propriété ou le <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriété.  
  
 Essentiellement, le <xref:System.Windows.DataTemplate> dans l’exemple ci-dessus définit chaque fois qu’il est un `Photo` de l’objet, elle doit apparaître comme un <xref:System.Windows.Controls.Image> au sein d’un <xref:System.Windows.Controls.Border>. Avec cette <xref:System.Windows.DataTemplate>, notre application maintenant ressemble à ceci :  
  
 ![Image photo](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 Le modèle de création de modèles fournit d’autres fonctionnalités. Par exemple, si vous affichez les données de collection qui contient d’autres collections à l’aide un <xref:System.Windows.Controls.HeaderedItemsControl> tapez comme un <xref:System.Windows.Controls.Menu> ou un <xref:System.Windows.Controls.TreeView>, est le <xref:System.Windows.HierarchicalDataTemplate>. Une autre fonctionnalité de création de modèles de données est la <xref:System.Windows.Controls.DataTemplateSelector>, qui vous permet de choisir un <xref:System.Windows.DataTemplate> à utiliser selon une logique personnalisée. Pour plus d’informations, consultez l’article [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md), qui fournit une discussion plus approfondie sur les différentes fonctionnalités de création de modèles de données.  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>Modèles de contrôle  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], le <xref:System.Windows.Controls.ControlTemplate> d’un contrôle définit l’apparence du contrôle. Vous pouvez modifier la structure et l’apparence d’un contrôle en définissant un nouveau <xref:System.Windows.Controls.ControlTemplate> pour le contrôle. Dans de nombreux cas, cela vous donne suffisamment de souplesse pour ne pas avoir à écrire vos propres contrôles personnalisés. Pour plus d’informations, consultez [Personnalisation de l'apparence d'un contrôle existant en créant un ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>Déclencheurs  
 Un déclencheur définit des propriétés ou démarre des actions, par exemple une animation, lorsqu’une valeur de propriété change ou lorsqu’un événement est déclenché. <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, et <xref:System.Windows.DataTemplate> ont tous un `Triggers` propriété pouvant contenir un ensemble de déclencheurs. Il existe différents types de déclencheurs.  
  
### <a name="property-triggers"></a>Déclencheurs de propriété  
 A <xref:System.Windows.Trigger> que jeux de valeurs de propriété ou démarre des actions en fonction de la valeur d’une propriété est appelé un déclencheur de propriété.  
  
 Pour illustrer l’utilisation de déclencheurs de propriété, vous pouvez rendre chaque <xref:System.Windows.Controls.ListBoxItem> partiellement transparent, sauf si elle est sélectionnée. Le style suivant affecte la <xref:System.Windows.UIElement.Opacity%2A> valeur un <xref:System.Windows.Controls.ListBoxItem> à `0.5`. Lorsque le <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> propriété est `true`, toutefois, le <xref:System.Windows.UIElement.Opacity%2A> a la valeur `1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 Cet exemple utilise un <xref:System.Windows.Trigger> pour définir une valeur de propriété, mais notez que la <xref:System.Windows.Trigger> classe a également la <xref:System.Windows.TriggerBase.EnterActions%2A> et <xref:System.Windows.TriggerBase.ExitActions%2A> propriétés qui activent un déclencheur effectuer des actions.  
  
 Notez que la <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété de la <xref:System.Windows.Controls.ListBoxItem> a la valeur `75`. Dans l’illustration suivante, le troisième élément est l’élément sélectionné :  
  
 ![Styled ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>EventTriggers et tables de montage séquentiel  
 Un autre type de déclencheur est le <xref:System.Windows.EventTrigger>, qui lance un ensemble d’actions en fonction de l’occurrence d’un événement. Par exemple, les éléments suivants <xref:System.Windows.EventTrigger> les objets qui spécifient quand le pointeur de la souris entre dans le <xref:System.Windows.Controls.ListBoxItem>, le <xref:System.Windows.FrameworkElement.MaxHeight%2A> propriété réalise une animation à une valeur de `90` sur un `0.2` seconde période. Lorsque la souris s’éloigne de l’élément, la propriété retourne à sa valeur d’origine pendant une période de `1` seconde. Notez qu’il n’est pas nécessaire de spécifier un <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> la valeur pour le <xref:System.Windows.ContentElement.MouseLeave> animation. L’animation est en effet capable d’effectuer le suivi de la valeur d’origine.  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 Pour plus d’informations, consultez l’article [Vue d’ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Dans l’illustration suivante, la souris pointe sur le troisième élément :  
  
 ![Capture d’écran : exemple de styles](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers, DataTriggers et MultiDataTriggers  
 En plus de <xref:System.Windows.Trigger> et <xref:System.Windows.EventTrigger>, il existe d’autres types de déclencheurs. <xref:System.Windows.MultiTrigger>vous permet de définir des valeurs de propriété selon plusieurs conditions. Vous utilisez <xref:System.Windows.DataTrigger> et <xref:System.Windows.MultiDataTrigger> lorsque la propriété de votre condition est liée aux données.  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>Ressources et thèmes partagés  
 Une application [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] type peut avoir plusieurs ressources d’interface utilisateur qui sont appliquées sur l’ensemble de l’application. Collectivement, cet ensemble de ressources peut être considéré comme le thème de l’application. [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]prend en charge pour l’utilisateur de l’empaquetage ressources d’interface utilisateur comme un thème à l’aide d’un dictionnaire de ressources qui est encapsulé en tant que la <xref:System.Windows.ResourceDictionary> classe.  
  
 Le thèmes [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] sont définis en utilisant le mécanisme de styles et modèles exposé par [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] pour la personnalisation des visuels de tout élément.  
  
 Les ressources de thème [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] sont stockées dans des dictionnaires de ressources incorporés. Ces dictionnaires de ressources doivent être incorporés dans un assembly signé, et peuvent être incorporés dans le même assembly que le code lui-même, ou bien dans un assembly parallèle. Dans le cas de PresentationFramework.dll, l’assembly qui contient les contrôles [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)], les ressources de thème se trouvent dans une série d’assemblys parallèles.  
  
 Le thème est alors le dernier emplacement à consulter lors de la recherche du style d’un élément. En règle générale, la recherche commence en remontant l’arborescence d’éléments pour rechercher une ressource appropriée, avant de consulter la collection de ressources d’application et d’interroger pour finir le système. Cela permet aux développeurs d’applications de redéfinir le style pour n’importe quel objet au niveau de l’arborescence ou de l’application avant d’atteindre le thème.  
  
 Vous pouvez définir des dictionnaires de ressources sous forme de fichiers individuels qui vous permettent de réutiliser un thème entre plusieurs applications. Vous pouvez également créer des thèmes permutables en définissant plusieurs dictionnaires de ressources qui fournissent les mêmes types de ressources mais avec des valeurs différentes. Pour définir l’apparence une application, il est recommandé de redéfinir ces styles ou d’autres ressources au niveau de l’application.  
  
 Pour partager un ensemble de ressources, y compris les styles et modèles, entre les applications, vous pouvez créer un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de fichiers et de définir un <xref:System.Windows.ResourceDictionary>. Par exemple, observez l’illustration suivante qui montre une partie de [l’exemple de style avec ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041) :  
  
 ![Exemples de modèle de contrôle](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 Si vous examinez les fichiers [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] de l’exemple, vous remarquerez qu’ils comportent tous les éléments suivants :  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 C’est le partage de `shared.xaml`, qui définit un <xref:System.Windows.ResourceDictionary> qui contient un ensemble de ressources de style et un pinceau qui active les contrôles dans l’exemple d’avoir une apparence cohérente.  
  
 Pour plus d’informations, consultez [Dictionnaires de ressources fusionnés](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).  
  
 Si vous créez un thème pour votre contrôle personnalisé, consultez la section relative aux bibliothèques de contrôles externes de la page [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
## <a name="see-also"></a>Voir aussi  
 [URI à en-tête pack dans WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [Guide pratique pour rechercher des éléments générés par ControlTemplate](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [Rechercher des éléments générés par DataTemplate](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
