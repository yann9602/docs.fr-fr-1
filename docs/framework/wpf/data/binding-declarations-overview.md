---
title: "Vue d&#39;ensemble des d&#233;clarations de liaison | Microsoft Docs"
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
  - "lier des données, déclarations"
  - "déclarations de liaisons"
  - "liaison de données, déclarations"
  - "extensions de balisage"
  - "élément objet (syntaxe)"
  - "syntaxe, éléments objets"
ms.assetid: b97fd626-4c0d-4761-872a-2bca5820da2c
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# Vue d&#39;ensemble des d&#233;clarations de liaison
Cette rubrique traite des différentes manières de déclarer une liaison.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Prereq"></a>   
## Composants requis  
 Avant de lire cette rubrique, il importe que vous soyez familiarisé avec le concept et l'utilisation des extensions de balisage.  Pour plus d'informations sur les extensions de balisage, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 Cette rubrique n'aborde pas les concepts de liaison de données.  Pour en savoir plus sur les concepts de liaison de données, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
<a name="BindinginXAML"></a>   
## Déclaration d'une liaison en XAML  
 Cette section explique comment déclarer une liaison en XAML.  
  
<a name="MarkupExtensionSyntax"></a>   
### Utilisation d'extension de balisage  
 <xref:System.Windows.Data.Binding> est une extension de balisage.  Lorsque vous utilisez l'extension de liaison pour déclarer une liaison, la déclaration consiste en une série de clauses qui suivent le mot clé `Binding` et sont séparées par des virgules \(,\).  Les clauses de la déclaration de liaison peuvent se présenter dans n'importe quel ordre et de nombreuses combinaisons sont possibles.  Les clauses sont des paires *Nom*\= *Valeur*, où *Nom* correspond au nom de la propriété <xref:System.Windows.Data.Binding> et *Valeur* correspond à la valeur que vous affectez à la propriété.  
  
 Lorsque vous créez des chaînes de déclaration de liaison dans la balise, vous devez les attacher à la [propriété de dépendance](GTMT) spécifique d'un objet cible.  L'exemple suivant montre comment lier la propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> à l'aide de l'extension de liaison, en spécifiant les propriétés <xref:System.Windows.Data.Binding.Source%2A> et <xref:System.Windows.Data.Binding.Path%2A>.  
  
 [!code-xml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Vous pouvez ainsi spécifier la plupart des propriétés de la classe <xref:System.Windows.Data.Binding>.  Pour plus d'informations sur l'extension de liaison et pour obtenir la liste des propriétés <xref:System.Windows.Data.Binding> qui ne peuvent pas être définies à l'aide de l'extension de liaison, consultez la vue d'ensemble [Binding, extension de balisage](../../../../docs/framework/wpf/advanced/binding-markup-extension.md).  
  
<a name="ObjectElementSyntax"></a>   
### Syntaxe des éléments objet  
 La syntaxe d'éléments objet est une alternative à la création de la déclaration de liaison.  Dans la plupart des cas, l'utilisation de l'extension de balisage ou de la syntaxe d'élément objet ne présente aucun avantage particulier.  Toutefois, vous devez utiliser la syntaxe d'élément objet lorsque l'extension de balisage ne prend pas en charge votre scénario, par exemple : lorsque la valeur de votre propriété est d'un type non\-chaîne pour lequel il n'existe aucune conversion.  
  
 L'exemple suivant illustre à la fois la syntaxe d'élément objet et l'utilisation d'extension de balisage :  
  
 [!code-xml[BindConversionMarkup#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversionMarkup/CSharp/Page1.xaml#1)]  
  
 L'exemple lie la propriété <xref:System.Windows.Controls.TextBlock.Foreground%2A> en déclarant une liaison à l'aide de la syntaxe d'extension.  La déclaration de liaison pour la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> utilise la syntaxe d'élément objet.  
  
 Pour plus d'informations sur les différents termes, consultez [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
<a name="MBandPB"></a>   
### MultiBinding et PriorityBinding  
 <xref:System.Windows.Data.MultiBinding> et <xref:System.Windows.Data.PriorityBinding> ne prennent pas en charge la syntaxe d'extension XAML.  Par conséquent, vous devez utiliser la syntaxe d'élément objet si vous déclarez un <xref:System.Windows.Data.MultiBinding> ou un <xref:System.Windows.Data.PriorityBinding> en XAML.  
  
<a name="BindinginCode"></a>   
## Création d'une liaison dans le code  
 Pour spécifier une liaison, vous pouvez également définir les propriétés directement sur un objet <xref:System.Windows.Data.Binding> dans le code.  L'exemple suivant indique comment créer un objet <xref:System.Windows.Data.Binding> et spécifier les propriétés dans le code :  Dans cet exemple, `TheConverter` est un objet qui implémente l'interface <xref:System.Windows.Data.IValueConverter>.  
  
 [!code-csharp[BindConversion#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#1)]
 [!code-vb[BindConversion#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#1)]  
[!code-csharp[BindConversion#end1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindConversion/CSharp/Window1.xaml.cs#end1)]
[!code-vb[BindConversion#end1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindConversion/visualbasic/window1.xaml.vb#end1)]  
  
 Si l'objet que vous liez est un <xref:System.Windows.FrameworkElement> ou un <xref:System.Windows.FrameworkContentElement>, vous pouvez appeler la méthode `SetBinding` directement sur votre objet au lieu d'utiliser <xref:System.Windows.Data.BindingOperations.SetBinding%2A?displayProperty=fullName>.  Pour obtenir un exemple, consultez [Créer une liaison dans du code](../../../../docs/framework/wpf/data/how-to-create-a-binding-in-code.md).  
  
<a name="Path_Syntax"></a>   
## Syntaxe de Path pour la liaison  
 Utilisez la propriété <xref:System.Windows.Data.Binding.Path%2A> pour spécifier la valeur source que vous souhaitez utiliser pour la liaison :  
  
-   Dans le cas le plus simple, la valeur de la propriété <xref:System.Windows.Data.Binding.Path%2A> correspond au nom de la propriété de l'objet source à utiliser pour la liaison, comme `Path=PropertyName`.  
  
-   Les sous\-propriétés d'une propriété peuvent être spécifiées par une syntaxe semblable, comme dans [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)].  Par exemple, la clause `Path=ShoppingCart.Order` affecte à la liaison la valeur de la sous\-propriété `Order` de l'objet ou la propriété `ShoppingCart`.  
  
-   Pour créer une liaison avec une [propriété attachée](GTMT), placez des parenthèses autour de la [propriété attachée](GTMT).  Par exemple, pour créer une liaison avec la [propriété attachée](GTMT) <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>, la syntaxe est `Path=(DockPanel.Dock)`.  
  
-   Les indexeurs d'une propriété peuvent être spécifiés dans des crochets qui suivent le nom de la propriété où l'indexeur est appliqué.  Par exemple, la clause `Path=ShoppingCart[0]` affecte à la liaison l'index qui correspond à la manière dont l'indexation interne de votre propriété gère la chaîne littérale "0".  Les indexeurs imbriqués sont également pris en charge.  
  
-   Vous pouvez combiner des indexeurs et des sous\-propriétés dans une clause `Path`. Par exemple : `Path=ShoppingCart.ShippingInfo[MailingAddress,Street].`  
  
-   À l'intérieur des indexeurs peuvent figurer plusieurs paramètres d'indexeur séparés par des virgules \(,\).  Vous pouvez spécifier le type de chaque paramètre à l'aide de parenthèses.  Par exemple, vous pouvez avoir `Path="[(sys:Int32)42,(sys:Int32)24]"`, où `sys` est mappé à l'espace de noms `System`.  
  
-   Lorsque la source est une vue de collection, l'élément actuel peut être spécifié avec une barre oblique \(\/\).  Par exemple, la clause `Path=/` affecte à la liaison l'élément actuel dans la vue.  Lorsque la source est une collection, cette syntaxe spécifie l'élément actuel de la vue de collection par défaut.  
  
-   Les noms de propriété et les barres obliques peuvent être combinés pour parcourir les propriétés qui constituent des collections.  Par exemple, `Path=/Offices/ManagerName` spécifie l'élément actuel de la collection de sources, contenant une propriété `Offices` qui est également une collection.  Son élément actuel est un objet qui contient une propriété `ManagerName`.  
  
-   Un Path incluant un point \(.\) peut également être utilisé pour effectuer une liaison vers la source actuelle.  Par exemple, `Text="{Binding}"` est équivalent à `Text="{Binding Path=.}"`.  
  
### Mécanisme d'échappement  
  
-   À l'intérieur des indexeurs \(\[\]\), le signe d'insertion \(^\) remplace le caractère suivant.  
  
-   Si vous définissez <xref:System.Windows.Data.Binding.Path%2A> en XAML, vous devez également échapper \(à l'aide d'entités XML\) certains caractères spécifiques à la définition de langage XML :  
  
    -   Utilisez `&` pour créer une séquence d'échappement pour le caractère "&".  
  
    -   Utilisez `>` pour créer une séquence d'échappement pour la balise de fin "\>".  
  
-   En outre, si vous décrivez la liaison entière dans un attribut à l'aide de la syntaxe d'extension de balisage, vous devez créer une séquence d'échappement \(à l'aide de la barre oblique inverse "\\"\) pour les caractères propres à l'analyseur d'extension de balisage [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] :  
  
    -   La barre oblique inverse \(\\\) est le caractère d'échappement lui\-même.  
  
    -   Le signe égal \(\=\) sépare le nom de propriété de la valeur de propriété.  
  
    -   La virgule \(,\) sépare des propriétés.  
  
    -   L'accolade fermante \(}\) marque la fin d'une extension de balisage.  
  
<a name="Default"></a>   
## Comportements par défaut  
 Le comportement par défaut est le suivant si vous n'avez rien spécifié dans la déclaration.  
  
-   Un convertisseur par défaut est créé et tente de procéder à une conversion de type entre la valeur de la [source de liaison](GTMT) et la valeur de la [cible de liaison](GTMT).  En cas d'échec de la conversion, le convertisseur par défaut retourne la valeur `null`.  
  
-   Si vous ne définissez pas <xref:System.Windows.Data.Binding.ConverterCulture%2A>, le moteur de liaison utilise la propriété `Language` de l'objet [cible de la liaison](GTMT).  En XAML, la valeur par défaut est "en\-US" ou hérite de la valeur de l'élément racine \(ou tout élément\) de la page, si une valeur a été explicitement définie.  
  
-   Tant que la liaison a déjà un contexte de données \(par exemple, le contexte de données hérité provenant d'un élément parent\) et que l'élément ou la collection retourné par ce contexte convient pour lier sans requérir de changement de chemin d'accès supplémentaire, une déclaration de liaison ne peut avoir aucune clause : `{Binding}` C'est souvent de cette façon qu'une liaison est spécifiée pour l'application du style de données, où la liaison agit sur une collection.  Pour plus d'informations, consultez la section « Objets entiers utilisés comme source de liaison » de la rubrique [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
-   Le <xref:System.Windows.Data.Binding.Mode%2A> par défaut est unidirectionnel ou bidirectionnel selon la [propriété de dépendance](GTMT) liée.  Vous pouvez toujours déclarer explicitement le mode de liaison pour garantir que votre liaison a le comportement désiré.  En général, les propriétés de contrôle modifiables par l'utilisateur, telles que <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> et <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A?displayProperty=fullName>, ont comme valeur par défaut des liaisons bidirectionnelles, alors que la plupart des autres propriétés ont comme valeur par défaut des liaisons unidirectionnelles.  
  
-   La valeur <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> par défaut est <xref:System.Windows.Data.UpdateSourceTrigger> ou <xref:System.Windows.Data.UpdateSourceTrigger> selon la [propriété de dépendance](GTMT) liée.  La valeur par défaut de la plupart des [propriétés de dépendance](GTMT) est <xref:System.Windows.Data.UpdateSourceTrigger>, alors que la valeur par défaut de la propriété <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=fullName> est <xref:System.Windows.Data.UpdateSourceTrigger>.  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [PropertyPath, syntaxe XAML](../../../../docs/framework/wpf/advanced/propertypath-xaml-syntax.md)