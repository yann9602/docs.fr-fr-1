---
title: "Vue d&#39;ensemble du langage XAML (WPF) | Microsoft Docs"
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
  - "syntaxe d'attribut (XAML)"
  - "classes de base (XAML)"
  - "classes (XAML)"
  - "fichiers code-behind (WPF), XAML"
  - "propriétés de collections (XAML)"
  - "modèles de contenu (XAML)"
  - "événements [XAML]"
  - "langage XAML (voir XAML)"
  - "Property (élément XAML)"
  - "élément racine (XAML)"
  - "événements routés"
  - "interfaces utilisateur (XAML)"
  - "XAML (WPF), à propos de XAML"
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
caps.latest.revision: 57
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 50
---
# Vue d&#39;ensemble du langage XAML (WPF)
Cette rubrique décrit les fonctionnalités du langage XAML et explique comment l'utiliser pour écrire des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Cette rubrique décrit spécifiquement le langage XAML tel qu'il est implémenté par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  XAML en tant que tel est un concept de langage qui ne se limite pas à [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
   
  
<a name="what_is_xaml"></a>   
## Description du langage XAML  
 XAML est un langage de balisage déclaratif.  Comme appliqué au modèle de programmation [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)], XAML simplifie la création d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] pour une application [!INCLUDE[TLA2#tla_winfx](../../../../includes/tla2sharptla-winfx-md.md)].  Vous pouvez créer des éléments d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] visibles dans le balisage XAML déclaratif, puis séparer la définition de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de la logique au moment de l'exécution en utilisant des fichiers code\-behind, joints aux balises par le biais de définitions de classe partielles.  Le code XAML représente directement l'instanciation d'objets dans un ensemble spécifiques de types de stockage défini dans des assemblys. Il est différent de la plupart des autres langages de balisage, qui sont en général interprété sans un tel lien direct à un système de types de stockage.  XAML créé un workflow au sein duquel des parties éloignées peuvent travailler ensemble sur l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] et la logique d'une application, en utilisant des outils potentiellement différents.  
  
 En cas de représentation sous forme de texte, les fichiers XAML sont des fichiers XML qui disposent généralement d'une extension `.xaml`.  Les fichiers peuvent être encodés par tout encodage XML, mais l'encodage en tant qu'UTF\-8 est typique.  
  
 L'exemple suivant montre comment créer un bouton dans le cadre d'une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)].  Cet exemple est uniquement destiné à vous donner une idée de la manière dont XAML représente les métaphores de programmation d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] courantes \(il ne s'agit pas d'un exemple complet\).  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## Présentation rapide de la syntaxe XAML  
 Les sections suivantes présentent les formes de base de la syntaxe XAML et fournissent un bref exemple de balisage.  Ces sections n'ont pas pour but de fournir des informations exhaustives sur chaque format de syntaxe, notamment sur leur représentation dans le système de types de stockage.  Pour plus d'informations sur les caractéristiques de chacune des formes de syntaxe XAML présentées dans cette rubrique, consultez [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 La plupart des informations dans les sections suivantes vous paraîtront simples, si le langage XML vous est familier.  Cela est dû à l'un des principes de conception du langage XAML.  Il définit ses propres concepts, mais ces concepts fonctionnent dans le langage et le format de balisage XML.  
  
### Éléments d'objet XAML  
 Un élément objet déclare généralement une instance d'un type.  Ce type est défini dans les assemblys qui fournissent les types de stockage à une technologie qui utilise XAML en tant que langage.  
  
 La syntaxe des éléments d'objet commence toujours par un signe « inférieur à » \(\<\).  Suit le nom du type dans lequel vous voulez créer une instance.  \(Le nom peut éventuellement inclure un préfixe, concept qui sera expliqué ultérieurement.\) Ensuite, vous pouvez déclarer des attributs sur l'élément objet si vous le souhaitez.  Pour compléter la balise de l'élément objet, terminez par un signe « supérieur à » \(\>\).  À la place, vous pouvez utiliser une forme d'auto\-fermeture dépourvue de contenu, en complétant la balise par une barre oblique et un signe « supérieur à », dans cet ordre \(\/\>\).  Par exemple, regardez à nouveau l'extrait de code de balisage présenté précédemment :  
  
 [!code-xml[XAMLOvwSupport#DirtSimple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 Spécifie deux éléments objet : `<StackPanel>` \(avec contenu suivi d'une balise de fermeture\) et `<Button .../>` \(forme d'auto\-fermeture, avec plusieurs attributs\).  Les éléments objet `StackPanel` et `Button` sont tous les deux mappés au nom d'une classe qui est définie par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et fait partie des assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Lorsque vous spécifiez une balise d'élément objet, vous créez une instruction pour le traitement XAML qui crée une instance.  Chaque instance est créée en appelant le constructeur par défaut du type sous\-jacent lors de l'analyse et du chargement XAML.  
  
### Syntaxe d'attribut \(propriétés\)  
 Les propriétés d'un objet peuvent souvent être exprimées sous la forme d'attributs de l'élément objet.  Une syntaxe d'attribut nomme la propriété définie dans la syntaxe d'attribut, suivie par l'opérateur d'assignation \(\=\).  La valeur d'un attribut est toujours spécifiée sous la forme d'une chaîne entre guillemets.  
  
 La syntaxe d'attribut est la syntaxe de définition de propriétés la plus simplifiée, en plus d'être la plus intuitive, ce qui devrait pousser les développeurs qui utilisaient des langages de balisage par le passé à la choisir.  Par exemple, la balise suivante crée un bouton comportant du texte rouge et un arrière\-plan bleu, de même que le texte affiché spécifié en tant que `Content`.  
  
 [!code-xml[XAMLOvwSupport#BlueRedButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### Syntaxe d'élément de propriété  
 Il n'est parfois pas possible d'utiliser la syntaxe d'attribut avec certaines propriétés d'un élément objet, car l'objet ou les informations nécessaires pour définir la valeur de la propriété ne peuvent pas être exprimés de manière appropriée par un guillemet et une simple chaîne de syntaxe d'attribut.  Dans ces cas\-là, une syntaxe différente, connue sous le nom de syntaxe d'élément de propriété, peut être utilisée.  
  
 La syntaxe de la balise de début de l'élément de propriété est `<`*typeName*`.`*propertyName*`>`.  En règle générale, le contenu de cette balise est un élément objet du type que la propriété utilise en tant que valeur.  Après avoir spécifié le contenu, vous devez fermer l'élément de propriété avec une balise de fin.  La syntaxe pour la balise de fin est `</`*typeName*`.`*propertyName*`>`.  
  
 Lorsqu'une syntaxe d'attribut peut être utilisée, son utilisation sera privilégiée dans la mesure où elle est plus pratique et permet d'avoir un balisage plus compact. Ce n'est souvent toutefois qu'une question de style et non de limitation technique.  L'exemple suivant illustre la définition des mêmes propriétés que dans l'exemple de syntaxe d'attribut ci\-dessus, mais cette fois en utilisant la syntaxe d'élément de propriété pour l'ensemble des propriétés du `Button`.  
  
 [!code-xml[XAMLOvwSupport#BlueRedButtonPE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### Syntaxe de collection  
 Le langage XAML inclut quelques optimisations qui produisent des balises plus explicites.  Parmi ces optimisations, on peut citer le fait que si une propriété particulière utilise un type de collection, alors les éléments que vous déclarez dans le balisage en tant qu'éléments enfants dans la valeur de cette propriété font partie de la collection.  Dans ce cas, une collection d'éléments objets enfants représente la valeur qui est définie dans la propriété de la collection.  
  
 L'exemple suivant illustre la syntaxe de collection pour la définition des valeurs de la propriété <xref:System.Windows.Media.GradientBrush.GradientStops%2A> :  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### Propriétés de contenu XAML  
 XAML spécifie une fonctionnalité des langage via laquelle une classe peut désigner exactement l'une de ses propriétés comme étant la propriété de contenu XAML.  Les éléments enfants de cet élément objet sont utilisés pour définir la valeur de cette propriété de contenu.  En d'autres termes, vous pouvez omettre un élément de propriété, pour la propriété de contenu uniquement, lorsque vous définissez cette propriété dans le balisage XAML et produire une métaphore parent\/enfant plus visible dans le balisage.  
  
 Par exemple, <xref:System.Windows.Controls.Border> spécifie une propriété de contenu de <xref:System.Windows.Controls.Decorator.Child%2A>.  Les deux éléments <xref:System.Windows.Controls.Border> suivants sont traités de manière identique.  Le premier s'appuie sur la syntaxe de la propriété de contenu et omet l'élément de propriété `Border.Child`.  Le deuxième affiche `Border.Child` explicitement.  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 Une règle du langage XAML veut que la valeur d'une propriété de contenu XAML soit indiquée dans son intégralité avant ou après tous les autres éléments de propriété sur cet élément objet.  Par exemple, la balise suivante ne compile pas :  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 Pour plus d'informations sur cette restriction applicable aux propriétés de contenu XAML, consultez la section « Propriétés de contenu XAML » de [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
### Contenu textuel  
 Un petit nombre d'éléments XAML peuvent traiter directement du texte comme leur contenu.  Pour cela, l'une des situations suivantes doit être respectée :  
  
-   La classe doit déclarer une propriété de contenu, et cette propriété de contenu doit être d'un type assignable à une chaîne \(le type peut être <xref:System.Object>\).  Par exemple, tout contrôle <xref:System.Windows.Controls.ContentControl> utilise <xref:System.Windows.Controls.ContentControl.Content%2A> en tant que propriété de contenu et le type <xref:System.Object>, assurant ainsi la prise en charge de l'utilisation suivante sur un <xref:System.Windows.Controls.ContentControl> pratique, tel qu'un <xref:System.Windows.Controls.Button>: `<Button>Hello</Button>`.  
  
-   Le type doit déclarer un convertisseur de type, auquel cas le contenu textuel est utilisé comme texte d'initialisation pour ce convertisseur de type.  Par exemple, `<Brush>Blue</Brush>`.  Ce cas est moins commun dans la pratique.  
  
-   Le type doit être une primitive de langage XAML connue.  
  
### Propriétés de contenu et syntaxe de collection combinées  
 Considérez cet exemple :  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 Dans ce cas précis, chaque <xref:System.Windows.Controls.Button> est un élément enfant de <xref:System.Windows.Controls.StackPanel>.  Il s'agit d'une balise simplifiée et intuitive qui omet deux instructions pour deux raisons différentes.  
  
-   **Élément de propriété StackPanel.Children omis :** <xref:System.Windows.Controls.StackPanel> est dérivé de <xref:System.Windows.Controls.Panel>.  <xref:System.Windows.Controls.Panel> définit <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> comme sa propriété de contenu XAML.  
  
-   **Élément objet UIElementCollection omis :** La propriété <xref:System.Windows.Controls.Panel.Children%2A?displayProperty=fullName> prend le type <xref:System.Windows.Controls.UIElementCollection>, qui implémente <xref:System.Collections.IList>.  La balise d'élément de la collection peut être omise, conformément aux règles XAML de traitement des collections telles que <xref:System.Collections.IList>.  \(Dans ce cas, <xref:System.Windows.Controls.UIElementCollection> ne peut pas être réellement instancié parce qu'il n'expose pas de constructeur par défaut, et c'est pourquoi l'élément objet <xref:System.Windows.Controls.UIElementCollection> est indiqué comme commenté\).  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### Syntaxe d'attribut \(événements\)  
 La syntaxe d'attribut peut également être utilisée pour les membres qui sont des événements plutôt que des propriétés.  Dans ce cas, le nom de l'attribut est le nom de l'événement.  Dans l'implémentation WPF d'événements pour XAML, la valeur de l'attribut est le nom d'un gestionnaire qui implémente le délégué de cet événement.  Par exemple, la balise suivante assigne un gestionnaire pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> à un <xref:System.Windows.Controls.Button> créé dans la balise :  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 En ce qui concerne les événements et XAML, WPF recouvre bien plus que ce simple exemple de syntaxe d'attribut.  Par exemple, vous pouvez vous demander ce que le `ClickHandler` référencé ici représente et comment il est défini.  Tout ceci vous sera expliqué dans la section  suivante de cette rubrique.  
  
<a name="case_and_whitespace_in_xaml"></a>   
## Cas et espace blanc en XAML  
 XAML respecte la casse en général.  À des fins de résolution des types de stockage, XAML WPF respecte la casse selon les mêmes règles que le CLR respecte la casse.  Les éléments objet, les éléments de propriété et les noms d'attribut doivent être spécifiés à l'aide du respect de la casse en comparant le nom au type sous\-jacent dans l'assembly ou à un membre d'un type.  Les primitives et les mots clés du langage XAML respectent également la casse.  Les valeurs ne respectent pas toujours la casse.  Le respect de la casse par les valeurs dépend du comportement du convertisseur de type associé à la propriété qui prend la valeur ou du type valeur de la propriété.  Par exemple, les propriétés qui prennent le type <xref:System.Boolean> peuvent prendre la valeur `true` ou `True` qui sont équivalentes, mais uniquement parce que la conversion du type d'analyseur XAML WPF natif de chaîne pour <xref:System.Boolean> accepte déjà ces valeurs comme étant équivalentes.  
  
 Les processeurs et les sérialiseurs XAML WPF ignorent ou suppriment tous les espaces blancs non significatifs et normalisent ceux qui sont significatifs.  Cela est cohérent avec les recommandations du comportement de l'espace blanc par défaut de la spécification XAML.  Ce comportement n'a généralement de conséquences que lorsque vous spécifiez des chaînes dans les propriétés de contenu XAML.  Pour faire simple, XAML convertit les espaces, les sauts de ligne et les tabulations en espaces, puis conserve un seul espace à chacune des extrémités d'une chaîne contiguë.  La gestion des espaces blancs en XAML n'est pas couverte de manière exhaustive dans cette rubrique.  Pour plus d'informations, consultez [Traitement des espaces blancs en XAML](../../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).  
  
<a name="markup_extensions"></a>   
## Extensions de balisage  
 Les extensions de balisage sont un concept de langage XAML.  Lorsqu'elles sont utilisées pour attribuer la valeur d'une syntaxe d'attribut, les accolades `{` et `}`\) indiquent l'utilisation d'une extension de balisage.  Cette utilisation ordonne au traitement XAML de se soustraire au traitement général des valeurs d'attribut en tant que chaîne littérale ou valeur convertible en chaîne.  
  
 Les extensions de balisage les plus courantes utilisées dans la programmation d'applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont [Binding](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), qui est utilisée pour les expressions de liaison de données, et les références de ressource [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) et [DynamicResource](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md).  En utilisant des extensions de balisage, vous pouvez utiliser la syntaxe d'attribut pour fournir des valeurs pour les propriétés même si cette propriété ne prend pas en charge de syntaxe d'attribut en général.  Les extensions de balisage utilisent souvent des types d'expression intermédiaires pour autoriser des fonctions telles que le traitement différé des valeurs ou le référencement d'autres objets qui sont uniquement présents au moment de l'exécution.  
  
 Par exemple, le balisage suivant définit la valeur de la propriété <xref:System.Windows.FrameworkElement.Style%2A> à l'aide de la syntaxe d'attribut.  La propriété <xref:System.Windows.FrameworkElement.Style%2A> prend une instance de la classe <xref:System.Windows.Style> qui, par défaut, ne pouvait pas être instanciée par une chaîne de syntaxe d'attribut.  Mais dans ce cas, l'attribut référence une extension de balisage particulière, [StaticResource](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md).  Lorsque cette extension de balisage est traitée, elle retourne une référence à un style qui a été instancié précédemment en tant que ressource indexée dans un dictionnaire de ressources.  
  
<!-- TODO: review snippet reference  [!CODE [FEResourceSH#XAMLOvwShortResources](FEResourceSH#XAMLOvwShortResources)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources2](FEResourceSH#XAMLOvwShortResources2)]  -->  
<!-- TODO: review snippet reference [!CODE [FEResourceSH#XAMLOvwShortResources3](FEResourceSH#XAMLOvwShortResources3)]  -->  
  
 Pour obtenir la liste de toutes les extensions de balisage pour XAML spécifiquement implémentées dans WPF, consultez [Extensions XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md).  Pour obtenir la liste des références des extensions de balisage qui sont définies par System.Xaml et qui sont largement disponibles pour les implémentations XAML .NET Framework, consultez [Fonctionnalités de langage pour les espaces de noms XAML \(x:\)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  Pour plus d'informations sur les concepts d'extension de balisage, consultez [Extensions de balisage et XAML WPF](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
<a name="type_converters"></a>   
## Convertisseurs de type  
 La section  indique que la valeur de l'attribut doit pouvoir être définie par une chaîne.  La gestion native de base de la conversion des chaînes en d'autres types d'objets ou valeurs primitives repose sur le type <xref:System.String> proprement dit, en plus du traitement natif de certains types, tels que <xref:System.DateTime> ou <xref:System.Uri>.  Toutefois, de nombreux types [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ou membres de ces types étendent le comportement de traitement de base des attributs de chaîne, de sorte que des instances de types d'objets plus complexes puissent être spécifiées comme des chaînes et des attributs.  
  
 La structure <xref:System.Windows.Thickness> est un exemple d'un type pour lequel une conversion de type est possible pour les utilisations de XAML.  <xref:System.Windows.Thickness> indique des dimensions dans un rectangle imbriqué et est utilisé en tant que valeur pour les propriétés telles que <xref:System.Windows.FrameworkElement.Margin%2A>.  En plaçant un convertisseur de type sur <xref:System.Windows.Thickness>, toutes les propriétés qui utilisent un <xref:System.Windows.Thickness> sont plus faciles à spécifier en XAML, étant donné qu'elles peuvent être spécifiées en tant qu'attributs.  L'exemple suivant utilise une syntaxe d'attribut et une conversion de type pour attribuer une valeur à une <xref:System.Windows.FrameworkElement.Margin%2A> :  
  
 [!code-xml[XAMLOvwSupport#MarginTCE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 L'exemple de syntaxe d'attribut précédent est équivalent à l'exemple de syntaxe plus complet suivant, où le <xref:System.Windows.FrameworkElement.Margin%2A> est défini à la place via une syntaxe d'élément de propriété qui contient un élément objet <xref:System.Windows.Thickness>.  Les quatre propriétés de clé de <xref:System.Windows.Thickness> sont définies comme attributs sur la nouvelle instance :  
  
 [!code-xml[XAMLOvwSupport#MarginVerbose](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  Il existe également un nombre limité d'objets pour lesquels la conversion de type est la seule manière publique d'affecter une propriété à ce type sans impliquer une sous\-classe, car le type proprement dit ne possède pas de constructeur par défaut.  C'est le cas notamment de <xref:System.Windows.Input.Cursor>.  
  
 Pour plus d'informations sur la conversion de type et son utilisation pour la syntaxe d'attribut, consultez [TypeConverters et XAML](../../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## Éléments racine XAML et espaces de noms XAML  
 Un fichier XAML ne peut contenir qu'un seul élément racine pour être à la fois un fichier [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] de forme correcte et un fichier XAML valide.  Dans le cas de scénarios WPF typiques, vous devez choisir un élément racine significatif dans le modèle d'application WPF \(par exemple, <xref:System.Windows.Window> ou <xref:System.Windows.Controls.Page> pour une page, <xref:System.Windows.ResourceDictionary> pour un dictionnaire externe ou <xref:System.Windows.Application> pour la définition d'application\).  L'exemple suivant montre l'élément racine d'un fichier XAML type pour une page [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], avec l'élément racine <xref:System.Windows.Controls.Page>.  
  
 [!code-xml[XAMLOvwSupport#RootOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xml[XAMLOvwSupport#RootOnly2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 L'élément racine contient également les attributs `xmlns` et `xmlns:x`.  Ces attributs indiquent à un processeur XAML les espaces de noms XAML qui contiennent les définitions des types de stockage qui seront référencés par le balisage en tant qu'éléments.  L'attribut `xmlns` indique spécifiquement l'espace de noms XAML par défaut.  Dans l'espace de noms XAML par défaut, les éléments objet du balisage peuvent être spécifiés sans préfixe.  Dans la plupart des scénarios d'application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et dans la quasi\-totalité des exemples donnés dans les sections [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] du [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], l'espace de noms XAML par défaut est mappé à l'espace de noms [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)].  L'attribut `xmlns:x` indique un espace de noms XAML supplémentaire, qui mappe l'espace de noms du langage XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)].  
  
 Cette utilisation de `xmlns` pour définir une portée pour l'utilisation et le mappage d'une portée de nom est cohérente avec la spécification XML 1.0.  Les portées de nom XAML sont différentes des portées de nom XML uniquement en ceci qu'une portée de nom XAML implique également des informations sur la manière dont les éléments de portée de nom sont stockés par les types dans le cadre de la résolution du type et de l'analyse du contenu XAML.  
  
 Notez que les attributs `xmlns` sont strictement nécessaires uniquement sur l'élément racine de chaque fichier XAML.  Les définitions `xmlns` s'appliquent à tous les éléments descendants de l'élément racine \(ce comportement est compatible avec la spécification XML 1.0 pour `xmlns`.\) Les attributs `xmlns` sont également autorisés sur d'autres éléments en dessous de la racine et peuvent s'appliquer à tous les éléments descendants de l'élément de définition.  Cependant, la définition ou la redéfinition fréquente des espaces de noms XAML peut donner lieu à un style de balisage XAML difficile à lire.  
  
 L'implémentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de son processeur XAML inclut une infrastructure qui a conscience des assemblys WPF principaux.  Les assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] principaux sont réputés pour contenir les types qui prennent en charge les mappages [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l'espace de noms XAML par défaut.  Ce mappage est possible grâce à la configuration qui fait partie de votre fichier de génération de projet, ainsi que des systèmes de génération et de projet WPF.  Par conséquent, la déclaration d'un espace de noms XAML par défaut en tant que `xmlns` par défaut suffit pour référencer les éléments XAML provenant d'assemblys [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### Le préfixe x:  
 Dans l'exemple d'élément racine précédent, le préfixe `x:` a été utilisé pour mapper l'espace de noms XAML [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)], qui est l'espace de noms XAML dédié prenant en charge les constructions de langage XAML.  Ce préfixe `x:` est utilisé pour mapper cet espace de noms XAML dans les modèles de projets, dans les exemples et dans la documentation de ce [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)].  L'espace de noms XAML du langage XAML contient plusieurs constructions de programmation que vous utiliserez très fréquemment dans votre contenu XAML.  Les constructions de programmation de préfixe `x:` que vous utiliserez le plus souvent sont répertoriées dans la liste suivante :  
  
-   [x:Key](../../../../docs/framework/xaml-services/x-key-directive.md): définit une clé unique pour chaque ressource dans un <xref:System.Windows.ResourceDictionary> \(ou concepts de dictionnaire semblables dans d'autres infrastructures\).  `x:Key` représentera probablement 90 % des utilisations de `x:` que vous rencontrerez dans le balisage d'une application WPF typique.  
  
-   [x:Class](../../../../docs/framework/xaml-services/x-class-directive.md) : spécifie l'espace de noms [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et le nom de la classe qui fournit le code\-behind pour une page XAML.  Vous devez disposer d'une telle classe pour prendre en charge le code\-behind par le biais du modèle de programmation WPF et, par conséquent, vous devez presque toujours voir `x:` mappé, même en l'absence de ressources.  
  
-   [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) : spécifie un nom d'objet au moment de l'exécution pour l'instance qui existe dans le code au moment de l'exécution après qu'un élément objet a été traité.  En général, vous utiliserez fréquemment une propriété équivalente définie par WPF pour [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md).  De telles propriétés mappent spécifiquement à une propriété de stockage CLR et sont donc plus commodes pour la programmation d'applications, dans laquelle vous utilisez fréquemment le code au moment de l'exécution pour rechercher les éléments nommés du XAML initialisé.  La propriété de ce type la plus courante est <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName>.  Vous pouvez encore utiliser [x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) lorsque la propriété équivalente [au niveau de l'infrastructure WPFP:System.Windows.FrameworkElement.Name](GTMT) n'est pas prise en charge dans un type particulier.  Cela peut arriver dans certains scénarios d'animation.  
  
-   [x:Static](../../../../docs/framework/xaml-services/x-static-markup-extension.md) : active une référence qui retourne une valeur statique qui, dans d'autres circonstances, n'est pas une propriété compatible XAML.  
  
-   [x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) : construit une référence <xref:System.Type> en fonction d'un nom de type.  Il est utilisé pour spécifier des attributs qui prennent <xref:System.Type>, tels que <xref:System.Windows.Style.TargetType%2A?displayProperty=fullName>, même si la propriété propose fréquemment une conversion de chaîne en <xref:System.Type> native de manière à ce que l'utilisation de l'extension de balisage [x:Type](../../../../docs/framework/xaml-services/x-type-markup-extension.md) soit facultative.  
  
 Il existe d'autres constructions de programmation dans le préfixe `x:`\/espace de noms XAML qui ne sont pas aussi courantes.  Pour plus d'informations, consultez [Fonctionnalités de langage pour les espaces de noms XAML \(x:\)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## Préfixes personnalisés et types personnalisés en XAML  
 Pour vos propres assemblys personnalisés, tout comme pour les assemblys autres que le cœur WPF de PresentationCore, PresentationFramework et WindowsBase, vous pouvez spécifier l'assembly comme étant un élément d'un mappage `xmlns` personnalisé.  Vous pouvez ensuite référencer les types de cet assembly dans votre XAML, dans la mesure où votre type est correctement implémenté de manière à prendre en charge les utilisations XAML voulues.  
  
 L'exemple suivant présente de manière très simple le fonctionnement des préfixes personnalisés dans le balisage XAML.  Le préfixe `custom` est défini dans la balise d'élément racine et est mappé à un assembly spécifique packagé et disponible avec l'application.  Cet assembly contient un type `NumericUpDown` implémenté pour prendre en charge l'utilisation générale de XAML ainsi que l'utilisation d'un héritage de classe autorisant son insertion à ce point particulier dans un modèle de contenu XAML WPF.  Une instance de ce contrôle `NumericUpDown` est déclarée en tant qu'élément objet, à l'aide du préfixe, afin qu'un analyseur XAML identifie l'espace de noms XAML contenant le type, et par conséquent l'emplacement de l'assembly de stockage contenant la définition de type.  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 Pour plus d'informations sur les types personnalisés en XAML, consultez [XAML et classes personnalisées pour WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).  
  
 Pour plus d'informations sur la relation entre les espaces de noms XML et les espaces de noms du code de stockage dans les assemblys, consultez [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).  
  
<a name="events_and_xaml_codebehind"></a>   
## Événements et code\-behind XAML  
 La plupart des applications [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont composées de code\-behind et de balises XAML.  Dans un projet, le code XAML est écrit sous la forme d'un fichier `.xaml`, et d'un langage [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] de sorte que [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] ou [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] est utilisé pour écrire un fichier code\-behind.  Lorsqu'un fichier XAML est compilé pour balisage en tant que partie de modèles d'application et de programmation WPF, l'emplacement du fichier code\-behind XAML pour un fichier XAML est identifié en spécifiant un espace de noms et une classe en tant qu'attribut `x:Class` de l'élément racine du XAML.  
  
 Dans les exemples examinés jusqu'à présent, vous avez vu plusieurs boutons, mais aucun comportement logique ne leur a été associé jusqu'à présent.  Au niveau de l'application, le mécanisme de base pour ajouter un comportement pour un élément objet consiste à utiliser un événement existant de l'élément classe et d'écrire un gestionnaire spécifique pour cet événement appelé lorsque cet événement est déclenché au moment de l'exécution.  Le nom de l'évènement et le nom du gestionnaire à utiliser sont spécifiés dans la balise, tandis que le code qui implémente votre gestionnaire est défini dans le code\-behind.  
  
 [!code-xml[XAMLOvwSupport#ButtonWithCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 Notez que le fichier code\-behind utilise l'espace de noms CLR `ExampleNamespace` et déclare `ExamplePage` en tant que classe partielle de cet espace de noms.  Cela correspondant à la valeur d'attribut `x:Class` de `ExampleNamespace`.`ExamplePage` qui a été fournie dans la racine de la balise.  Le compilateur de balisage WPF crée une classe partielle pour tout fichier XAML compilé, en dérivant une classe du type d'élément racine.  Lorsque vous fournissez un code\-behind qui définit cette même classe partielle, le code résultant est combiné dans les mêmes espace de noms et classe de l'application compilée.  
  
 Pour plus d'informations sur les exigences associées à la programmation de code\-behind dans WPF, consultez la section « Exigences concernant le code\-behind, le gestionnaire d'événements et les classes partielles » de [Code\-behind et XAML dans WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
 Si vous ne souhaitez pas créer de fichier code\-behind distinct, vous pouvez également incorporer votre code dans un fichier XAML.  Ce code incorporé est toutefois une technique moins flexible et qui présente des limitations substantielles.  Pour plus d'informations, consultez [Code\-behind et XAML dans WPF](../../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
### Événements routés  
 Les [événements routés](GTMT) sont une fonctionnalité d'événement particulière fondamentale de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les événements routés permettent à un élément de gérer un événement déclenché par un autre élément, pour autant qu'ils soient connectés par le biais d'une relation d'arborescence.  Lorsque vous spécifiez la gestion des événements avec un attribut XAML, vous pouvez écouter et gérer l'événement routé sur n'importe quel élément, y compris les éléments qui ne répertorient pas cet événement particulier dans la table des membres de la classe.  Pour ce faire, vous devez qualifier l'attribut de nom de l'évènement avec le nom de classe possédant.  Par exemple, le `StackPanel` parent dans l'exemple `StackPanel` \/ `Button` en cours peut enregistrer un gestionnaire pour l'événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton de l'élément enfant en spécifiant l'attribut `Button.Click` sur l'élément objet `StackPanel`, avec le nom de votre gestionnaire comme valeur d'attribut.  Pour plus d'informations sur le fonctionnement des événements routés, consultez [Vue d'ensemble des événements routés](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="x_name_and_xaml_named_elements"></a>   
## Éléments nommés XAML  
 Par défaut, l'instance d'objet créée dans un graphique d'objet lors du traitement d'un élément objet XAML ne possède pas d'identificateur unique ni de référence d'objet.  En revanche, si vous appelez un constructeur dans le code, vous utilisez presque toujours le résultat de constructeur pour attribuer une variable à l'instance construite, de manière à pouvoir référencer l'instance ultérieurement dans votre code.  Pour fournir un accès standardisé aux objets créés à l'aide d'une définition de balise, XAML définit l'[attribut x:Name](../../../../docs/framework/xaml-services/x-name-directive.md) Vous pouvez définir la valeur de l'attribut `x:Name` sur n'importe quel élément objet.  Dans votre code\-behind, l'identificateur que vous choisissez équivaut à une variable d'instance qui fait référence à l'instance construite.  Les éléments nommés fonctionnent à tous points de vue comme s'ils étaient des instances d'objet \(le nom référence cette instance\) et votre code\-behind peut référencer les éléments nommés pour gérer des interactions au moment de l'exécution dans l'application.  Cette connexion entre instances et variables est accomplie par le compilateur de balisage XAML WPF, et  implique plus spécifiquement des fonctionnalités et des modèles tels que <xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A> qui ne seront pas abordés en détail dans cette rubrique.  
  
 Les éléments XAML [au niveau de l'infrastructure WPF](GTMT) héritent d'une propriété <xref:System.Windows.FrameworkElement.Name%2A>, qui équivaut à l'attribut `x:Name` défini dans le contenu XAML.  Plusieurs autres classes fournissent également des équivalents de niveau propriété pour `x:Name`, qui est également souvent définie comme une propriété `Name`.  En général, si vous ne pouvez pas trouver de propriété `Name` dans la table des membres pour votre élément\/type choisi, utilisez `x:Name` à la place.  Les valeurs `x:Name` fourniront un identificateur à un élément XAML qui peut être utilisé au moment de l'exécution, par les sous\-systèmes spécifiques ou par les méthodes utilitaire telles que <xref:System.Windows.FrameworkElement.FindName%2A>.  
  
 L'exemple suivant définit <xref:System.Windows.FrameworkElement.Name%2A> sur un élément <xref:System.Windows.Controls.StackPanel>.  Un gestionnaire sur un <xref:System.Windows.Controls.Button> dans ce <xref:System.Windows.Controls.StackPanel> référence ensuite le <xref:System.Windows.Controls.StackPanel> par le biais de sa référence d'instance `buttonContainer` définie par <xref:System.Windows.FrameworkElement.Name%2A>.  
  
 [!code-xml[XAMLOvwSupport#NamedE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xml[XAMLOvwSupport#NamedE2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 À l'instar d'une variable, le nom XAML d'une instance est gouverné par un concept de portée, de sorte que des noms uniques peuvent être appliqués au sein d'une portée prévisible.  La balise primaire qui définit une page définit une portée de nom XAML unique, la limite de cette portée étant l'élément racine de cette page.  D'autres sources de balisage peuvent toutefois interagir avec une page au moment de l'exécution \(styles ou modèles contenus dans des styles\) et ces sources possèdent souvent leur propre portée de nom XAML, qui n'est pas forcément connectée à celle de la page.  Pour plus d'informations sur `x:Name` et les portées de nom XAML, consultez <xref:System.Windows.FrameworkElement.Name%2A>, [x:Name, directive](../../../../docs/framework/xaml-services/x-name-directive.md) ou [Portées de nom XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
<a name="attached_properties_and_attached_events"></a>   
## Propriétés et événements attachés  
 XAML comprend une fonctionnalité de langage qui permet de spécifier certains événements ou certaines propriétés sur un élément quelconque, indépendamment du fait que la propriété ou l'élément existe ou non dans les définitions de type de l'élément sur lequel il est défini.  La version propriété de cette fonctionnalité est appelée une [propriété attachée](GTMT) et la version événement un [événement attaché](GTMT).  Conceptuellement, vous pouvez considérer les propriétés jointes et les événements attachés comme des membres globaux qui peuvent être définis sur toute instance élément\/objet XAML.  Toutefois, cet élément\/classe ou une infrastructure plus importante doit prendre en charge une banque de propriétés de stockage pour les valeurs attachées.  
  
 Les propriétés jointes en XAML sont généralement utilisées par le biais de la syntaxe d'attribut.  Dans la syntaxe d'attribut, les propriétés jointes sont spécifiées sous la forme *TypePropriétaire*.*NomPropriété*.  
  
 En apparence, cela ressemble à une utilisation d'élément de propriété, mais dans ce cas\-ci, le *TypePropriétaire* que vous spécifiez est toujours d'un type autre que l'élément objet dans lequel la propriété jointe est définie.  *TypePropriétaire* est le type qui fournit les méthodes d'accesseur exigées par un processeur XAML pour obtenir ou définir la valeur de la propriété jointe.  
  
 Le scénario le plus courant pour les propriétés attachées consiste à permettre à des éléments enfants de signaler une valeur de propriété à leur élément parent.  
  
 L'exemple suivant illustre la propriété attachée <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>.  La classe <xref:System.Windows.Controls.DockPanel> définit les accesseurs pour <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> et possède par conséquent la propriété attachée.  La classe <xref:System.Windows.Controls.DockPanel> inclut également une logique qui itère ses éléments enfants et vérifie de manière spécifique chaque élément pour une valeur définie de <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName>.  Si une valeur est trouvée, elle est utilisée pendant la disposition pour placer les éléments enfants.  L'utilisation de la propriété attachée <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=fullName> et de cette fonctionnalité de positionnement est en fait le scénario motivant pour la classe <xref:System.Windows.Controls.DockPanel>.  
  
 [!code-xml[XAMLOvwSupport#DockAP](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 Dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], la plupart des propriétés jointes sont également implémentées sous forme de [propriétés de dépendance](GTMT).  Pour plus d'informations, consultez [Vue d'ensemble des propriétés jointes](../../../../docs/framework/wpf/advanced/attached-properties-overview.md).  
  
 Les événements attachés utilisent une forme *TypePropriétaire*.*NomÉvénement* similaire à la syntaxe d'attribut.  Comme pour les événements non attachés, la valeur d'attribut d'un événement attaché en XAML spécifie le nom de la méthode de gestionnaire appelée lorsque l'événement est géré sur l'élément.  Les utilisations d'événements attachés en XAML WPF sont moins communes.  Pour plus d'informations, consultez [Vue d'ensemble des événements attachés](../../../../docs/framework/wpf/advanced/attached-events-overview.md).  
  
<a name="base_classes_and_xaml"></a>   
## Types de base et XAML  
 Le XAML WPF sous\-jacent et son espace de noms XAML sont une collection de types qui correspondent à des objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et à des éléments de balisage pour XAML.  Toutes les classes ne peuvent cependant pas être mappées à des éléments.  Les classes abstraites, telles que <xref:System.Windows.Controls.Primitives.ButtonBase>, ainsi que certaines classes de base non\-abstraites, sont utilisées pour l'héritage dans le modèle d'objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Les classes de base, y compris abstraites, sont importantes pour le développement en XAML car chacun des éléments XAML concrets hérite de membres d'une classe de base quelconque dans sa hiérarchie.  Souvent, ces membres incluent des propriétés qui peuvent être définies en tant qu'attributs sur l'élément, ou en tant qu'événements qui peuvent être gérés.  <xref:System.Windows.FrameworkElement> est la classe [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] de base concrète de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] au [niveau de l'infrastructure WPF](GTMT).  Lors de la conception de l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], vous utiliserez différentes classes de forme, de panneau, de décorateur ou de contrôle, qui dérivent toutes de <xref:System.Windows.FrameworkElement>.  Une classe de base connexe, <xref:System.Windows.FrameworkContentElement>, prend en charge des éléments orientés document qui fonctionnent bien pour une présentation de mise en page fluide, à l'aide d'[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] qui reflètent délibérément les [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dans <xref:System.Windows.FrameworkElement>.  La combinaison d'attributs au niveau de l'élément et d'un modèle d'objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vous offre un jeu de propriétés courantes qui sont définissables sur la majorité des éléments XAML concrets, indépendamment de l'élément exact spécifique et de son type sous\-jacent.  
  
<a name="xaml_security"></a>   
## Sécurité XAML  
 XAML est un langage de balisage qui représente directement l'instanciation et l'exécution de l'objet.  Par conséquent, les éléments créés en XAML ont la même capacité d'interaction avec les ressources système \(accès réseau, E\/S du système de fichiers, par exemple\) que le code généré correspondant.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge le [!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)] de l'infrastructure de sécurité [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  Cela signifie que le contenu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui s'exécute dans la zone Internet dispose d'autorisations d'exécution réduites. "  XAML libre » \(pages de XAML non compilé interprétées au moment du chargement par une visionneuse XAML\) et l'application [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] sont généralement exécutés dans cette zone Internet et utilisent le même jeu d'autorisations.  Le XAML chargé dans une application bénéficiant d'un niveau de confiance total a toutefois le même accès aux ressources système que l'application hôte.  Pour plus d'informations, consultez [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
<a name="loading_xaml_from_code"></a>   
## Chargement de XAML à partir du code  
 XAML peut être utilisé pour définir l'ensemble de l'interface utilisateur, mais il est parfois approprié de définir uniquement une partie de l'interface utilisateur en XAML.  Cette fonction peut par exemple être utilisée pour permettre une personnalisation partielle, un stockage local d'informations, l'utilisation de XAML pour fournir un objet d'entreprise, ou dans divers autres scénarios.  La clé de ces scénarios repose sur la classe <xref:System.Windows.Markup.XamlReader> et sa méthode <xref:System.Windows.Markup.XamlReader.Load%2A>.  L'entrée est un fichier XAML et la sortie un objet qui représente l'intégralité de l'arborescence d'objets au moment de l'exécution créée à partir de ce balisage.  Vous pouvez alors insérer l'objet pour qu'il devienne une propriété d'un autre objet déjà présent dans l'application.  Pour autant que la propriété soit une propriété appropriée dans le modèle de contenu qui possède d'éventuelles fonctions d'affichage et qui indique au moteur d'exécution qu'un nouveau contenu a été ajouté dans l'application, vous pouvez très facilement modifier le contenu d'une application en cours d'exécution en le chargeant en XAML.  Notez que cette fonction est généralement uniquement disponible dans des applications de confiance totale, en raison des implications évidentes pour la sécurité liées au chargement de fichiers dans des applications en cours d'exécution.  
  
<a name="whats_next"></a>   
## Quoi d'autre ?  
 Cette rubrique propose une introduction de base à la terminologie et aux concepts de la syntaxe XAML comme elle s'applique à WPF.  Pour plus d'informations sur les termes utilisés ici, consultez [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).  
  
 Si ce n'est déjà fait, essayez les exercices de la rubrique [Procédure pas à pas : mise en route de WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md) du didacticiel.  La création de l'application de balisage décrite dans le didacticiel contribuera à renforcer votre compréhension de bon nombre des concepts décrits dans cette rubrique.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un modèle d'application particulier basé sur la classe <xref:System.Windows.Application>.  Pour plus d'informations, consultez [Vue d'ensemble de la gestion d'applications](../../../../docs/framework/wpf/app-development/application-management-overview.md).  
  
 [Génération d'une application WPF](../../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md) propose davantage de détails sur la génération d'applications XAML inclusives à partir de la ligne de commande et avec [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].  
  
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) donne plus d'informations sur la polyvalence des propriétés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et introduit le concept de [propriétés de dépendance](GTMT).  
  
## Voir aussi  
 [Syntaxe XAML en détail](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)   
 [XAML et classes personnalisées pour WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [Fonctionnalités de langage pour les espaces de noms XAML \(x:\)](../../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md)   
 [Extensions XAML WPF](../../../../docs/framework/wpf/advanced/wpf-xaml-extensions.md)   
 [Vue d'ensemble des éléments de base](../../../../docs/framework/wpf/advanced/base-elements-overview.md)   
 [Arborescences dans WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)