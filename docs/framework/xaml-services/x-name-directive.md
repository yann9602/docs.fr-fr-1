---
title: "x:Name Directive | Microsoft Docs"
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
  - "x:Name"
  - "xName"
  - "Name"
helpviewer_keywords: 
  - "x:Name attribute [XAML Services]"
  - "XAML [XAML Services], x:Name attribute"
  - "Name attribute in XAML [XAML Services]"
ms.assetid: b7e61222-e8cf-48d2-acd0-6df3b7685d48
caps.latest.revision: 27
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 27
---
# x:Name Directive
Identifie de manière unique les éléments définis en XAML\-définis dans une portée de nom XAML.  Les portées de nom XAML et leurs modèles d'unicité peuvent être appliqués aux objets instanciés, lorsque les infrastructures fournissent les API ou implémentent les comportements qui accèdent au graphique d'objets créé en XAML pendant l'exécution.  
  
## Utilisation d'attributs XAML  
  
```  
<object x:Name="XAMLNameValue".../>  
```  
  
## Valeurs XAML  
  
|||  
|-|-|  
|`XAMLNameValue`|Chaîne qui se conforme aux restrictions de la [XamlName, grammaire](../../../docs/framework/xaml-services/xamlname-grammar.md).|  
  
## Notes  
 Après l'application de `x:Name` au modèle de programmation de prise en charge d'une infrastructure, le nom est équivalent à la variable qui conserve une référence d'objet ou une instance telle que retournée par un constructeur.  
  
 La valeur d'une utilisation de la directive `x:Name` doit être unique dans une portée de nom XAML.  Par défaut, lorsqu'elle est utilisée par l'API des services XAML .NET Framework, la portée de nom XAML principale est définie à l'élément racine XAML d'une production XAML unique et intègre les éléments contenus dans cette production XAML.  Les portées de nom XAML discrètes supplémentaires qui peuvent se produire dans une production XAML unique peuvent être définies par les infrastructures pour traiter des scénarios spécifiques.  Par exemple, dans WPF, les nouvelles portées de noms XAML sont définies et créées par tout modèle défini également dans cette production XAML.  Pour plus d'informations sur les portées de noms XAML \(écrits pour WPF mais pertinents pour de nombreux concepts de portée de noms XAML courants\), consultez [Portées de nom XAML WPF](../../../ocs/framework/wpf/advanced/wpf-xaml-namescopes.md).  
  
 En général, `x:Name` ne doit pas être appliqué dans les situations qui utilisent également `x:Key`.  Les implémentations XAML réalisées par les infrastructures spécifiques existantes ont introduit des concepts de substitution entre `x:Key` et `x:Name`, mais ce n'est pas une pratique recommandée.  Les services XAML .NET Framework ne prennent pas en charge de tels concepts de substitution lors de la gestion de noms et d'informations telles que <xref:System.Windows.Markup.INameScope> ou <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.  
  
 Les règles d'autorisation de `x:Name` ainsi que la mise en conformité de l'unicité des noms sont définies potentiellement par des infrastructures d'implémentation spécifiques.  Toutefois, pour être utilisables avec les services XAML .NET Framework, les définitions d'infrastructure de l'unicité de la porté de nom XAML doivent être compatibles avec la définition des informations <xref:System.Windows.Markup.INameScope> dans cette documentation, et doivent utiliser les mêmes règles concernant l'emplacement où les informations sont appliquées.  Par exemple, l'implémentation [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] divise différents éléments de balisage en plages <xref:System.Windows.NameScope> séparées, telles que des dictionnaires de ressources, l'arborescence logique créée par le XAML au niveau de la page, les modèles et d'autres contenus différés, puis met en conformité l'unicité de noms XAML dans chacune ces portées de noms XAML.  
  
 Pour les types personnalisés utilisant des writers d'objet XAML de services XAML .NET Framework, une propriété qui mappe à `x:Name` sur un type peut être établie ou changée.  Vous définissez ce comportement en référençant le nom de la propriété à mapper avec <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> dans le code de définition de type.  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> est un attribut de niveau type.  
  
 À l'aide des services XAML .NET Framework, la logique de stockage pour la prise en charge de la portée de nom XAML peut être définie d'une façon non spécifique à l'infrastructure en implémentant l'interface <xref:System.Windows.Markup.INameScope>.  
  
## Remarques sur l'utilisation de WPF  
 Dans la configuration de build standard pour une application [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] qui utilise XAML, les classes partielles et le code\-behind, le `x:Name` spécifié devient le nom d'un champ qui est créé dans le code sous\-jacent lorsque [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] est traité par une tâche de génération de compilation du balisage, et ce champ contient une référence à l'objet. Par défaut, le champ créé est interne.  Vous pouvez modifier l'accès au champ en spécifiant l'[attribut x:FieldModifier](../../../docs/framework/xaml-services/x-fieldmodifier-directive.md).  Dans WPF et Silverlight, la séquence est que la compilation de balisage définit et nomme le champ dans une classe partielle, mais la valeur est initialement vide.  Ensuite, une méthode générée nommée `InitializeComponent` est appelée à partir du constructeur de classe.  `InitializeComponent` se compose des appels de `FindName` à l'aide de chacune des valeurs `x:Name` qui existent dans la partie XAML de la classe partielle en tant que chaînes d'entrée.  Les valeurs de retour sont ensuite assignées à la référence de champ ainsi nommée pour remplir les valeurs de champs avec les objets créés par l'analyse XAML.  L'exécution de `InitializeComponent` permettent de référencer le graphique d'objet au moment de l'exécution à l'aide de `x:Name` \/ nom de champ directement, plutôt que de devoir appeler explicitement `FindName` à chaque fois que vous avez besoin d'une référence à un objet XAML défini.  
  
 Pour une application WPF qui utilise les cibles [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)] et inclut des fichiers XAML avec l'action de génération `Page`, une propriété de référence séparée est créée pendant la compilation qui ajoute le mot clé `WithEvents` à tous les éléments qui ont un `x:Name`, pour prendre en charge la syntaxe `Handles` pour les délégués de gestionnaire d'événements.  Cette propriété est toujours publique.  Pour plus d'informations, consultez [Gestion des événements Visual Basic et WPF](../../../ocs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md).  
  
 `x:Name` est utilisé par le processeur XAML WPF pour inscrire un nom dans une portée de nom XAML au moment du chargement, même pour les cas où la page n'est pas compilée par balisage par les actions de génération \(par exemple, XAML libre d'un dictionnaire de ressources\).  Une raison de ce comportement vient du fait que `x:Name` est potentiellement nécessaire pour la liaison de <xref:System.Windows.Data.Binding.ElementName%2A>.  Pour plus d'informations, consultez [Vue d'ensemble de la liaison de données](../../../ocs/framework/wpf/data/data-binding-overview.md).  
  
 Comme indiqué précédemment, `x:Name` \(ou `Name`\) ne doit pas être appliqué dans les situations qui également utilisent `x:Key`.  [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.ResourceDictionary> a un comportement spécial consistant à se définir lui\-même comme une portée de nom XAML mais à retourner Non implémenté ou des valeurs null pour les API <xref:System.Windows.Markup.INameScope> comme moyen d'appliquer ce comportement.  Si l'analyseur XAML WPF rencontre `Name` ou `x:Name` dans un <xref:System.Windows.ResourceDictionary> défini en XAML, le nom n'est pas ajouté à une portée de nom XAML.  La tentative de recherche de ce nom à partir d'une portée de nom XAML et les méthodes `FindName` ne retournent pas de résultats valides.  
  
### x:Name et Name  
 De nombreux scénarios d'applications WPF peuvent éviter toute utilisation de l'attribut `x:Name`, parce que la propriété de dépendance `Name` spécifiée dans l'espace de noms XAML par défaut pour plusieurs classes de base importantes telles que <xref:System.Windows.FrameworkElement> et <xref:System.Windows.FrameworkContentElement> satisfait ce même but.  Il existe encore des scénarios XAML et WPF courants, pour lesquels l'accès du code à un élément sans propriété `Name` au niveau de l'infrastructure est important.  Par exemple, certaines animations et classes de prise en charge de table de montage séquentiel ne prennent pas en charge une propriété `Name`, mais elles ont souvent besoin d'être référencées dans le code afin de contrôler l'animation.  Vous devez spécifier `x:Name` comme attribut sur des chronologies et transformations créées en XAML si vous projetez de les référencer ultérieurement à partir du code.  
  
 Si <xref:System.Windows.FrameworkElement.Name%2A> est disponible comme une propriété sur la classe, <xref:System.Windows.FrameworkElement.Name%2A> et `x:Name` peuvent être utilisés de façon interchangeable comme des attributs, mais une exception d'analyse sera levée si les deux sont spécifiés sur le même élément.  Si le XAML est compilé par balisage, l'exception se produira sur la compilation de balisage, sinon, il se produira au chargement.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> peut être défini à l'aide de la syntaxe d'attribut XAML, et dans le code à l'aide de <xref:System.Windows.DependencyObject.SetValue%2A> ; notez cependant que définir la propriété <xref:System.Windows.FrameworkElement.Name%2A> dans le code ne crée pas de référence de champ représentative dans la portée de noms XAML dans la plupart des cas où le XAML est déjà chargé.  Au lieu d'essayer de définir <xref:System.Windows.FrameworkElement.Name%2A> dans le code, utilisez des méthodes <xref:System.Windows.NameScope> à partir du code, par rapport à la portée de nom appropriée.  
  
 <xref:System.Windows.FrameworkElement.Name%2A> peut également être défini à l'aide de la syntaxe d'élément de propriété avec du texte interne, mais c'est rare.  Par opposition, `x:Name` ne peut pas être défini dans la syntaxe d'élément de propriété XAML<xref:System.Windows.DependencyObject.SetValue%2A>, ou dans le code à l'aide de  ; il peut être défini uniquement à l'aide de la syntaxe d'attribut sur des objets parce que c'est une directive.  
  
## Notes d'utilisation de Silverlight  
 `x:Name` pour Silverlight est documenté séparément.  Pour plus d'informations, consultez [Fonctionnalités de langage d'espace de noms XAML \(x:\) \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkId=199081).  
  
## Voir aussi  
 <xref:System.Windows.FrameworkElement.Name%2A?displayProperty=fullName>   
 <xref:System.Windows.FrameworkContentElement.Name%2A?displayProperty=fullName>   
 [Arborescences dans WPF](../../../ocs/framework/wpf/advanced/trees-in-wpf.md)