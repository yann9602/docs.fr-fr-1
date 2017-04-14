---
title: "M&#233;tadonn&#233;es de propri&#233;t&#233; d&#39;infrastructure | Microsoft Docs"
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
  - "métadonnées de propriété d'infrastructure"
  - "métadonnées, propriétés d'infrastructure"
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# M&#233;tadonn&#233;es de propri&#233;t&#233; d&#39;infrastructure
Des options de métadonnées de propriété d'infrastructure sont signalées pour les propriétés d'éléments objet considérés au [niveau de l'infrastructure WPF](GTMT) dans l'architecture [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  En général, la désignation [niveau d'infrastructure WPF](GTMT) implique la gestion de fonctionnalités telles que le rendu, la liaison de données et les ajustements du système de propriétés par les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] de présentation et les fichiers exécutables de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les métadonnées de propriété d'infrastructure sont interrogées par ces systèmes afin d'identifier les caractéristiques spécifiques aux fonctionnalités de propriétés d'élément particuliers.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="prerequisites"></a>   
## Composants requis  
 Cette rubrique part du principe que vous comprenez les [propriétés de dépendance](GTMT) du point de vue d'un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] et que vous avez lu [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  Vous devez également avoir lu [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## Informations communiquées par les métadonnées de propriété d'infrastructure  
 Les métadonnées de propriété d'infrastructure peuvent être réparties dans les catégories suivantes :  
  
-   Propriétés de présentation qui affectent un élément \(<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>\).  Vous pouvez définir ces indicateurs dans des métadonnées si la propriété affecte ces aspects respectifs et si vous implémentez les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> \/ <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> dans votre classe pour fournir un comportement de rendu spécifique et des informations au système de disposition.  En général, une telle implémentation vérifie la présence d'invalidations de propriété dans les propriétés de dépendance dont des propriétés de disposition avaient la valeur true dans les métadonnées de propriété, et seules ces invalidations font l'objet d'une demande de nouvelle passe de disposition.  
  
-   Propriétés de présentation qui affectent l'élément parent d'un élément \(<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>\).  <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=fullName> et <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=fullName> sont deux exemples où ces indicateurs sont définis par défaut.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>.  Par défaut, les propriétés de dépendance n'héritent pas de valeurs.  <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> permet à la voie d'héritage de se déplacer également dans une arborescence d'éléments visuels, ce qui est nécessaire pour certains scénarios de composition de contrôle.  
  
    > [!NOTE]
    >  Le terme "hérite" dans le contexte des valeurs de propriété revêt une signification spécifique pour les propriétés de dépendance ; il signifie que les éléments enfants peuvent hériter de la valeur de propriété de dépendance réelle des éléments parents grâce à une fonctionnalité [au niveau de l'infrastructure WPF](GTMT) du système de propriétés [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Cette notion est donc sans rapport direct avec le type de code managé et l'héritage de membres par le biais de types dérivés.  Pour plus d'informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Caractéristiques de liaison de données \(<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>\).  Par défaut, les propriétés de dépendance de l'infrastructure prennent en charge la liaison de données, avec un comportement de liaison unidirectionnel.  Vous pouvez désactiver la liaison de données s'il n'existe aucun scénario \(dans la mesure où elles sont conçues pour être flexibles et extensibles, il existe très peu d'exemples de telles propriétés dans les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut\).  Vous pouvez définir une liaison bidirectionnelle par défaut pour les propriétés qui lient les comportements d'un contrôle parmi ses composants \(<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A>, par exemple\) ou lorsque la liaison bidirectionnelle est le scénario attendu et le plus courant pour les utilisateurs \(<xref:System.Windows.Controls.TextBox.Text%2A>, par exemple\).  La modification des métadonnées associées à la liaison de données influence uniquement la valeur par défaut ; cette valeur par défaut peut toujours être modifiée pour chaque liaison individuelle.  Pour plus d'informations sur les modes de liaison et la liaison en général, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Enregistrement ou non des propriétés dans un journal par des applications ou des services prenant en charge la journalisation \(<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>\).  Par défaut, la journalisation n'est pas activée pour les éléments généraux, mais l'est de manière sélective pour certains contrôles d'entrée d'utilisateur.  Cette propriété est destinée à être lue par des services de journalisation, y compris l'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de journalisation, et est généralement définie sur des contrôles utilisateur, tels que des sélections d'utilisateur dans des listes qui doivent être rendues persistantes à travers les étapes de navigation.  Pour plus d'informations sur le journal, consultez [Vue d'ensemble de la navigation](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## Lecture de FrameworkPropertyMetadata  
 Les propriétés liées ci\-dessus sont les propriétés que <xref:System.Windows.FrameworkPropertyMetadata> ajoute à sa classe de base immédiate <xref:System.Windows.UIPropertyMetadata>.  Par défaut, toutes ces propriétés ont la valeur `false`.  Lorsqu'il est important de connaître la valeur de ces propriétés, une demande de métadonnées pour une propriété doit essayer d'effectuer un cast des métadonnées retournées à <xref:System.Windows.FrameworkPropertyMetadata>, puis vérifier les valeurs des propriétés individuelles, selon les besoins.  
  
<a name="Specifying_Metadata"></a>   
## Spécification des métadonnées  
 Lorsque vous créez une instance de métadonnées en vue d'appliquer des métadonnées à une nouvelle inscription de propriété de dépendance, vous avez le choix de la classe de métadonnées à utiliser : la classe <xref:System.Windows.PropertyMetadata> de base ou une classe dérivée quelconque, telle que <xref:System.Windows.FrameworkPropertyMetadata>.  En général, vous devez utiliser <xref:System.Windows.FrameworkPropertyMetadata>, en particulier si votre propriété interagit avec le système de propriétés et des fonctions [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] telles que la disposition et la liaison de données.  Une autre option pour créer des scénarios plus sophistiqués consiste à dériver à partir de la classe <xref:System.Windows.FrameworkPropertyMetadata> afin de créer votre propre classe de rapport de métadonnées, dont les membres contiennent des informations complémentaires.  Vous pouvez également utiliser <xref:System.Windows.PropertyMetadata> ou <xref:System.Windows.UIPropertyMetadata> pour communiquer le degré de prise en charge des fonctionnalités de votre implémentation.  
  
 Pour les propriétés existantes \(appel <xref:System.Windows.DependencyProperty.AddOwner%2A> ou <xref:System.Windows.DependencyProperty.OverrideMetadata%2A>\), vous devez toujours effectuer une substitution avec le type de métadonnées utilisé par l'inscription d'origine.  
  
 Si vous créez une instance <xref:System.Windows.FrameworkPropertyMetadata>, vous pouvez compléter ces métadonnées avec des valeurs pour les propriétés spécifiques qui communiquent les caractéristiques de propriété d'infrastructure de deux façons différentes :  
  
1.  Utilisez la signature de constructeur <xref:System.Windows.FrameworkPropertyMetadata> qui autorise un paramètre `flags`.  Saisissez dans ce paramètre toutes les valeurs combinées souhaitées des indicateurs d'énumération <xref:System.Windows.FrameworkPropertyMetadataOptions>.  
  
2.  Utilisez une des signatures sans paramètre `flags`, puis affectez la valeur `true` à chaque propriété booléenne de création de rapport sur <xref:System.Windows.FrameworkPropertyMetadata> pour chaque modification de caractéristique souhaitée.  Si vous optez pour cette solution, vous devez définir ces propriétés avant la construction de tout élément possédant cette propriété de dépendance ; les propriétés booléennes sont en lecture\-écriture afin d'autoriser ce comportement d'évitement du paramètre `flags` tout en complétant les métadonnées. Les métadonnées doivent toutefois être sealed avant l'utilisation de la propriété.  Par conséquent, toute tentative de définition des propriétés après l'envoi d'une demande de métadonnées est une opération incorrecte.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## Comportement de fusion des métadonnées de propriété d'infrastructure  
 Lorsque vous substituez des métadonnées de propriété l'infrastructure, les différentes caractéristiques des métadonnées sont soit fusionnées, soit remplacées.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est fusionné.  Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, ce rappel est stocké dans les métadonnées.  Si vous ne spécifiez pas de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est promue en tant que référence de l'ancêtre le plus proche qui l'a spécifiée dans les métadonnées.  
  
-   Le comportement réel du système de propriétés pour <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> est le suivant : des implémentations sont conservées et ajoutées à une table pour tous les propriétaires de métadonnées dans la hiérarchie et l'exécution par le système de propriétés commence par les rappels de la classe la plus dérivée.  Les rappels hérités ne sont exécutés qu'une seule fois et sont considérés comme s'ils appartenaient à la classe qui les a placés dans les métadonnées.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> est remplacé.  Si vous ne spécifiez pas de <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.DefaultValue%2A> est prise dans l'ancêtre le plus proche qui l'a spécifiée dans les métadonnées.  
  
-   Les implémentations de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> sont remplacées.  Si vous ajoutez un nouveau <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, ce rappel est stocké dans les métadonnées.  Si vous ne spécifiez pas de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> dans la substitution, la valeur de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> est promue en tant que référence de l'ancêtre le plus proche qui l'a spécifiée dans les métadonnées.  
  
-   Le comportement du système de propriétés est le suivant : seul le <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> présent dans les métadonnées immédiates est appelé.  Aucune référence à d'autres implémentations de <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> dans la hiérarchie n'est conservée.  
  
-   Les indicateurs d'énumération <xref:System.Windows.FrameworkPropertyMetadataOptions> sont combinés en une opération de bits OR.  Si vous spécifiez <xref:System.Windows.FrameworkPropertyMetadataOptions>, les options d'origine ne sont pas remplacées.  Pour modifier une option, définissez la propriété correspondante dans <xref:System.Windows.FrameworkPropertyMetadata>.  Par exemple, si l'objet <xref:System.Windows.FrameworkPropertyMetadata> d'origine définit l'indicateur <xref:System.Windows.FrameworkPropertyMetadataOptions?displayProperty=fullName>, vous pouvez modifier cela en affectant à <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=fullName> la valeur `false`.  
  
 Ce comportement est implémenté par <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A> et peut être substitué sur des classes de métadonnées dérivées.  
  
## Voir aussi  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>   
 [Métadonnées de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)