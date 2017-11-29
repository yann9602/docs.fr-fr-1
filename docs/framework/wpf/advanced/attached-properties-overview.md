---
title: "Vue d'ensemble des propriétés jointes"
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
helpviewer_keywords: attached properties [WPF Designer]
ms.assetid: 75928354-dc01-47e8-a018-8409aec1f32d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c33dc50d028dbe818d531ffac1d24b7152a2538
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="attached-properties-overview"></a>Vue d'ensemble des propriétés jointes
Une propriété jointe est un concept défini par XAML. Elle est conçue pour être utilisée comme un type de propriété globale qui peut être défini sur tout objet. Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], les propriétés jointes sont généralement définies comme une forme spécialisée de la propriété de dépendance qui n’a pas le « wrapper » de propriété classique.  
  
   
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Prérequis  
 Cette rubrique part du principe que vous savez ce que sont les propriétés de dépendance du point de vue d’un consommateur de propriétés de dépendance existantes sur les classes [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], et que vous avez lu la [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Pour suivre les exemples de cette rubrique, vous devez également comprendre XAML et savoir comment écrire des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
<a name="attached_properties_usage"></a>   
## <a name="why-use-attached-properties"></a>Pourquoi utiliser des propriétés jointes  
 Une des finalités d’une propriété jointe est de permettre à différents éléments enfants de spécifier des valeurs uniques pour une propriété définie en fait dans un élément parent. Une application spécifique de ce scénario est de faire en sorte que les éléments enfants informent l’élément parent sur la manière dont ils doivent être présentés dans l’[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Par exemple, le <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété. Le <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété est créée comme une propriété attachée, car il est conçu pour être défini sur des éléments qui sont contenus dans un <xref:System.Windows.Controls.DockPanel>, plutôt que sur <xref:System.Windows.Controls.DockPanel> lui-même. Le <xref:System.Windows.Controls.DockPanel> classe définit la méthode statique <xref:System.Windows.DependencyProperty> champ nommé <xref:System.Windows.Controls.DockPanel.DockProperty>et fournit le <xref:System.Windows.Controls.DockPanel.GetDock%2A> et <xref:System.Windows.Controls.DockPanel.SetDock%2A> méthodes que les accesseurs publics pour la propriété jointe.  
  
<a name="attached_properties_xaml"></a>   
## <a name="attached-properties-in-xaml"></a>Propriétés jointes en XAML  
 En XAML, vous définissez des propriétés jointes à l’aide de la syntaxe *FournisseurPropriétéJointe*.*NomPropriété*  
  
 Voici un exemple de comment vous pouvez définir <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> en XAML :  
  
 [!code-xaml[PropertiesOvwSupport#APBasicUsage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml#apbasicusage)]  
  
 Notez que l’utilisation est quelque peu similaire à une propriété statique ; vous toujours référencez au type <xref:System.Windows.Controls.DockPanel> qui possède et enregistre la propriété jointe, plutôt qu’à une instance quelconque spécifiée par nom.  
  
 En outre, comme une propriété jointe en XAML est un attribut que vous définissez dans le balisage, seule l’opération définie est pertinente. Vous ne pouvez pas obtenir directement une propriété en XAML, bien que des mécanismes indirects permettent de comparer des valeurs, telles que les déclencheurs dans les styles (pour plus d’informations, consultez [Application d’un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)).  
  
### <a name="attached-property-implementation-in-wpf"></a>Implémentation des propriétés jointes dans WPF  
 Dans [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], la plupart des propriétés jointes existant sur les types de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] liés à la présentation d’interface sont implémentées en tant que propriétés de dépendance. Les propriétés jointes sont un concept de XAML, tandis que les propriétés de dépendance sont un concept de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Étant donné que les propriétés jointes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont des propriétés de dépendance, elles prennent en charge les concepts de propriété de dépendance tels que les métadonnées de propriété, et les valeurs par défaut de ces métadonnées.  
  
<a name="howused"></a>   
## <a name="how-attached-properties-are-used-by-the-owning-type"></a>Comment les propriétés jointes sont utilisées par le type propriétaire  
 Bien que les propriétés jointes puissent être définies sur tout objet, cela ne signifie pas systématiquement que leur définition produira un résultat concret ou que leur valeur sera jamais utilisée par un autre objet. En général, les propriétés jointes sont utilisées pour que les objets provenant de diverses relations logiques ou hiérarchies de classes possibles puissent chacun communiquer des informations communes au type qui définit la propriété jointe. Le type qui définit la propriété jointe suit en général l’un de ces modèles :  
  
-   Le type qui définit la propriété jointe est conçu pour pouvoir être l’élément parent des éléments qui définiront les valeurs de la propriété jointe. Le type itère ensuite ses objets enfants par le biais de la logique interne au sein d’une structure d’objets arborescente, obtient les valeurs et agit sur elles.  
  
-   Le type qui définit la propriété jointe est utilisé comme élément enfant pour divers éléments parents et modèles de contenu possibles.  
  
-   Le type qui définit la propriété jointe représente un service. D’autres types définissent les valeurs de la propriété jointe. Quand l’élément qui définit la propriété est évalué dans le contexte du service, les valeurs de la propriété jointe sont obtenues par le biais de la logique interne de la classe de service.  
  
### <a name="an-example-of-a-parent-defined-attached-property"></a>Exemple d’une propriété jointe définie par le parent  
 Le scénario le plus courant dans lequel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit une propriété jointe est quand un élément parent prend en charge une collection d’éléments enfants, et implémente également un comportement dont les caractéristiques sont signalées individuellement pour chaque élément enfant.  
  
 <xref:System.Windows.Controls.DockPanel>définit le <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété attachée, et <xref:System.Windows.Controls.DockPanel> a le code au niveau de la classe dans le cadre de sa logique de rendu (en particulier, <xref:System.Windows.Controls.DockPanel.MeasureOverride%2A> et <xref:System.Windows.Controls.DockPanel.ArrangeOverride%2A>). A <xref:System.Windows.Controls.DockPanel> instance toujours vérifie si un de ses éléments enfants immédiats a défini une valeur pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>. Si tel est le cas, ces valeurs sont entrées pour la logique de rendu appliquée à l’élément enfant en question. Imbriqué <xref:System.Windows.Controls.DockPanel> instances chaque traitent leurs propres collections d’éléments enfants immédiats, mais ce comportement est spécifique à l’implémentation à la manière dont <xref:System.Windows.Controls.DockPanel> processus <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> valeurs. Il est théoriquement possible d’avoir des propriétés jointes qui influent sur les éléments au-delà du parent immédiat. Si le <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> propriété jointe est définie sur un élément qui n’a aucun <xref:System.Windows.Controls.DockPanel> élément parent sur lequel agir, aucune erreur ou exception est levée. Cela signifie simplement qu’une valeur de propriété globale a été définie, mais elle n’a actuellement aucun <xref:System.Windows.Controls.DockPanel> parent peut consommer les informations.  
  
<a name="attached_properties_code"></a>   
## <a name="attached-properties-in-code"></a>Propriétés jointes dans le code  
 Les propriétés jointes dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n’ont pas les méthodes de « wrapper » [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typiques qui facilitent la définition/l’obtention de l’accès. Cela est dû au fait que la propriété jointe ne fait pas nécessairement partie de l’espace de noms [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour les instances dans lesquelles est définie la propriété. Toutefois, un processeur XAML doit pouvoir définir ces valeurs quand XAML est analysé. Pour prendre en charge une utilisation efficace de la propriété jointe, le type de propriétaire de la propriété jointe doit implémenter des méthodes d’accesseur dédiées de la forme `Get`*NomPropriété* et `Set`*NomPropriété*. Ces méthodes d’accesseur dédiées sont également utiles pour obtenir ou définir la propriété jointe dans le code. Du point de vue du code, une propriété jointe s’apparente à un champ de stockage comportant des accesseurs de méthode au lieu d’accesseurs de propriété, et ce champ de stockage peut exister sur tout objet plutôt que devoir être défini de manière spécifique.  
  
 L’exemple suivant illustre la définition d’une propriété jointe dans le code. Dans cet exemple, `myCheckBox` est une instance de la <xref:System.Windows.Controls.CheckBox> classe.  
  
 [!code-csharp[PropertiesOvwSupport#APCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page4.xaml.cs#apcode)]
 [!code-vb[PropertiesOvwSupport#APCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page4.xaml.vb#apcode)]  
  
 Comme le code XAML dans le cas, si `myCheckBox` n’a pas déjà été ajouté en tant qu’élément enfant de `myDockPanel` par la troisième ligne de code, la quatrième ligne du code ne déclenchera pas d’exception, mais la valeur de propriété n’est pas interagir avec un <xref:System.Windows.Controls.DockPanel> parent et par conséquent faites rien. Uniquement un <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> a sur un élément enfant combiné à la présence de valeur un <xref:System.Windows.Controls.DockPanel> élément parent entraîne un comportement effectif dans l’application rendue. (Dans ce cas, vous pourriez définir la propriété jointe, puis la joindre à l’arborescence. Vous pourriez également joindre la propriété à l’arborescence, puis la définir. Le résultat est le même, quel que soit l’ordre des actions.)  
  
<a name="attached_properties_metadata"></a>   
## <a name="attached-property-metadata"></a>Métadonnées de propriété jointe  
 Lors de l’inscription de la propriété <xref:System.Windows.FrameworkPropertyMetadata> est définie pour spécifier les caractéristiques de la propriété, par exemple si la propriété affecte le rendu, de mesure et ainsi de suite. Les métadonnées d’une propriété jointe sont en général identiques à celles d’une propriété de dépendance. Si vous spécifiez une valeur par défaut dans une substitution des métadonnées d’une propriété jointe, cette valeur devient la valeur par défaut de la propriété jointe implicite sur les instances de la classe de substitution. Spécifiquement, votre valeur par défaut est signalée si un processus demande la valeur d’une propriété jointe par le biais de l’accesseur de méthode `Get` de cette propriété, en spécifiant une instance de la classe dans laquelle vous avez indiqué les métadonnées, et si la valeur de cette propriété jointe n’était autrement pas définie.  
  
 Si vous souhaitez activer l’héritage des valeurs de propriété sur une propriété, vous devez utiliser des propriétés jointes plutôt que des propriétés de dépendance non jointes. Pour plus d’informations, consultez [Héritage de la valeur de propriété](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
<a name="custom"></a>   
## <a name="custom-attached-properties"></a>Propriétés jointes personnalisées  
  
<a name="create_attached_properties"></a>   
### <a name="when-to-create-an-attached-property"></a>Quand créer une propriété jointe  
 Vous pouvez créer une propriété jointe si un mécanisme de définition de propriété doit être disponible pour les classes autres que la classe de définition. Le scénario le plus courant à cette fin est la mise en page. Exemples de propriétés de disposition existantes sont <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType>, et <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType>. Le scénario activé ici implique que les éléments existant comme éléments enfants sur les éléments contrôlant la mise en page sont en mesure d’exprimer individuellement des spécifications de mise en page à leurs éléments parents de mise en page et chacun d’eux définit une valeur de propriété configurée par le parent en tant que propriété jointe.  
  
 Un autre scénario illustrant l’utilisation d’une propriété jointe s’applique quand votre classe représente un service et que vous voulez que les classes soient en mesure d’intégrer le service avec une plus grande transparence.  
  
 Un autre scénario encore consiste à bénéficier de la prise en charge du [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] de [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], par exemple l’édition de la fenêtre **Propriétés**. Pour plus d’informations, consultez [Vue d’ensemble de la création de contrôles](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Comme mentionné précédemment, vous devez enregistrer une propriété jointe si vous souhaitez utiliser l’héritage des valeurs de propriété.  
  
<a name="how_do_i_create_attached_properties"></a>   
### <a name="how-to-create-an-attached-property"></a>Comment créer une propriété jointe  
 Si votre classe définit la propriété jointe strictement pour une utilisation sur d’autres types, alors que la classe n’a pas dériver de <xref:System.Windows.DependencyObject>. Mais vous n’avez pas besoin de dériver de <xref:System.Windows.DependencyObject> si vous suivez globaux [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modèle de votre propriété jointe est également une propriété de dépendance.  
  
 Définissez votre propriété jointe comme une propriété de dépendance en déclarant un `public` `static` `readonly` champ de type <xref:System.Windows.DependencyProperty>. Vous définissez ce champ à l’aide de la valeur de retour de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> (méthode). Le nom du champ doit correspondre au nom de la propriété jointe, auquel s’ajoute la chaîne `Property`, pour suivre le modèle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] établi de dénomination des champs d’identification par rapport aux propriétés représentées. Le fournisseur de propriétés jointes doit également fournir des méthodes statiques `Get`*NomPropriété* et `Set`*NomPropriété* comme accesseurs de la propriété jointe pour que le système de propriétés puisse utiliser celle-ci.  
  
> [!NOTE]
>  Si vous omettez l’accesseur get de la propriété jointe, la liaison de données sur la propriété ne fonctionne pas dans les outils de conception, tels que [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] et Expression Blend.  
  
#### <a name="the-get-accessor"></a>Accesseur Get  
 La signature pour l’accesseur `Get`*NomPropriété* doit être :  
  
 `public static object Get` *NomPropriété* `(object`  `target` `)`  
  
-   L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, le <xref:System.Windows.Controls.DockPanel.GetDock%2A?displayProperty=nameWithType> le paramètre en tant que types de méthode <xref:System.Windows.UIElement>, car la propriété jointe est uniquement destinée à être définie sur <xref:System.Windows.UIElement> instances.  
  
-   La valeur de retour peut être spécifiée comme un type plus spécifique dans votre implémentation. Par exemple, le <xref:System.Windows.Controls.DockPanel.GetDock%2A> en tant que méthode tape <xref:System.Windows.Controls.Dock>, car la valeur peut être uniquement cette énumération.  
  
#### <a name="the-set-accessor"></a>Accesseur Set  
 La signature pour l’accesseur `Set`*NomPropriété* doit être :  
  
 `public static void Set` *NomPropriété* `(object`  `target` `, object`  `value` `)`  
  
-   L’objet `target` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, le <xref:System.Windows.Controls.DockPanel.SetDock%2A> en tant que méthode tape <xref:System.Windows.UIElement>, car la propriété jointe est uniquement destinée à être définie sur <xref:System.Windows.UIElement> instances.  
  
-   L’objet `value` peut être défini comme un type plus spécifique dans votre implémentation. Par exemple, le <xref:System.Windows.Controls.DockPanel.SetDock%2A> en tant que méthode tape <xref:System.Windows.Controls.Dock>, car la valeur peut être uniquement cette énumération. N’oubliez pas que la valeur de cette méthode est l’entrée provenant du chargeur XAML quand il rencontre votre propriété jointe dans une utilisation des propriétés jointes dans le balisage. Cette entrée est la valeur spécifiée comme valeur d’attribut XAML dans le balisage. Ainsi, la conversion de type, la sérialisation de valeur ou l’extension de balisage doit être prise en charge pour le type utilisé afin que le type approprié puisse être créé à partir de la valeur d’attribut (laquelle est en fin de compte une simple chaîne).  
  
 L’exemple suivant illustre l’enregistrement de propriété de dépendance (à l’aide de la <xref:System.Windows.DependencyProperty.RegisterAttached%2A> méthode), ainsi que le `Get` *PropertyName* et `Set` *PropertyName* accesseurs . Dans cet exemple, le nom de la propriété jointe est `IsBubbleSource`. Les accesseurs doivent donc être nommés `GetIsBubbleSource` et `SetIsBubbleSource`.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
#### <a name="attached-property-attributes"></a>Attributs des propriétés jointes  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit plusieurs [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] qui doivent fournir des informations sur les propriétés jointes aux processus de réflexion et aux utilisateurs typiques des informations de réflexion et de propriété, tels que les concepteurs. Les propriétés jointes ayant un type de portée illimitée, les concepteurs ont besoin d’un moyen d’éviter que les utilisateurs croulent sous une liste globale de toutes les propriétés jointes qui sont définies dans l’implémentation d’une technologie particulière utilisant XAML. Vous pouvez utiliser les [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] définit pour les propriétés jointes pour déterminer les cas où une propriété jointe donnée doit être affichée dans une fenêtre de propriétés. Vous pouvez également envisager l’application de ces attributs à vos propres propriétés jointes personnalisées. La finalité et la syntaxe des [!INCLUDE[TLA2#tla_netframewkattr#plural](../../../../includes/tla2sharptla-netframewkattrsharpplural-md.md)] sont décrites dans les pages de référence appropriées :  
  
-   <xref:System.Windows.AttachedPropertyBrowsableAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForChildrenAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableForTypeAttribute>  
  
-   <xref:System.Windows.AttachedPropertyBrowsableWhenAttributePresentAttribute>  
  
<a name="more"></a>   
## <a name="learning-more-about-attached-properties"></a>En savoir plus sur les propriétés jointes  
  
-   Pour plus d’informations sur la création d’une propriété jointe, consultez [Enregistrer une propriété jointe](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md).  
  
-   Pour obtenir des scénarios d’usage avancés des propriétés de dépendance et des propriétés jointes, consultez [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
-   Vous pouvez également enregistrer une propriété en tant que propriété jointe et que propriété de dépendance ; mais dans cette situation, vous exposez encore les implémentations de « wrapper ». Dans ce cas, vous pouvez définir la propriété soit sur cet élément, soit sur tout élément par le biais de la syntaxe de propriété jointe XAML. Est un exemple d’une propriété avec un scénario approprié pour des utilisations standard et attachée <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Windows.DependencyProperty>  
 [Vue d’ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Vue d’ensemble du langage XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [Enregistrer une propriété jointe](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)
