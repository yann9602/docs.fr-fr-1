---
title: "Vue d&#39;ensemble des propri&#233;t&#233;s de d&#233;pendance | Microsoft Docs"
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
  - "propriétés jointes"
  - "liaison de données"
  - "propriétés de dépendance"
  - "propriétés, attachées"
  - "propriétés, vue d'ensemble"
  - "ressources, références à"
  - "styles"
ms.assetid: d119d00c-3afb-48d6-87a0-c4da4f83dee5
caps.latest.revision: 30
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# Vue d&#39;ensemble des propri&#233;t&#233;s de d&#233;pendance
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit un jeu des services qui peuvent être utilisés pour étendre les fonctionnalités d'une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  Ensemble, ces services sont en général connus sous le nom de système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Une propriété stockée par le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est appelée [propriété de dépendance](GTMT). Cette vue d'ensemble décrit le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et les fonctionnalités d'une [propriété de dépendance](GTMT). Elle s'intéresse notamment à l'utilisation des [propriétés de dépendance](GTMT) existantes en XAML et dans le code.  Cette vue d'ensemble introduit également des aspects spécialisés des propriétés de dépendance, comme les métadonnées de propriété de dépendance, et explique comment créer votre propre propriété de dépendance dans une classe personnalisée.  
  
   
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique suppose que vous disposez de quelques connaissances de base de [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et de la programmation orientée objet.  Pour pouvoir suivre les exemples dans cette rubrique, vous devez également maîtriser le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et savoir écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Pour plus d'informations, consultez [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
<a name="why_dependency_properties"></a>   
## Propriétés de dépendance et propriétés CLR  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], les propriétés sont généralement exposées comme propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  À un niveau basique, vous pouvez interagir directement avec ces propriétés sans jamais savoir qu'elles sont implémentées en tant que [propriété de dépendance](GTMT).  Toutefois, vous devez vous familiariser avec quelques\-unes ou toutes les fonctionnalités du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour pouvoir en tirer parti.  
  
 Les [propriétés de dépendance](GTMT) ont pour but de permettre de calculer la valeur d'une propriété en fonction de la valeur d'autres entrées.  Ces autres entrées peuvent correspondre à des propriétés système \(p. ex. des thèmes et des préférences utilisateur\), des mécanismes de détermination de la propriété juste\-à\-temps \(p. ex. la liaison de données et les animations\/tables de montage séquentiel\), des modèles à utilisation multiple \(comme les ressources et les styles\) ou des valeurs connues à travers des relations parent\-enfant avec d'autres éléments dans l'arborescence d'éléments.  De plus, une [propriété de dépendance](GTMT) peut être implémentée pour fournir une validation autonome, des valeurs par défaut, des rappels que le moniteur remplace par d'autres propriétés, ainsi qu'un système qui peut forcer des valeurs de propriété selon des informations d'exécution potentielles.  Les classes dérivées peuvent également modifier certaines caractéristiques spécifiques d'une propriété existante en substituant les métadonnées de propriété de dépendance, au lieu de remplacer l'implémentation réelle de propriétés existantes ou de créer de nouvelles propriétés.  
  
 Dans la référence du Kit de développement, vous pouvez identifier les propriétés de dépendance par la présence de la section Informations sur les propriétés de dépendance à la page des références gérées de cette propriété.  La section Informations sur les propriétés de dépendance inclut un lien vers le champ d'identificateur <xref:System.Windows.DependencyProperty> pour cette propriété de dépendance, ainsi qu'une liste des options de métadonnées définies pour cette propriété, des informations de substitution par classe et d'autres détails.  
  
<a name="back_dependency_properties"></a>   
## Propriétés de dépendance stockant des propriétés CLR  
 Les [propriétés de dépendance](GTMT) et le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] étendent les fonctionnalités de propriété en fournissant un type qui stocke une propriété, comme une implémentation alternative du modèle standard de stockage de la propriété avec un champ privé.  Ce type s'appelle <xref:System.Windows.DependencyProperty>.  L'autre type important qui définit le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s'appelle <xref:System.Windows.DependencyObject>.<xref:System.Windows.DependencyObject> définit la classe de base qui peut enregistrer et posséder une [propriété de dépendance](GTMT).  
  
 Ci\-dessous figure un résumé de la terminologie utilisée dans cette documentation [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] pour traiter des [propriétés de dépendance](GTMT) :  
  
-   **Propriété de dépendance :** Propriété stockée par une <xref:System.Windows.DependencyProperty>.  
  
-   **Identificateur de propriété de dépendance :** instance <xref:System.Windows.DependencyProperty>, obtenue comme valeur de retour lors de l'enregistrement d'une [propriété de dépendance](GTMT), puis stockée comme membre statique d'une classe.  Cet identificateur est utilisé comme paramètre pour de nombreuses [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] qui interagissent avec le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   "**Wrapper CLR :** Implémentations Get et Set réelles pour la propriété.  Ces implémentations incorporent l'identificateur de propriété de dépendance en l'utilisant dans les appels <xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A>, stockant ainsi la propriété à l'aide du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 L'exemple suivant définit la [propriété de dépendance](GTMT) `IsSpinning` et montre la relation de l'identificateur <xref:System.Windows.DependencyProperty> avec la propriété qu'il stocke.  
  
 [!code-csharp[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic)]
 [!code-vb[PropertiesOvwSupport#DPFormBasic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#dpformbasic)]  
[!code-csharp[PropertiesOvwSupport#DPFormBasic2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#dpformbasic2)]  
  
 La convention d'affectation de noms de la propriété et son champ de stockage <xref:System.Windows.DependencyProperty> est importante.  Le nom du champ correspond toujours au nom de la propriété, avec le suffixe `Property`.  Pour plus d'informations sur cette convention et ses raisons, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
<a name="setting_property_values"></a>   
## Définition de valeurs de propriété  
 Vous pouvez définir des propriétés dans le code ou en XAML.  
  
<a name="local_property_values"></a>   
### Définition de valeurs de propriété en XAML  
 L'exemple XAML suivant affecte la couleur rouge à l'arrière\-plan d'un bouton.  Cet exemple illustre un cas dans lequel la valeur de la chaîne simple d'un attribut XAML est convertie par type par l'analyseur XAML WPF en un type [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] \(<xref:System.Windows.Media.Color>, par l'intermédiaire de <xref:System.Windows.Media.SolidColorBrush>\) dans le code généré.  
  
 [!code-xml[PropertiesOvwSupport#MostBasicProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#mostbasicproperty)]  
  
 XAML prend en charge diverses formes de syntaxe pour définir des propriétés.  La syntaxe à utiliser pour une propriété dépendra du type valeur utilisé par la propriété ainsi que d'autres facteurs tels que la présence d'un convertisseur de type.  Pour plus d'informations sur la syntaxe XAML pour la définition de propriétés, consultez [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md) et [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 À titre d'exemple de syntaxe autre qu'une syntaxe d'attribut, l'exemple de XAML suivant montre un autre arrière\-plan de bouton.  Cette fois, au lieu de définir une couleur unie, l'arrière\-plan a pour valeur une image, avec un élément représentant cette image et la source de cette image spécifiée comme attribut de l'élément imbriqué.  Il s'agit d'un exemple de syntaxe d'élément de propriété.  
  
 [!code-xml[PropertiesOvwSupport#PESyntaxProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml#pesyntaxproperty)]  
  
<a name="setting_properties_code"></a>   
### Définition de propriétés dans le code  
 La définition de valeurs de [propriété de dépendance](GTMT) dans le code correspond en général simplement à un appel de l'implémentation SET exposée par le wrapper [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyset)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertySet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyset)]  
  
 L'obtention d'une valeur de propriété correspond elle aussi essentiellement à un appel de l'implémentation GET du "wrapper" :  
  
 [!code-csharp[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/Page1.xaml.cs#proceduralpropertyget)]
 [!code-vb[PropertiesOvwSupport#ProceduralPropertyGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page1.xaml.vb#proceduralpropertyget)]  
  
 Vous pouvez également appeler directement [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]<xref:System.Windows.DependencyObject.GetValue%2A> et <xref:System.Windows.DependencyObject.SetValue%2A> du système de propriétés.  En général, ce n'est pas nécessaire si vous utilisez des propriétés existantes \(les wrappers sont plus pratiques et fournissent une meilleure exposition de la propriété pour les outils de développement\), mais l'appel direct des [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] convient pour certains scénarios.  
  
 Vous pouvez également définir des propriétés en XAML et y accéder ultérieurement dans le code, à l'aide de code\-behind.  Pour plus d'informations, consultez [Code\-behind et XAML dans WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
<a name="functionality"></a>   
## Fonctionnalités de propriété fournies par une propriété de dépendance  
 Une propriété de dépendance fournit des fonctionnalités qui étendent les fonctionnalités d'une propriété par opposition à une propriété stockée par un champ.  Souvent, les fonctionnalités de ce type représentent ou prennent en charge une fonctionnalité spécifique du jeu global de fonctionnalités de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
-   [Ressources](#setting_properties_resources)  
  
-   [Liaison des données](#setting_properties_data_binding)  
  
-   [Styles](#setting_properties_styles)  
  
-   [Animations](#animations)  
  
-   [Substitutions de métadonnées](#metadata)  
  
-   [Héritage de la valeur de propriété](#setting_properties_inheritance)  
  
-   [Intégration du Concepteur WPF](#vs2008_integration)  
  
<a name="setting_properties_resources"></a>   
### Ressources  
 Une valeur de propriété de dépendance peut être définie en référençant une ressource.  Les ressources sont en général spécifiées comme valeur de la propriété `Resources` d'un élément racine d'une page ou de l'application \(ces emplacements permettent d'accéder le plus facilement à la ressource\).  L'exemple suivant indique comment définir une ressource <xref:System.Windows.Media.SolidColorBrush>.  
  
 [!code-xml[PropertiesOvwSupport#ResourcesResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesresource)]  
  
 Une fois la ressource définie, vous pouvez la référencer et l'utiliser pour fournir une valeur de propriété :  
  
 [!code-xml[PropertiesOvwSupport#ResourcesReference](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page2.xaml#resourcesreference)]  
  
 Cette ressource est référencée comme [DynamicResource, extension de balisage](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) \(en XAML WPF, vous pouvez utiliser une référence à une ressource statique ou dynamique\).  Pour utiliser une référence à une ressource dynamique, vous devez définir à une propriété de dépendance de manière à ce que le système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] active précisément l'utilisation de la référence à une ressource dynamique.  Pour plus d'informations, consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
> [!NOTE]
>  Les ressources sont traitées comme valeur locale, ce qui signifie que si vous définissez une autre valeur locale, vous supprimerez la référence à la ressource.  Pour plus d'informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
<a name="setting_properties_data_binding"></a>   
### Liaison de données  
 Une propriété de dépendance peut référencer une valeur à travers la liaison de données.  La liaison de données fonctionne par le biais d'une syntaxe d'extension de balisage spécifique en XAML ou l'objet <xref:System.Windows.Data.Binding> dans le code.  Avec la liaison de données, la dernière détermination de valeur de propriété est différée jusqu'au moment de l'exécution, la valeur étant alors obtenue d'une source de données.  
  
 L'exemple suivant définit la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> pour un <xref:System.Windows.Controls.Button>, à l'aide d'une liaison déclarée en XAML.  La liaison utilise un contexte de données hérité et une source de données <xref:System.Windows.Data.XmlDataProvider> \(non illustré\).  La liaison elle\-même spécifie la propriété source souhaitée par <xref:System.Windows.Data.Binding.XPath%2A> dans la source de données.  
  
 [!code-xml[PropertiesOvwSupport#BasicInlineBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#basicinlinebinding)]  
  
> [!NOTE]
>  Les liaisons sont traitées comme valeurs locales, ce qui signifie que si vous définissez une autre valeur locale, vous supprimerez la liaison.  Pour plus d'informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Les propriétés de dépendance, ou la classe <xref:System.Windows.DependencyObject>, ne sont pas dotées d'une prise en charge native de <xref:System.ComponentModel.INotifyPropertyChanged> pour générer des notifications de modifications de la valeur de propriété source <xref:System.Windows.DependencyObject> pour les opérations de liaison de données.  Pour plus d'informations sur la création de propriétés à des fins de liaison de données pouvant signaler des modifications à une cible de liaison de données, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
<a name="setting_properties_styles"></a>   
### Styles  
 Les styles et les modèles sont deux des principaux scénarios justifiant l'utilisation de propriétés de dépendance.  Les styles sont particulièrement utiles pour configurer des propriétés qui définissent l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] de l'application.  Les styles sont en général définis en tant que ressources en XAML.  Les styles interagissent avec le système de propriétés parce qu'ils contiennent en général des « méthodes setter » pour des propriétés particulières, ainsi que des « déclencheurs » qui modifient une valeur de propriété selon la valeur en temps réel d'une autre propriété.  
  
 L'exemple suivant crée un style très simple \(qui serait défini à l'intérieur d'un dictionnaire <xref:System.Windows.FrameworkElement.Resources%2A>, non illustré\), puis applique ce style directement à la propriété <xref:System.Windows.FrameworkElement.Style%2A> d'un <xref:System.Windows.Controls.Button>.  L'accesseur Set du style affecte la couleur verte à la propriété <xref:System.Windows.Controls.Control.Background%2A> d'un <xref:System.Windows.Controls.Button> mis en forme.  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyleDef](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyledef)]  
  
 [!code-xml[PropertiesOvwSupport#SimpleStyle](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#simplestyle)]  
  
 Pour plus d'informations, consultez [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="animations"></a>   
### Animations  
 Les propriétés de dépendance peuvent être animées.  Lorsqu'une animation est appliquée et s'exécute, la valeur animée a priorité sur toutes les autres valeurs \(ex. valeur locale\) de la propriété.  
  
 L'exemple suivant anime le <xref:System.Windows.Controls.Control.Background%2A> d'une propriété <xref:System.Windows.Controls.Button> \(techniquement, le <xref:System.Windows.Controls.Control.Background%2A> est animé en utilisant la syntaxe d'élément de propriété pour spécifier un <xref:System.Windows.Media.SolidColorBrush> vierge comme <xref:System.Windows.Controls.Control.Background%2A>, puis la propriété <xref:System.Windows.Media.SolidColorBrush.Color%2A> de ce <xref:System.Windows.Media.SolidColorBrush> est la propriété qui est directement animée\).  
  
 [!code-xml[PropertiesOvwSupport#MiniAnimate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#minianimate)]  
  
 Pour plus d'informations sur l'animation de propriétés, consultez [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) et [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
<a name="metadata"></a>   
### Substitutions de métadonnées  
 Vous pouvez modifier certains comportements d'une [propriété de dépendance](GTMT) en substituant ses métadonnées lorsque vous dérivez de la classe qui enregistre initialement la [propriété de dépendance](GTMT).  La substitution de métadonnées repose sur l'identificateur <xref:System.Windows.DependencyProperty>.  La substitution de métadonnées ne requiert pas la réimplémentation de la propriété.  La modification de métadonnées est gérée en mode natif par le système de propriétés. Chaque classe contient potentiellement les métadonnées individuelles de toutes les propriétés héritées des classes de base, et ce, type par type.  
  
 L'exemple suivant substitue les métadonnées d'une propriété de dépendance <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>.  La substitution des métadonnées de cette propriété de dépendance fait partie d'un modèle d'implémentation qui crée des contrôles pouvant utiliser des styles par défaut provenant de thèmes.  
  
 [!code-csharp[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#overridemetadata)]
 [!code-vb[PropertiesOvwSupport#OverrideMetadata](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#overridemetadata)]  
  
 Pour plus d'informations sur la substitution ou l'obtention de métadonnées de propriétés, consultez [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="setting_properties_inheritance"></a>   
### Héritage de la valeur de propriété  
 Un élément peut hériter la valeur d'une propriété de dépendance de son parent dans l'arborescence d'objets.  
  
> [!NOTE]
>  Le comportement de l'héritage de la valeur de propriété n'est pas activé globalement pour toutes les propriétés de dépendance, parce que l'heure de calcul de l'héritage a un impact sur les performances.  L'héritage de valeur de propriété est en général activé uniquement pour les propriétés où un scénario particulier suggère que l'héritage de valeur de propriété est approprié.  Vous pouvez déterminer si une propriété de dépendance hérite en recherchant cette propriété de dépendance dans la section **Informations sur les propriétés de dépendance** du Kit de développement logiciel de référence.  
  
 L'exemple suivant illustre une liaison et définit la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> qui spécifie la source de la liaison, ce que l'exemple de liaison ci\-dessus ne montrait pas.  Les liaisons suivantes dans les objets enfants n'ont pas besoin de spécifier la source. Ils peuvent utiliser la valeur héritée de <xref:System.Windows.FrameworkElement.DataContext%2A> dans l'objet <xref:System.Windows.Controls.StackPanel> parent.  \(à la place, un objet enfant pourrait éventuellement choisir de spécifier directement son propre <xref:System.Windows.FrameworkElement.DataContext%2A> ou un <xref:System.Windows.Data.Binding.Source%2A> dans le <xref:System.Windows.Data.Binding> et de ne pas utiliser délibérément la valeur héritée pour le contexte de données de ses liaisons.\)  
  
 [!code-xml[PropertiesOvwSupport#InheritanceContext](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#inheritancecontext)]  
  
 Pour plus d'informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="vs2008_integration"></a>   
### Intégration du Concepteur WPF  
 Un contrôle personnalisé avec des propriétés implémentées comme propriétés de dépendance bénéficiera d'une prise en charge du [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] appropriée.  Par exemple, il permettra de modifier des propriétés de dépendance directes et jointes à l'aide de la fenêtre **Propriétés**.  Pour plus d'informations, consultez [Vue d'ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
<a name="value_determination"></a>   
## Priorité de la valeur de propriété de dépendance  
 Lorsque vous obtenez la valeur d'une [propriété de dépendance](GTMT), vous obtenez potentiellement une valeur définie pour cette propriété à l'aide de l'une des autres entrées basées sur des propriétés qui participent au système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  La priorité de la valeur de la propriété de dépendance est telle que plusieurs scénarios sur la façon dont les propriétés obtiennent leurs valeurs peuvent interagir de manière prévisible.  
  
 Prenons l'exemple suivant.  L'exemple inclut un style qui s'applique à tous les boutons et à leurs propriétés <xref:System.Windows.Controls.Control.Background%2A>, mais qui spécifie aussi un bouton avec une valeur <xref:System.Windows.Controls.Control.Background%2A> localement définie.  
  
> [!NOTE]
>  La documentation du Kit de développement logiciel utilise parfois les termes « valeur locale » et « valeur localement définie » pour désigner des propriétés de dépendance.  Une valeur localement définie est une valeur de propriété définie directement dans une instance d'objet dans le code ou en tant qu'attribut d'un élément dans XAML.  
  
 En principe, la propriété est définie deux fois pour le premier bouton, mais une seule valeur s'applique : la valeur ayant la priorité la plus élevée.  Une valeur localement définie a la priorité la plus élevée \(à l'exception d'une animation en cours d'exécution, mais aucune animation ne s'applique dans cet exemple\) et donc la valeur localement définie est utilisée au lieu de la valeur de l'accesseur Set du style pour l'arrière\-plan du premier bouton.  Le deuxième bouton n'a pas de valeur locale \(et aucune autre valeur ayant une priorité supérieure à un accesseur Set de style\) et donc, l'arrière\-plan de ce bouton provient de l'accesseur Set de style.  
  
 [!code-xml[PropertiesOvwSupport#MiniPrecedence](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml#miniprecedence)]  
  
### Pourquoi la priorité de la propriété de dépendance existe\-t\-elle ?  
 En général, vous ne souhaitez pas que des styles s'appliquent dans tous les cas et viennent masquer une valeur localement définie d'un élément individuel \(sinon, il serait très difficile d'utiliser des styles ou des éléments en général\).  Par conséquent, les valeurs qui proviennent de styles ont une priorité plus faible qu'une valeur localement définie.  Pour une liste plus complète des propriétés de dépendance et de l'origine éventuelle de la valeur effective d'une propriété de dépendance, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
> [!NOTE]
>  Nombre des propriétés définies pour des éléments [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne sont pas des propriétés de dépendance.  Dans l'ensemble, les propriétés ont été implémentées comme des propriétés de dépendance uniquement lorsqu'il fallait prendre en charge au moins l'un des scénarios autorisés par le système de propriétés : liaison de données, style, animation, prise en charge de valeur par défaut, héritage, propriétés jointes ou invalidation.  
  
<a name="dp_implement_roadmap"></a>   
## En savoir plus sur les propriétés de dépendance  
  
-   Une [propriété jointe](GTMT) est un type de propriété qui prend en charge une syntaxe particulière en XAML.  Souvent, une propriété attachée n'a pas de correspondance 1:1 avec une propriété [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] et n'est pas nécessairement une [propriété de dépendance](GTMT).  En général, une [propriété attachée](GTMT) a pour but de permettre à des éléments enfants de signaler des valeurs de propriété à un élément parent, même si l'élément parent et l'élément enfant ne possèdent pas tous les deux cette propriété dans le cadre des listes de membres de classe.  Le scénario principal consiste à permettre aux éléments enfants d'informer le parent sur la manière dont ils doivent être présentés dans [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Pour obtenir un exemple, consultez <xref:System.Windows.Controls.DockPanel.Dock%2A> ou <xref:System.Windows.Controls.Canvas.Left%2A>.  Pour plus d'informations, consultez [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
-   Les développeurs de composants ou d'applications peuvent souhaiter créer leur propre [propriété de dépendance](GTMT), pour activer des fonctions telles que la liaison de données ou le support de styles, ou pour l'invalidation et la prise en charge du forçage de valeur.  Pour plus d'informations, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Les propriétés de dépendance doivent en général être considérées comme des propriétés publiques, accessibles ou au moins détectables par tout appelant qui a accès à une instance.  Pour plus d'informations, consultez [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Propriétés de dépendance en lecture seule](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Architecture de WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)