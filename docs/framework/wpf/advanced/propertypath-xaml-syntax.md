---
title: "PropertyPath, syntaxe XAML | Microsoft Docs"
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
  - "PropertyPath (objet)"
  - "XAML, PropertyPath (objet)"
ms.assetid: 0e3cdf07-abe6-460a-a9af-3764b4fd707f
caps.latest.revision: 24
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# PropertyPath, syntaxe XAML
L'objet <xref:System.Windows.PropertyPath> prend en charge une syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] inline complexe pour définir différentes propriétés qui acceptent le type <xref:System.Windows.PropertyPath> comme valeur.  Cette rubrique décrit la syntaxe <xref:System.Windows.PropertyPath> telle qu'elle est appliquée aux syntaxes de liaison et d'animation.  
  
   
  
<a name="where"></a>   
## Cas d'emploi de PropertyPath  
 <xref:System.Windows.PropertyPath> est un objet commun utilisé dans plusieurs fonctionnalités de [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Malgré l'utilisation du <xref:System.Windows.PropertyPath> commun pour communiquer les informations de chemin de propriété, les utilisations varient pour chaque domaine de fonctionnalités où <xref:System.Windows.PropertyPath> est utilisé comme type.  Par conséquent, il s'avère plus pratique de documenter les syntaxes pour chaque fonctionnalité.  
  
 À l'origine, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise <xref:System.Windows.PropertyPath> pour décrire les chemins de modèle objet permettant de parcourir les propriétés d'une source de données d'objet, ainsi que pour décrire le chemin d'accès cible pour les animations ciblées.  
  
 Certaines propriétés de style et de modèle telles que <xref:System.Windows.Setter.Property%2A?displayProperty=fullName> prennent un nom de propriété qualifié qui ressemble en apparence à <xref:System.Windows.PropertyPath>.  Il ne s'agit toutefois pas d'un vrai <xref:System.Windows.PropertyPath>, mais plutôt d'une utilisation au format de chaîne *owner.property* qualifiée activée par le processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] WPF en association avec le convertisseur de type pour <xref:System.Windows.DependencyProperty>.  
  
<a name="databinding_s"></a>   
## PropertyPath pour les objets dans la liaison de données  
 La liaison de données est une fonctionnalité de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui permet de créer une liaison vers la valeur cible d'une [propriété de dépendance](GTMT).  Toutefois, la source d'une liaison de données ne doit pas nécessairement être une [propriété de dépendance](GTMT). Il peut en effet s'agir de n'importe quel type de propriété reconnu par le fournisseur de données applicable.  Les chemins de propriété sont utilisés en particulier pour <xref:System.Windows.Data.ObjectDataProvider>, qui sert à obtenir des sources de liaison à partir d'objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] et de leurs propriétés.  
  
 La liaison de données vers [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] n'utilise pas <xref:System.Windows.PropertyPath>, car elle n'utilise pas <xref:System.Windows.Data.Binding.Path%2A> dans <xref:System.Windows.Data.Binding>.  À la place, vous utilisez <xref:System.Windows.Data.Binding.XPath%2A> et spécifiez la syntaxe XPath valide dans le [!INCLUDE[TLA#tla_xmldom](../../../../includes/tlasharptla-xmldom-md.md)] des données.  <xref:System.Windows.Data.Binding.XPath%2A> est également spécifié comme une chaîne, mais n'est pas documenté ici; consultez [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).  
  
 Pour bien comprendre les chemins de propriété dans la liaison de données, vous devez savoir qu'il est possible de cibler la liaison sur une valeur de propriété donnée ou de créer une liaison vers des propriétés cibles qui obtiennent des listes ou des collections.  Si vous liez des collections, par exemple une collection <xref:System.Windows.Controls.ListBox> qui se développera en fonction du nombre d'éléments de données compris dans la collection, votre chemin de propriété doit référencer l'objet collection et pas les éléments de collection individuels.  Le moteur de liaison de données établit automatiquement la correspondance entre la collection utilisée en tant que source de données et le type de la cible liée, ce qui entraîne un comportement tel que le remplissage de <xref:System.Windows.Controls.ListBox> avec un tableau d'éléments.  
  
<a name="singlecurrent"></a>   
### Propriété unique de l'objet immédiat en tant que contexte de données  
  
```  
<Binding Path="propertyName" .../>  
```  
  
 *propertyName* doit correspondre au nom d'une propriété située dans le <xref:System.Windows.FrameworkElement.DataContext%2A> actuel pour une utilisation <xref:System.Windows.Data.Binding.Path%2A>.  Si la liaison met à jour la source, cette propriété doit être en lecture\/écriture et l'objet source doit être mutable.  
  
<a name="singleindex"></a>   
### Indexeur unique de l'objet immédiat en tant que contexte de données  
  
```  
<Binding Path="[key]" .../>  
```  
  
 `key` doit correspondre à l'index typé vers un dictionnaire ou une table de hachage ou à l'index d'entiers d'un tableau.  En outre, la valeur de la clé doit être un type pouvant être directement lié à la propriété où elle est appliquée.  Par exemple, une table de hachage qui contient des clés et des valeurs de chaîne peut être utilisée de cette manière pour créer une liaison avec du texte pour un <xref:System.Windows.Controls.TextBox>.  Ou, si la clé pointe vers une collection ou un sous\-index, vous pouvez utiliser cette syntaxe pour créer une liaison avec une propriété de collection cible.  Sinon, vous devez référencer une propriété spécifique via une syntaxe telle que `<Binding Path="[``key``].``propertyName``" .../>`.  
  
 Vous pouvez spécifier le type de l'index, si nécessaire.  Pour plus d'informations sur cet aspect d'un chemin de propriété indexée, consultez <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>.  
  
<a name="multipleindirect"></a>   
### Propriétés multiples \(ciblage de propriété indirect\)  
  
```  
<Binding Path="propertyName.propertyName2" .../>  
```  
  
 `propertyName` doit correspondre au nom d'une propriété qui est le <xref:System.Windows.FrameworkElement.DataContext%2A> actuel.  Les propriétés de chemin `propertyName` et `propertyName2` peuvent être des propriétés qui existent dans une relation, où `propertyName2` correspond à une propriété existant dans le type qui est la valeur de `propertyName`.  
  
<a name="singleattached"></a>   
### Propriété unique, attachée ou typée  
  
```  
<object property="(ownerType.propertyName)" .../>  
```  
  
 Les parenthèses indiquent que cette propriété dans <xref:System.Windows.PropertyPath> doit être construite à l'aide d'une qualification partielle.  Peut utiliser un espace de noms XML pour rechercher le type avec un mappage approprié.  Le `ownerType` recherche les types auxquels un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut accéder via les déclarations <xref:System.Windows.Markup.XmlnsDefinitionAttribute> de chaque assembly.  La plupart des applications ont l'espace de noms XML par défaut mappé à l'espace de noms [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)], donc un préfixe est habituellement uniquement nécessaire pour les types personnalisés ou les types à l'extérieur de cet espace de noms.  `propertyName` doit décider d'être le nom d'une propriété existante sur  `ownerType`.  En règle générale, cette syntaxe est utilisée dans l'un des cas suivants :  
  
-   Le chemin est spécifié en langage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dont le style ou le modèle n'est associé à aucun type de cible.  Une utilisation qualifiée n'est généralement pas valide pour les autres cas que celui\-ci. En effet, dans les cas sans style et sans modèle, la propriété existe dans une instance, pas dans un type.  
  
-   La propriété est attachée.  
  
-   Vous créez une liaison avec une propriété statique.  
  
 Pour une utilisation en tant que cible de table de montage séquentiel, la propriété spécifiée en tant que `propertyName` doit être <xref:System.Windows.DependencyProperty>.  
  
<a name="sourcetraversal"></a>   
### Parcours de source \(liaison avec des hiérarchies de collections\)  
  
```  
<object Path="propertyName/propertyNameX" .../>  
```  
  
 L'élément \/ de cette syntaxe sert à naviguer dans un objet source de données hiérarchique. Il est possible de spécifier plusieurs pas dans la hiérarchie à l'aide de caractères \/ successifs.  Le parcours de source tient compte de la position du pointeur d'enregistrement actif, déterminée en synchronisant les données avec l'interface utilisateur de la vue.  Pour plus d'informations sur la liaison avec des objets source de données hiérarchiques et sur le pointeur d'enregistrement actif dans le cadre de la liaison de données, consultez [Utiliser le modèle maître\/détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md) ou [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
> [!NOTE]
>  En apparence, cette syntaxe ressemble à [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)].  Une vraie expression [!INCLUDE[TLA2#tla_xpath](../../../../includes/tla2sharptla-xpath-md.md)] permettant de créer une liaison avec une source de données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] n'est pas utilisée comme valeur <xref:System.Windows.Data.Binding.Path%2A> et doit plutôt être utilisée pour la propriété <xref:System.Windows.Data.Binding.XPath%2A> mutuellement exclusive.  
  
### Vues de collection  
 Pour référencer une vue de collection nommée, préfixez le nom de vue de collection par le caractère dièse \(`#`\).  
  
### Pointeur d'enregistrement actif  
 Pour référencer le pointeur d'enregistrement actif pour une vue de collection ou un scénario de liaison de données maître\/détail, commencez la chaîne de chemin d'accès par une barre oblique \(`/`\).  N'importe quel chemin d'accès après la barre oblique est parcouru à partir du pointeur d'enregistrement actif.  
  
### Indexeurs multiples  
  
```  
<object Path="[index1,index2...]" .../>  
or  
<object Path="propertyName[index,index2...]" .../>  
```  
  
 Si un objet donné prend en charge plusieurs indexeurs, ceux\-ci peuvent être spécifiés dans l'ordre, de la même manière qu'un tableau faisant référence à une syntaxe.  L'objet en question peut correspondre au contexte actuel ou à la valeur d'une propriété qui contient un objet d'index multiple.  
  
 Par défaut, les valeurs d'indexeur sont typées à l'aide des caractéristiques de l'objet sous\-jacent.  Vous pouvez spécifier le type de l'index, si nécessaire.  Pour plus d'informations sur le typage des indexeurs, consultez <xref:System.Windows.Data.Binding.Path%2A?displayProperty=fullName>.  
  
<a name="mixing"></a>   
### Mélange des syntaxes  
 Chacune des syntaxes ci\-dessus peut être intercalée.  Par exemple, l'exemple suivant crée un chemin de propriété vers la couleur à une coordonnée x,y particulière d'une propriété `ColorGrid` qui contient un tableau de grille de pixels d'objets <xref:System.Windows.Media.SolidColorBrush> :  
  
```  
<Rectangle Fill="{Binding ColorGrid[20,30].SolidColorBrushResult}" .../>  
```  
  
### Échappements pour les chaînes de chemin de propriété  
 Pour certains objets métiers, vous pouvez rencontrer une casse où la chaîne de chemin de propriété requiert une séquence d'échappement pour analyser correctement.  Le besoin d'échappement doit être rare, parce que beaucoup de ces caractères ont des problèmes d'interactions de noms similaires dans les langages généralement utilisés pour définir l'objet métier.  
  
-   À l'intérieur des indexeurs \(\[\]\), le signe d'insertion \(^\) remplace le caractère suivant.  
  
-   Vous devez placer dans une séquence d'échappement \(à l'aide d'entités XML\) certains caractères qui sont spécifiques à la définition de langage XML.  Utilisez `&` pour créer une séquence d'échappement pour le caractère "&".  Utilisez `>` pour créer une séquence d'échappement pour la balise de fin "\>".  
  
-   Vous devez placer dans une séquence d'échappement \(à l'aide de la barre oblique inverse `\`\) les caractères qui sont spécifiques au comportement de l'analyseur XAML WPF pour le traitement d'une extension de balisage.  
  
    -   La barre oblique inverse \(`\`\) est le caractère d'échappement lui\-même.  
  
    -   Le signe égal \(`=`\) sépare le nom de propriété de la valeur de propriété.  
  
    -   La virgule \(`,`\) sépare des propriétés.  
  
    -   L'accolade fermante \(`}`\) marque la fin d'une extension de balisage.  
  
> [!NOTE]
>  Techniquement, ces échappements fonctionnent également pour un chemin de propriété de storyboard, mais vous parcourez habituellement des modèles objets pour les objets WPF existants, et l'échappement devrait être inutile.  
  
<a name="databinding_sa"></a>   
## PropertyPath pour les cibles d'animation  
 La propriété cible d'une animation doit être une [propriété de dépendance](GTMT) qui comporte un <xref:System.Windows.Freezable> ou un type primitif.  Toutefois, la propriété ciblée d'un type et la propriété animée éventuelle peuvent exister sur des objets différents.  En ce qui concerne les animations, un chemin de propriété sert à définir la connexion entre la propriété de l'objet de cible d'animation nommé et la propriété d'animation cible prévue, en parcourant les relations des propriétés d'objets dans les valeurs de propriété.  
  
<a name="general"></a>   
### Considérations générales relatives aux propriétés d'objet pour les animations  
 Pour plus d'informations sur les concepts d'animation en général, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md) et [Vue d'ensemble de l'animation](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Le type valeur ou la propriété animée doit correspondre à un <xref:System.Windows.Freezable> ou à un type primitif.  La propriété qui commence le chemin doit correspondre au nom d'une [propriété de dépendance](GTMT) qui existe pour le type <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> spécifié.  
  
 Pour prendre en charge le clonage afin d'animer un <xref:System.Windows.Freezable> déjà figé, l'objet spécifié par <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> doit être une classe dérivée <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>.  
  
<a name="singlestepanim"></a>   
### Propriété unique sur l'objet cible  
  
```  
<animation Storyboard.TargetProperty="propertyName" .../>  
```  
  
 `propertyName` doit correspondre au nom d'une [propriété de dépendance](GTMT) qui existe pour le type <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> spécifié.  
  
<a name="indirectanim"></a>   
### Ciblage de propriété indirect  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2" .../>  
```  
  
 `propertyName` doit être une propriété correspondant à un type valeur <xref:System.Windows.Freezable> ou à un type primitif, qui existe pour le type <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> spécifié.  
  
 `propertyName2` doit correspondre au nom d'une [propriété de dépendance](GTMT) qui existe sur l'objet représentant la valeur de `propertyName`.  Autrement dit, `propertyName2` doit exister en tant que propriété de dépendance sur le type correspondant à `propertyName`<xref:System.Windows.DependencyProperty.PropertyType%2A>.  
  
 Le ciblage indirect d'animations est nécessaire en raison des styles et modèles appliqués.  Pour pouvoir cibler une animation, vous avez besoin d'un <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> sur un objet cible. Ce nom est défini par [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) ou par <xref:System.Windows.FrameworkElement.Name%2A>.  Les éléments de modèle et de style peuvent également avoir des noms. Toutefois, ces noms ne sont valides que dans la portée de nom du style et du modèle.  \(Si des modèles et des styles partagent des portées de nom avec une balise d'application, les noms ne peuvent pas être uniques.  En effet, les styles et modèles sont littéralement partagés entre des instances et préservent les noms en double.\) Par conséquent, si les propriétés d'un élément que vous souhaitez animer proviennent d'un style ou d'un modèle, vous devez commencer par une instance d'élément nommé qui n'est pas issue d'un modèle de style. Ensuite, vous devez cibler l'arborescence d'éléments visuels du style ou du modèle pour accéder à la propriété à animer.  
  
 Par exemple, la propriété <xref:System.Windows.Controls.Panel.Background%2A> d'un <xref:System.Windows.Controls.Panel> est un <xref:System.Windows.Media.Brush> complet \(en réalité, un <xref:System.Windows.Media.SolidColorBrush>\) qui provient d'un modèle de thème.  Pour animer complètement un <xref:System.Windows.Media.Brush>, il devrait y avoir un BrushAnimation \(probablement un pour chaque type <xref:System.Windows.Media.Brush>\), mais ce type n'existe pas.  Pour animer un Brush, vous animez plutôt des propriétés d'un type <xref:System.Windows.Media.Brush> particulier.  Vous devez partir de <xref:System.Windows.Media.SolidColorBrush> vers <xref:System.Windows.Media.SolidColorBrush.Color%2A> afin d'y appliquer un <xref:System.Windows.Media.Animation.ColorAnimation>.  Pour cet exemple, le chemin de propriété serait `Background.Color`.  
  
<a name="attachedanim"></a>   
### Propriétés jointes  
  
```  
<animation Storyboard.TargetProperty="(ownerType.propertyName)" .../>  
```  
  
 Les parenthèses indiquent que cette propriété dans <xref:System.Windows.PropertyPath> doit être construite à l'aide d'une qualification partielle.  Elle peut utiliser un espace de noms XML pour rechercher le type.  Le `ownerType` recherche les types auxquels un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] peut accéder via les déclarations <xref:System.Windows.Markup.XmlnsDefinitionAttribute> de chaque assembly.  La plupart des applications ont l'espace de noms XML par défaut mappé à l'espace de noms [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)], donc un préfixe est habituellement uniquement nécessaire pour les types personnalisés ou les types à l'extérieur de cet espace de noms.  `propertyName` doit décider d'être le nom d'une propriété existante sur  `ownerType`.  La propriété spécifiée en tant que `propertyName` doit être un <xref:System.Windows.DependencyProperty>.  \(Toutes les propriétés attachées [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] étant implémentées en tant que propriétés de dépendance, ce problème ne concerne que les propriétés attachées personnalisées.\)  
  
<a name="indexanim"></a>   
### Indexeurs  
  
```  
<animation Storyboard.TargetProperty="propertyName.propertyName2[index].propertyName3" .../>  
```  
  
 La plupart des propriétés de dépendance ou des types <xref:System.Windows.Freezable> ne prennent pas d'indexeur en charge.  Par conséquent, la seule utilisation d'un indexeur dans un chemin d'animation se situe à une position intermédiaire entre la propriété qui démarre la chaîne sur la cible nommée et la propriété animée éventuelle.  Dans la syntaxe fournie, il s'agit de `propertyName2`.  Par exemple, l'utilisation d'un indexeur peut s'avérer nécessaire si la propriété intermédiaire est une collection telle que <xref:System.Windows.Media.TransformGroup>, dans un chemin de propriété tel que `RenderTransform.Children[1].Angle`.  
  
<a name="ppincode"></a>   
## PropertyPath dans le code  
 L'utilisation de code pour <xref:System.Windows.PropertyPath>, notamment la construction de <xref:System.Windows.PropertyPath>, est documentée dans la rubrique de référence relative à <xref:System.Windows.PropertyPath>.  
  
 En règle générale, <xref:System.Windows.PropertyPath> est conçu pour utiliser deux constructeurs différents : un pour les utilisations de liaison et les utilisations d'animation les plus simples, et un autre pour les utilisations d'animation complexes.  Utilisez la signature <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> dans le cadre d'une liaison, où l'objet correspond à une chaîne.  Utilisez la signature <xref:System.Windows.PropertyPath.%23ctor%28System.Object%29> pour les chemins d'animation pas à pas, où l'objet correspond à <xref:System.Windows.DependencyProperty>.  Utilisez la signature [PropertyPath\(String, Object\<xref:System.Windows.PropertyPath.%23ctor%28System.String%2CSystem.Object%5B%5D%29> pour les animations complexes.  Ce constructeur utilise une chaîne de jeton pour le premier paramètre et un tableau d'objets qui remplissent les positions de la chaîne de jeton pour définir une relation de chemin de propriété.  
  
## Voir aussi  
 <xref:System.Windows.PropertyPath>   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)