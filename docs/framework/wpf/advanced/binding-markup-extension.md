---
title: Binding, extension de balisage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d2bbca799e1eda1abae3d199dd71e004b17c4c9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="binding-markup-extension"></a>Binding, extension de balisage
Diffère d’une valeur de propriété une valeur liée aux données, création d’un objet d’expression et interprétant le contexte de données qui s’applique à l’élément et ses liaisons au moment de l’exécution.  
  
## <a name="binding-expression-usage"></a>Utilisation d’expressions de liaison  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>Remarques sur la syntaxe  
 Dans ces syntaxes, la `[]` et `*` ne sont pas des littéraux. Elles font partie d’une notation indiquant que zéro ou plusieurs *bindProp*`=`*valeur* paires peuvent être utilisées, avec un `,` séparateur entre elles et précédent *bindProp*  `=` *valeur* paires.  
  
 Toute des propriétés répertoriées dans la section « Liaison de propriétés que peut être définie avec l’Extension Binding » à la place peut être définie à l’aide des attributs d’un <xref:System.Windows.Data.Binding> élément objet. Toutefois, qui n’est pas réellement l’extension de balisage de <xref:System.Windows.Data.Binding>, il est simplement le traitement XAML général d’attributs qui définissent les propriétés du CLR <xref:System.Windows.Data.Binding> classe. En d’autres termes, `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*valeurN* `"]*/>` est une syntaxe équivalente pour les attributs de <xref:System.Windows.Data.Binding> utilisation de l’élément à la place de l’objet un `Binding` utilisation de l’expression. Pour en savoir plus sur l’utilisation d’attributs XAML des propriétés spécifiques de <xref:System.Windows.Data.Binding>, consultez la section « Utilisation d’attributs XAML » de la propriété correspondante de <xref:System.Windows.Data.Binding> dans la bibliothèque de classes .NET Framework.  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|Le nom de la <xref:System.Windows.Data.Binding> ou <xref:System.Windows.Data.BindingBase> propriété à définir. Pas toutes <xref:System.Windows.Data.Binding> propriétés peuvent être définies avec la `Binding` extension et certaines propriétés peuvent être définies au sein d’un `Binding` expression uniquement à l’aide supplémentaire des extensions de balisage imbriquées. Consultez la section « Liaison de propriétés que peut être définie avec l’Extension Binding ».|  
|`value1, valueN`|Valeur à affecter à la propriété. La gestion de la valeur d’attribut est en définitive spécifique au type et une logique spécifique <xref:System.Windows.Data.Binding> propriété définie.|  
|`path`|La chaîne de chemin d’accès qui définit l’implicite <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> propriété. Voir aussi [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).|  
  
## <a name="unqualified-binding"></a>{Binding} non qualifié  
 Le `{Binding}` utilisation indiqué dans « Utilisation de Binding Expression » crée un <xref:System.Windows.Data.Binding> de l’objet avec les valeurs par défaut, qui comprend une initiale <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> de `null`. Ceci est encore utile dans de nombreux scénarios, étant donné que créé <xref:System.Windows.Data.Binding> peut reposer sur les propriétés de liaison de données clés telles que <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> et <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> définie dans le contexte de données de l’exécution. Pour plus d’informations sur le concept de contexte de données, consultez [une liaison de données](../../../../docs/framework/wpf/data/data-binding-wpf.md).  
  
## <a name="implicit-path"></a>Chemin d’accès implicite  
 Le `Binding` utilisations d’extension de balisage <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> comme un « propriété par défaut », où `Path=` sans devoir s’affichent dans l’expression. Si vous spécifiez un `Binding` expression avec un chemin d’accès implicite, le chemin d’accès implicite doit apparaître en premier dans l’expression, avant tout autre `bindProp` = `value` paires où le <xref:System.Windows.Data.Binding> propriété est spécifiée par nom. Par exemple : `{Binding PathString}`, où `PathString` est une chaîne qui est évaluée à la valeur de <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> dans les <xref:System.Windows.Data.Binding> créés par l’extension de balisage. Vous pouvez ajouter un chemin d’accès implicite à d’autres propriétés nommées après le séparateur de virgule, par exemple, `{Binding LastName, Mode=TwoWay}`.  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>Propriétés de liaison qui peuvent être définies avec l’Extension de liaison  
 La syntaxe présentée dans cette rubrique utilise le type générique `bindProp` = `value` approximation, car il existe de nombreuses propriétés en lecture/écriture de <xref:System.Windows.Data.BindingBase> ou <xref:System.Windows.Data.Binding> qui peut être défini via le `Binding` extension de balisage / syntaxe d’expression. Ils peuvent être définies dans n’importe quel ordre, à l’exception d’implicite <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>. (Vous pouvez spécifier explicitement `Path=`, auquel cas elle peut être définie dans n’importe quel ordre). En fait, vous pouvez définir zéro ou plusieurs des propriétés dans la liste ci-dessous, à l’aide de `bindProp` = `value` paires séparées par des virgules.  
  
 Plusieurs de ces valeurs de propriété nécessitent des types d’objets qui ne prennent pas une conversion de type natif à partir d’une syntaxe de texte en XAML et nécessitent donc des extensions de balisage pour pouvoir être définie comme valeur d’attribut. Consultez la section Utilisation d’attributs XAML dans la bibliothèque de classes .NET Framework pour chaque propriété pour plus d’informations ; la chaîne que vous utilisez pour la syntaxe d’attribut XAML avec ou sans l’extension de balisage supplémentaire utilisation est essentiellement identique à la valeur que vous spécifiez dans un `Binding` expression, à l’exception que vous ne placez pas de guillemets autour de chaque `bindProp` = `value` dans le `Binding` expression.  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: chaîne qui identifie un groupe de liaison possible. Il s’agit d’un concept de liaison relativement avancé ; consultez la page de référence de <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>.  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: peut être défini comme un `bindProp` = `value` chaîne dans l’expression, mais pour ce faire requiert une référence d’objet pour la valeur, par exemple un [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md). Dans ce cas, la valeur est une instance d’une classe de convertisseur personnalisé.  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: définissable dans l’expression en tant qu’un identificateur de normes ; consultez la rubrique de référence <xref:System.Windows.Data.Binding.ConverterCulture%2A>.  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: peut être défini comme un `bindProp` = `value` chaîne dans l’expression, mais il est dépendant du type de paramètre passé. Si vous passez un type de référence pour la valeur, cette utilisation nécessite une référence d’objet tels qu’imbriquée [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: mutuellement exclusif <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.Source%2A>; chaque de ces propriétés de liaison représente une méthodologie de liaison spécifique. Consultez [vue d’ensemble de liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: peut être défini comme un `bindProp` = `value` chaîne dans l’expression, mais il est dépendant du type de la valeur passée. Si vous passez un type référence, nécessite une référence d’objet tels qu’imbriquée [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>: *valeur* est un nom de constante à partir de la <xref:System.Windows.Data.BindingMode> énumération. Par exemple, `{Binding Mode=OneWay}`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`.  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: chaîne qui décrit un chemin d’accès dans un objet de données ou un modèle objet général. Le format fournit plusieurs conventions différentes pour parcourir un modèle d’objet ne peut pas être correctement décrits dans cette rubrique. Consultez [syntaxe PropertyPath XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md).  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: mutuellement exclusif avec <xref:System.Windows.Data.Binding.ElementName%2A> et <xref:System.Windows.Data.Binding.Source%2A>; chaque de ces propriétés de liaison représente une méthodologie de liaison spécifique. Consultez [vue d’ensemble de liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md). Nécessite un imbriquée [RelativeSource MarkupExtension](../../../../docs/framework/wpf/advanced/relativesource-markupextension.md) utilisation pour spécifier la valeur.  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: mutuellement exclusif <xref:System.Windows.Data.Binding.RelativeSource%2A> et <xref:System.Windows.Data.Binding.ElementName%2A>; chaque de ces propriétés de liaison représente une méthodologie de liaison spécifique. Consultez [vue d’ensemble de liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md). Requiert qu’une utilisation de l’extension imbriquée, généralement une [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) qui fait référence à une objet source de données à partir d’un dictionnaire de ressources de clé.  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: chaîne qui décrit une convention de format de chaîne pour les données liées. Il s’agit d’un concept de liaison relativement avancé ; consultez la page de référence de <xref:System.Windows.Data.BindingBase.StringFormat%2A>.  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: peut être défini comme un `bindProp` = `value` chaîne dans l’expression, mais il est dépendant du type de paramètre passé. Si vous passez un type référence pour la valeur, nécessite une référence d’objet tels qu’imbriquée [StaticResource Markup Extension](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>: *valeur* est un nom de constante à partir de la <xref:System.Windows.Data.UpdateSourceTrigger> énumération. Par exemple, `{Binding UpdateSourceTrigger=LostFocus}`. Contrôles spécifiques ont potentiellement des valeurs par défaut différentes pour cette propriété de liaison. Consultez <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`. Consultez la section Notes.  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>: Valeur booléenne, peut être `true` ou `false`. La valeur par défaut est `false`. Consultez la section Notes.  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: chaîne qui décrit un chemin d’accès vers le XMLDOM d’une source de données XML. Consultez [lier aux données XML à l’aide d’un XMLDataProvider et requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Les éléments suivants sont des propriétés de <xref:System.Windows.Data.Binding> qui ne peut pas être définie à l’aide de la `Binding` extension de balisage /`{Binding}` forme d’expression.  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: cette propriété attend une référence à une implémentation de rappel. Rappels/méthodes autres que des gestionnaires d’événements ne peut pas être référencés dans la syntaxe XAML.  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: la propriété est une collection générique de <xref:System.Windows.Controls.ValidationRule> objets. Cela peut être exprimée sous la forme d’un élément de propriété dans un <xref:System.Windows.Data.Binding> élément objet, mais n’a aucune technique d’analyse de l’attribut disponible pour une utilisation dans un `Binding` expression. Consultez la rubrique de référence pour <xref:System.Windows.Data.Binding.ValidationRules%2A>.  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
>  En termes de la propriété de dépendance, un `Binding` expression est équivalente à définie localement valeur. Si vous définissez une valeur locale pour une propriété qui avait précédemment une `Binding` expression, le `Binding` est entièrement supprimée. Pour plus d’informations, consultez [Priorité de la valeur de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md).  
  
 Description de la liaison de données à un niveau de base n’est pas abordé dans cette rubrique. Consultez [vue d’ensemble de liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding>et <xref:System.Windows.Data.PriorityBinding> ne gèrent pas un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] syntaxe d’extension. Vous devez utiliser à la place des éléments de propriété. Consultez les rubriques de référence pour <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding>.  
  
 Des valeurs booléennes pour XAML ne sont pas la casse. Par exemple, vous pourriez spécifier `{Binding NotifyOnValidationError=true}` ou `{Binding NotifyOnValidationError=True}`.  
  
 Les liaisons qui impliquent la validation des données sont généralement spécifiées par explicite `Binding` élément plutôt que comme un `{Binding ...}` expression et paramètre <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> ou <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> dans une expression est rare. C’est parce que la propriété <xref:System.Windows.Data.Binding.ValidationRules%2A> ne peut pas être définie facilement dans le formulaire d’expression. Pour plus d’informations, consultez [Implement Binding Validation](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md).  
  
 `Binding` est une extension de balisage. Les extensions de balisage sont généralement implémentées quand il est nécessaire pour éviter que les valeurs d’attribut pour être des noms autres que des valeurs littérales ou du gestionnaire et l’exigence est plus globale que les convertisseurs de type attribués sur certains types ou propriétés. Toutes les extensions de balisage en cours d’utilisation XAML le `{` et `}` caractères dans leur syntaxe d’attribut, qui est la convention selon laquelle un processeur XAML reconnaît qu’une extension de balisage doit traiter le contenu de la chaîne. Pour plus d’informations, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 `Binding`est une extension de balisage atypique dans qui la <xref:System.Windows.Data.Binding> classe qui implémente la fonctionnalité d’extension pour l’implémentation XAML WPF implémente également plusieurs autres méthodes et propriétés qui ne sont pas liées au XAML. Les autres membres sont destinés à faire <xref:System.Windows.Data.Binding> une classe plus autonome et polyvalente que peut traiter de nombreux scénarios de liaison de données en plus de fonctionner comme une extension de balisage XAML.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.Data.Binding>  
 [Vue d’ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
