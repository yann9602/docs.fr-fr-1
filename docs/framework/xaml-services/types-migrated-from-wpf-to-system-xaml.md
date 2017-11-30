---
title: "Types migrés de WPF vers System.Xaml"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
caps.latest.revision: "14"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: db227b5c7915b6ce0b0fe8400a8545256ea6d6b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>Types migrés de WPF vers System.Xaml
Dans [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)] et [!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)], [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] et [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] incluaient tous les deux une implémentation de langage XAML. La plupart des types publics qui fournissaient une extensibilité pour l'implémentation XAML WPF se trouvaient dans les assemblys WindowsBase, PresentationCore et PresentationFramework. De même, les types publics qui fournissaient une extensibilité pour le langage XAML [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] se trouvaient dans l'assembly System.Workflow.ComponentModel. Dans [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], certains types XAML sont migrés vers l'assembly System.Xaml. Une implémentation .NET Framework courante de services de langage XAML autorise de nombreux scénarios d'extensibilité XAML initialement définis par l'implémentation XAML d'une infrastructure spécifique mais faisant désormais partie de la prise en charge globale du langage XAML [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] . Cette rubrique répertorie les types qui sont migrés et traite des problèmes relatifs à la migration.  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>Assemblys et espaces de noms  
 Dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], les types implémentés par WPF pour prendre en charge le langage XAML se trouvaient généralement dans l'espace de noms <xref:System.Windows.Markup> . La plupart de ces types se trouvaient dans l'assembly WindowsBase.  
  
 Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], un nouvel espace de noms <xref:System.Xaml> et un nouvel assembly System.Xaml ont été créés. La plupart des types implémentés initialement pour XAML WPF sont maintenant fournis comme points ou services d'extensibilité pour les implémentations du langage XAML. En vue de les rendre disponibles pour des scénarios plus généraux, les types sont transférés de leur assembly WPF d'origine vers l'assembly System.Xaml. Cela autorise les scénarios d'extensibilité XAML sans avoir à inclure les assemblys d'autres infrastructures (telles que WPF et [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)]).  
  
 En ce qui concerne les types migrés, ils restent pour la plupart dans l'espace de noms <xref:System.Windows.Markup> . Cela permettait en partie d'éviter d'interrompre le mappage des espaces de noms CLR dans les implémentations existantes par fichier. Par conséquent, l'espace de noms <xref:System.Windows.Markup> de [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] contient un mélange de types généraux de prise en charge du langage XAML (provenant de l'assembly System.Xaml) et de types spécifiques à l'implémentation XAML WPF (provenant de WindowsBase et d'autres assemblys WPF). Tous les types migrés vers System.Xaml, mais se trouvant déjà dans un assembly WPF, prennent en charge le transfert des types dans la version 4 de l'assembly WPF.  
  
### <a name="workflow-xaml-support-types"></a>Types de prise en charge XAML du flux de travail  
 [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] fournissait également des types de prise en charge XAML, et dans de nombreux cas, ils portaient les mêmes noms courts qu'un équivalent WPF. Voici une liste de types de prise en charge XAML [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] .  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 Ces types de prise en charge se trouvent toujours dans les assemblys [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] de [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] et peuvent encore être utilisés pour des applications [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)] spécifiques, mais ils ne doivent pas être référencés par des applications ou des infrastructures n'utilisant pas [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)].  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 Dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], la classe <xref:System.Windows.Markup.MarkupExtension> pour WPF se trouvait dans l'assembly WindowsBase. Pour [!INCLUDE[TLA#tla_workflow](../../../includes/tlasharptla-workflow-md.md)], une classe parallèle, <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>, se trouvait dans l'assembly System.Workflow.ComponentModel. Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la classe <xref:System.Windows.Markup.MarkupExtension> est migrée vers l'assembly System.Xaml. Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.Windows.Markup.MarkupExtension> est destiné aux scénarios d'extensibilité XAML qui utilisent les services XAML .NET Framework, et pas seulement pour ceux qui s'appuient sur des infrastructures spécifiques. Lorsque cela est possible, les infrastructures spécifiques ou le code utilisateur de l'infrastructure doivent également s'appuyer sur la classe <xref:System.Windows.Markup.MarkupExtension> pour l'extension XAML.  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>Classes de services de prise en charge MarkupExtension  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] pour WPF fournissaient plusieurs services qui étaient disponibles pour les implémenteurs de <xref:System.Windows.Markup.MarkupExtension> et les implémentations <xref:System.ComponentModel.TypeConverter> afin de prendre en charge l'utilisation des types et des propriétés en XAML. Ces services sont les suivants :  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  L’interface [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] est un autre service de <xref:System.Windows.Markup.IReceiveMarkupExtension> associé aux extensions de balisage. Cette inferface<xref:System.Windows.Markup.IReceiveMarkupExtension> n’a pas été migrée et est signalée comme `[Obsolete]` pour [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Les scénarios qui utilisaient l'interface <xref:System.Windows.Markup.IReceiveMarkupExtension> doivent désormais utiliser les rappels avec attribut <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> . La classe<xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> est également signalée comme `[Obsolete]`.  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>Fonctionnalités du langage XAML  
 Plusieurs fonctionnalités et composants du langage XAML pour WPF se trouvaient déjà dans l'assembly PresentationFramework. Ils ont été implémentés en tant que sous-classe <xref:System.Windows.Markup.MarkupExtension> pour exposer les utilisations des extensions de balisage en XAML dans le balisage XAML. Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ils se trouvent dans l'assembly System.Xaml afin que les projets n'incluant pas d'assemblys WPF puissent utiliser ces fonctionnalités au niveau du langage XAML. WPF utilise ces mêmes implémentations pour les applications [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] . Comme avec d'autres situations répertoriées dans cette rubrique, les types de prise en charge se trouvent toujours dans l'espace de noms <xref:System.Windows.Markup> afin d'éviter d'endommager les références précédentes.  
  
 Le tableau suivant contient une liste des classes de prise en charge des fonctionnalités XAML définies dans System.Xaml.  
  
|Fonctionnalité du langage XAML|Utilisation|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 Bien que System.Xaml ne dispose pas nécessairement de classes de prise en charge spécifiques, la logique générale en matière de traitement des fonctionnalités du langage XAML se trouve désormais dans System.Xaml, ainsi que dans ses lecteurs et writers XAML implémentés. Par exemple, `x:TypeArguments` est un attribut traité par les lecteurs et les writers XAML des implémentations System.Xaml. Il peut être signalé dans le flux de nœud XAML, gère le contexte de schéma XAML par défaut (basé sur CLR), a une représentation système de type XAML, etc. Par conséquent, la documentation de référence pour toutes les fonctionnalités au niveau du langage XAML constitue une sous-rubrique des [XAML Services](../../../docs/framework/xaml-services/index.md) et de cette zone générale de l’ensemble de documentation .NET Framework, et ne fait donc pas partie de la documentation WPF comme sous-rubrique de la rubrique [Avancé (Windows Presentation Foundation)](../../../docs/framework/wpf/advanced/index.md) (comme c’est toujours le cas dans les ensembles de documentation 3.5).  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer et classes de prise en charge  
 La classe <xref:System.Windows.Markup.ValueSerializer> prend en charge la conversion de type en chaîne, en particulier dans les cas de sérialisation XAML où la sérialisation peut nécessiter plusieurs modes ou nœuds dans la sortie. Dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], la classe <xref:System.Windows.Markup.ValueSerializer> pour WPF se trouvait dans l'assembly WindowsBase. Dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], la classe <xref:System.Windows.Markup.ValueSerializer> se trouve dans System.Xaml et est destinée aux scénarios d’extensibilité XAML, et pas uniquement à ceux qui s’appuient sur WPF. <xref:System.Windows.Markup.IValueSerializerContext> (service de prise en charge) et <xref:System.Windows.Markup.DateTimeValueSerializer> (sous-classe spécifique) sont également migrés vers System.Xaml.  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>Attributs XAML  
 XAML WPF incluait plusieurs attributs qui peuvent être appliqués aux types CLR pour indiquer certains éléments concernant leur comportement XAML. Voici une liste des attributs qui se trouvaient dans les assemblys WPF dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]. Ces attributs sont migrés vers System.Xaml dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)].  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>Classes diverses  
 L’interface <xref:System.Windows.Markup.IComponentConnector> se trouvait dans WindowsBase dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], mais elle se trouve dans System.Xaml dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.IComponentConnector> est principalement conçu pour la prise en charge des outils et les compilateurs de balisage XAML.  
  
 L’interface <xref:System.Windows.Markup.INameScope> se trouvait dans WindowsBase dans [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] et [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)], mais elle se trouve dans System.Xaml dans [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. <xref:System.Windows.Markup.INameScope> définit les opérations de base pour une portée de nom XAML.  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>Classes XAML portant les noms partagés qui se trouvent dans WPF et System.Xaml  
 Les classes suivantes se trouvent à la fois dans les assemblys WPF et dans l'assembly System.Xaml de [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]:  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 L'implémentation WPF se trouve dans l'espace de noms <xref:System.Windows.Markup> et l'assembly PresentationFramework. L'implémentation System.Xaml se trouve dans l'espace de noms <xref:System.Xaml> . En général, si vous utilisez des types WPF ou dérivez de types WPF, vous devez utiliser les implémentations WPF de <xref:System.Windows.Markup.XamlReader> et <xref:System.Windows.Markup.XamlWriter> , et non les implémentations System.Xaml. Pour plus d'informations, consultez la section Notes dans <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> et <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>.  
  
 Si vous incluez des références aux assemblys WPF et System.Xaml, et si vous utilisez également des instructions `include` pour les espaces de noms <xref:System.Windows.Markup> et <xref:System.Xaml> , vous devrez peut-être qualifier pleinement les appels à ces API afin de résoudre les types sans ambiguïté.  
  
## <a name="see-also"></a>Voir aussi  
 [Services XAML](../../../docs/framework/xaml-services/index.md)
