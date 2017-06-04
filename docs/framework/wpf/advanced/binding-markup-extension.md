---
title: "Binding, extension de balisage | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Binding"
helpviewer_keywords: 
  - "Binding (extensions de balisage)"
  - "XAML, Binding (extension de balisage)"
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: 23
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 23
---
# Binding, extension de balisage
Accepte une valeur de propriété comme valeur liée aux données, en créant un objet d'expression et interprétant le contexte de données qui s'applique à l'élément et à ses liaisons au moment de l'exécution.  
  
## Utilisation de l'expression Binding  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## Remarques sur la syntaxe  
 Dans ces syntaxes, `[]` et `*` ne sont pas littéraux.  Ils représentent une partie d'une notation indiquant que zéro ou plusieurs paires *bindProp*`=`*valeur* peuvent être utilisées, avec un séparateur `,` entre elles et les paires *bindProp*`=`*value* précédentes.  
  
 Toute propriété répertoriée dans la section « Propriétés Binding pouvant être définies avec l'extension Binding » peut être définie à la place à l'aide des attributs d'un élément objet <xref:System.Windows.Data.Binding>.  Toutefois, il ne s'agit pas de l'utilisation d'extension de marquage réelle de <xref:System.Windows.Data.Binding>. Il s'agit juste du traitement XAML général des attributs qui définissent les propriétés de la classe <xref:System.Windows.Data.Binding> du CLR.  En d'autres termes, `<Binding` *bindProp1*`="`*valeur1*`"[` *bindPropN*`="`*valeurN*`"]*/>` est une syntaxe équivalente pour les attributs <xref:System.Windows.Data.Binding> des éléments objet en remplacement de l'utilisation d'une expression `Binding`.  Pour en savoir plus sur l'utilisation des attributs XAML par les propriétés spécifiques de <xref:System.Windows.Data.Binding>, consultez la section « Utilisation des attributs XAML » de la propriété correspondante de <xref:System.Windows.Data.Binding> dans la bibliothèque de classes .NET Framework.  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Nom de la propriété <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.BindingBase> à définir.  Toutes les propriétés <xref:System.Windows.Data.Binding> ne peuvent pas être définies avec l'extension `Binding`, et certaines propriétés peuvent être définies uniquement dans une expression `Binding` à l'aide d'extensions de balisage imbriquées supplémentaires.  Consultez la section « Propriétés Binding pouvant être définies avec l'extension Binding ».|  
|`value1, valueN`|Valeur à attribuer à la propriété.  La gestion de la valeur d'attribut est en définitive spécifique au type et à la logique de la propriété <xref:System.Windows.Data.Binding> spécifique en cours de définition.|  
|`path`|Chaîne de chemin d'accès qui définit la propriété <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> implicite.  Voir aussi [PropertyPath, syntaxe XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## {Binding} non qualifié  
 L'utilisation de `{Binding}` présentée dans « Utilisation de l'expression Binding » Utilisation » crée un objet <xref:System.Windows.Data.Binding> avec les valeurs par défaut, qui inclut un <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> initial de `null`.  Ceci est encore utile dans de nombreux scénarios, étant donné que le <xref:System.Windows.Data.Binding> créé peut reposer sur des propriétés de liaison de données clés telles que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> et <xref:System.Windows.Data.Binding.Source%2A?displayProperty=fullName> qui sont définies dans le contexte d'exécution.  Pour plus d'informations sur le concept de contexte de données, consultez [Liaison de données](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## Chemin d'accès implicite  
 L'extension de balisage `Binding` utilise <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> en tant que « propriété par défaut » conceptuelle, où `Path=` n'a pas besoin d'être affiché dans l'expression.  Si vous spécifiez une expression `Binding` avec un chemin d'accès implicite, le chemin d'accès implicite doit s'afficher en premier dans l'expression, avant tout autre paire `bindProp`\=`value` où la propriété <xref:System.Windows.Data.Binding> est spécifiée par son nom.  Par exemple, `{Binding PathString}`, où `PathString` est une chaîne évaluée comme étant la valeur de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> dans le <xref:System.Windows.Data.Binding> créé par l'utilisation d'une extension de balisage.  Vous pouvez ajouter un chemin d'accès implicite à d'autres propriétés nommées après le séparateur de virgule, par exemple, `{Binding LastName, Mode=TwoWay}`.  
  
## Propriétés Binding pouvant être définies avec l'extension Binding  
 La syntaxe présentée dans cette rubrique utilise l'approximation `bindProp`\=`value` générique, car il existe de nombreuses propriétés en lecture\/écriture de <xref:System.Windows.Data.BindingBase> ou <xref:System.Windows.Data.Binding> qui peuvent être définies par le biais de la syntaxe d'expression \/ d'extension de balisage `Binding`.  Elles peuvent être définies dans n'importe quel ordre, à l'exception du <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName> implicite.  \(Vous avez la possibilité de spécifier `Path=`explicitement, auquel cas il peut également être défini dans n'importe quel ordre\).  Fondamentalement, vous pouvez ne définir aucune propriété ou définir plusieurs propriété dans la liste ci\-dessous, en utilisant des paires `bindProp`\=`value` séparées par des virgules.  
  
 Plusieurs de ces valeurs de propriétés nécessitent des types d'objet qui ne prennent pas en charge une conversion de type native d'une syntaxe texte en XAML, et requièrent par conséquent la définition d'extensions de balisage en tant que valeur d'attribut.  Consultez la section Utilisation des attributs XAML de la bibliothèque de classes .NET Framework pour en savoir plus sur chaque propriété ; la chaîne que vous utilisez pour la syntaxe des attributs XAML avec ou sans utilisation d'une extension de balisage supplémentaire est foncièrement identique à la valeur vous spécifiez dans une expression `Binding`, à ceci près que vous ne placez pas de guillemets autour de chaque `bindProp`\=`value` dans l'expression `Binding`.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A> : chaîne qui identifie un groupe de liaison possible.  Il s'agit d'un concept de liaison relativement avancé ; consultez la page de référence de <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A> : peut être défini en tant que chaîne `bindProp`\=`value` dans l'expression, mais pour ce faire, requiert une référence d'objet pour la valeur, par exemple [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  La valeur dans cette casse est une instance d'une classe de convertisseur personnalisée.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A> : définissable dans l'expression en tant qu'identificateur basé sur les normes ; consultez la rubrique de référence de <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A> : peut être défini en tant que chaîne `bindProp`\=`value` dans l'expression, mais en fonction du type du paramètre passé.  Si vous passez un type référence pour la valeur, cette utilisation nécessite une référence d'objet telle qu'un [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) imbriqué.  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A> : mutuellement exclusif avec <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.Source%2A> ; chacune de ces propriétés représente une méthodologie de liaison spécifique.  Consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A> : peut être défini en tant que chaîne `bindProp`\=`value` dans l'expression, mais en fonction du type de la valeur passée.  Si vous passez un type référence, nécessite une référence d'objet telle qu'un [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) imbriqué.  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A> : *valeur* est un nom constant issu de l'énumération <xref:System.Windows.Data.BindingMode>.  Par exemple, `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A> : chaîne qui décrit un chemin d'accès vers un objet de données ou un modèle objet général.  Le format fournit plusieurs conventions différentes pour parcourir un modèle objet qui ne peuvent pas être décrites correctement ici.  Consultez [PropertyPath, syntaxe XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A> : mutuellement exclusif avec <xref:System.Windows.Data.Binding.ElementName%2A> et <xref:System.Windows.Data.Binding.Source%2A> ; chacune de ces propriétés de liaison représente une méthodologie de liaison spécifique.  Consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  Requiert l'utilisation d'une [RelativeSource, extension de balisage](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) imbriquée pour spécifier la valeur.  
  
-   <xref:System.Windows.Data.Binding.Source%2A> : mutuellement exclusif avec <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.ElementName%2A> ; chacune de ces propriétés représente une méthodologie de liaison spécifique.  Consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  Requiert l'utilisation d'une extension imbriquée, généralement une [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) qui fait référence à une source de données d'objet d'un dictionnaire de ressources de clé.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A> : chaîne qui décrit une convention de format de chaîne pour les données liées.  Il s'agit d'un concept de liaison relativement avancé ; consultez la page de référence de <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A> : peut être défini en tant que chaîne `bindProp`\=`value` dans l'expression, mais en fonction du type du paramètre passé.  Si vous passez un type référence pour la valeur, nécessite une référence d'objet telle qu'un [StaticResource, extension de balisage](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) imbriqué.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> : *valeur* est un nom constant issu de l'énumération <xref:System.Windows.Data.UpdateSourceTrigger>.  Par exemple, `{Binding UpdateSourceTrigger=LostFocus}`.  Les contrôles spécifiques ont potentiellement des valeurs par défaut différentes pour cette propriété de liaison.  Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  Consultez la section Notes.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> : valeur booléenne, peut être `true` ou `false`.  La valeur par défaut est `false`.  Consultez la section Notes.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A> : chaîne qui décrit un chemin d'accès vers le XMLDOM d'une source de données XML.  Consultez [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Les propriétés suivantes sont des propriétés <xref:System.Windows.Data.Binding> qui ne peuvent pas être définies à l'aide de l'extension de balisage `Binding`\/forme d'expression `{Binding}`.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> : cette propriété attend une référence à une implémentation de rappel.  Les rappels\/méthodes autres que les gestionnaires d'événements ne peuvent pas être référencés dans la syntaxe XAML.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A> : la propriété prend une collecte générique des objets <xref:System.Windows.Controls.ValidationRule>.  Cette syntaxe pourrait être exprimée comme un élément de propriété dans un élément objet <xref:System.Windows.Data.Binding>. Toutefois, aucune technique d'analyse d'attributs n'est disponible pour l'utilisation dans une expression `Binding`.  Consultez la rubrique de référence pour <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## Notes  
  
> [!IMPORTANT]
>  En termes de priorité des propriétés de dépendance, une expression `Binding` est équivalente à une valeur définie localement.  Si vous définissez une valeur locale pour une propriété qui avait précédemment une expression `Binding`,  `Binding` est supprimée complètement.  Pour plus d'informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 La description de la liaison de données à un niveau de base n'est pas couverte dans cette rubrique.  Consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding> ne prennent pas en charge une syntaxe d'extension [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Vous pouvez utiliser à la place des éléments de propriété.  Consultez les rubriques de référence pour <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding>.  
  
 Les valeurs booléennes pour XAML ne respectent pas la casse.  Par exemple, vous pourriez spécifier `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Les liaisons qui impliquent la validation des données sont spécifiées en général par un élément `Binding` explicite plutôt que comme une expression `{Binding ...}`, et la définition de  <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> dans une expression est rare.  C'est parce que la propriété auxiliaire <xref:System.Windows.Data.Binding.ValidationRules%2A> ne peut pas être définie facilement dans le formulaire d'expression.  Pour plus d'informations, consultez [Implémenter la validation de la liaison](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding` est une extension de balisage.  En règle générale, les extensions de balisage sont implémentées quand il est nécessaire que les valeurs d'attribut soient autre chose que des valeurs littérales ou des noms de gestionnaire, et que l'exigence est plus globale que le simple fait d'attribuer des convertisseurs de type sur certains types ou propriétés.  En XAML, toutes les extensions de balisage utilisent les caractères `{` et `}` dans leur syntaxe d'attributs, convention selon laquelle un processeur XAML reconnaît qu'une extension de balisage doit traiter le contenu de la chaîne.  Pour plus d'informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding` est une extension de balisage atypique dans la mesure où la classe <xref:System.Windows.Data.Binding> qui implémente les fonctionnalités d'extension pour l'implémentation XAML WPF implémente également plusieurs autres méthodes et propriétés qui ne sont pas liées au XAML.  Les autres membres sont destinés à faire de <xref:System.Windows.Data.Binding> une classe plus autonome et polyvalente pouvant traiter de nombreux scénarios de liaison de données en plus de fonctionner en tant qu'extension de balisage XAML.  
  
## Voir aussi  
 <xref:System.Windows.Data.Binding>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble du langage XAML \(WPF\)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)