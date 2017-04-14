---
title: "Port&#233;es de nom XAML WPF | Microsoft Docs"
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
  - "API, associées à des noms"
  - "classes, FrameworkContentElement"
  - "classes, FrameworkElement"
  - "classes, RegisterName"
  - "FrameworkContentElement (classe)"
  - "FrameworkElement (classe)"
  - "API associées à des noms"
  - "portées de nom"
  - "RegisterName (classe)"
  - "styles, portées de nom dans"
  - "modèles, portées de nom dans"
  - "XAML, portées de nom"
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 18
---
# Port&#233;es de nom XAML WPF
Les portées de nom XAML sont un concept qui identifie les objets définis en XAML.  Les noms dans une portée de nom XAML peuvent être utilisés pour établir des relations entre les noms définis en XAML des objets et leurs équivalents d'instances dans une arborescence d'objets.  En général, les portées de nom XAML dans le code managé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées lors du chargement des racines de la page XAML pour une application XAML.  Les portées de nom XAML en tant qu'objet de programmation sont définies par l'interface <xref:System.Windows.Markup.INameScope> et sont également implémentées par la classe pratique <xref:System.Windows.NameScope>.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## Les portées de noms dans les applications XAML chargées  
 Dans un contexte de programmation ou informatique plus général, les concepts de programmation incluent souvent le principe d'un identificateur ou nom unique qui peut être utilisé pour accéder à un objet.  Pour les systèmes qui utilisent des identificateurs ou des noms de ce type, la portée de nom définit les limites indiquant à quel endroit un processus ou une technique effectuera des recherches si un objet de ce nom est demandé, ou les limites dans lesquelles le caractère unique des noms d'identification est appliqué.  Ces principes généraux sont vrais pour des portées de nom XAML.  Dans WPF, les portées de nom XAML sont créées sur l'élément racine d'une page XML lorsque la page est chargée.  Chaque nom spécifié dans la page XAML en commençant à sa racine est ajouté à une portée de nom XAML pertinente.  
  
 Dans le XAML de WPF, les éléments qui sont des éléments racine courants \(<xref:System.Windows.Controls.Page> et <xref:System.Windows.Window>, par exemple\) contrôlent toujours une portée de nom XAML.  Si un élément tel que <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> est l'élément racine de la page dans le balisage, un processeur [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ajoute implicitement une racine <xref:System.Windows.Controls.Page> de sorte que la <xref:System.Windows.Controls.Page> puisse fournir une portée de nom XAML qui fonctionne.  
  
> [!NOTE]
>  Les actions de génération WPF créent une portée de nom XAML pour la production XAML même si aucun attribut `Name` ou `x:Name` n'est défini sur un élément du balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Si vous essayez d'utiliser deux fois le même nom dans une portée de nom XAML, une exception est levée.  Pour le XAML de WPF qui a du code\-behind et fait partie d'une application compilée, l'exception est levée au moment de la génération par les actions de génération WPF, lors de la création de la classe générée pour la page pendant la compilation de balisage initiale.  Pour le XAML non compilé par balisage par aucune action de génération, des exceptions liées aux problèmes de portée de nom XAML peuvent être déclenchées lors du chargement du XAML.  Les concepteurs XAML peuvent également anticiper les problèmes de portée de nom XAML au moment du design.  
  
### Ajout d'objets aux arborescences d'objet d'exécution  
 Le moment où le langage XAML est analysé représente celui où une portée de nom XAML WPF est créée et définie.  Si vous ajoutez un objet à une arborescence d'objets à tout moment après que le code XAML ayant généré cette arborescence a été analysé, une valeur `Name` ou `x:Name` sur le nouvel objet ne met pas automatiquement à jour les informations dans une portée de nom XAML.  Pour ajouter un nom à un objet dans une portée de nom XAML WPF après le chargement de XAML, vous devez appeler l'implémentation appropriée de <xref:System.Windows.Markup.INameScope.RegisterName%2A> sur l'objet qui définit la portée de nom XAML, qui est en général la racine de la page XAML.  Si le nom n'est pas enregistré, l'objet ajouté ne peut pas être référencé par son nom via des méthodes comme <xref:System.Windows.FrameworkElement.FindName%2A>, et vous ne pouvez pas utiliser ce nom pour le ciblage d'animation.  
  
 Le scénario le plus courant pour les développeurs d'applications consiste à utiliser <xref:System.Windows.FrameworkElement.RegisterName%2A> pour enregistrer les noms dans la portée de nom XAML sur la racine actuelle de la page.  <xref:System.Windows.FrameworkElement.RegisterName%2A> fait partie d'un scénario important pour les tables de montage séquentiel qui ciblent des objets pour les animations.  Pour plus d'informations, consultez [Vue d'ensemble des storyboards](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Si vous appelez <xref:System.Windows.FrameworkElement.RegisterName%2A> sur un objet autre que l'objet qui définit la portée de nom XAML, le nom est toujours enregistré dans la portée de nom XAML dans lequel l'objet appelant est conservé, comme si vous aviez appelé <xref:System.Windows.FrameworkElement.RegisterName%2A> sur la portée de nom XAML définissant l'objet.  
  
### Portées de nom XAML dans le code  
 Vous pouvez créer puis utiliser des portées de nom XAML dans le code.  Les API et les concepts impliqués dans la création de la portée de nom XAML sont les mêmes, même pour une utilisation de code pur, car le processeur XAML pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ces API et concepts lorsqu'il traite le XAML lui\-même.  Les concepts et l'API existent principalement pour pouvoir rechercher des objets par leur nom dans une arborescence d'objets généralement définie complètement ou partiellement en XAML.  
  
 Pour les applications créées par programmation, et pas depuis un XAML chargé, l'objet qui définit une portée de nom XAML doit implémenter <xref:System.Windows.Markup.INameScope> ou être une classe dérivée de <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> afin de prendre en charge la création d'une portée de nom XAML sur ses instances.  
  
 De même, pour tout élément qui n'est pas chargé et traité par un processeur XAML, la portée de nom XAML pour l'objet n'est pas créée ou initialisée par défaut.  Vous devez créer explicitement une nouvelle portée de nom XAML pour tout objet dans lequel vous envisagez d'enregistrer des noms par la suite.  Pour créer une portée de nom XAML, vous appelez la méthode <xref:System.Windows.NameScope.SetNameScope%2A> statique.  Spécifiez l'objet qui le possédera en tant que paramètre `dependencyObject`, ainsi qu'un nouvel appel de constructeur <xref:System.Windows.NameScope.%23ctor%2A> en tant que paramètre `value`.  
  
 Si l'objet fourni comme `dependencyObject` pour <xref:System.Windows.NameScope.SetNameScope%2A> n'est pas une implémentation <xref:System.Windows.Markup.INameScope>, <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, appelant <xref:System.Windows.FrameworkElement.RegisterName%2A> sur tout élément enfant n'aura aucun effet.  Si vous ne parvenez pas à créer la nouvelle portée de nom XAML explicitement, les appels à <xref:System.Windows.FrameworkElement.RegisterName%2A> lèveront une exception.  
  
 Pour obtenir un exemple de l'utilisation des API de portée de nom XAML dans du code, consultez [Définir une portée de nom](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## Portées de nom XAML dans les styles et les modèles  
 Les styles et les modèles de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] offrent la possibilité de réutiliser et de réappliquer le contenu d'une façon simple.  Toutefois, les styles et les modèles peuvent également comprendre des éléments avec des noms XAML définis au niveau de modèle.  Ce même modèle peut être utilisé plusieurs fois dans une page.  Pour cette raison, les styles et les modèles définissent tous deux leurs propres portées de nom XAML, indépendamment de toute emplacement dans une arborescence d'objets où le style ou le modèle est appliqué.  
  
 Prenons l'exemple suivant :  
  
 [!code-xml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ici, le même modèle est appliqué à deux boutons différents.  Si les modèles n'avaient pas de portées de nom XAML discrètes, le nom `TheBorder` utilisé dans le modèle provoquerait un conflit de nom dans la portée de nom XAML.  Chaque instanciation du modèle a sa propre portée de nom XAML ; c'est pourquoi, dans cet exemple, la portée de nom XAML de chaque modèle instancié contient exactement un nom.  
  
 Les styles définissent également leur propre portée de nom XAML, essentiellement afin que les différentes parties des storyboards puissent avoir des noms particuliers.  Ces noms activent des comportements spécifiques des contrôles qui cibleront des éléments de ce nom, même si le modèle a été redéfini dans le cadre de la personnalisation de contrôle.  
  
 En raison de la séparation des portées de nom XAML, la recherche d'éléments nommés dans un modèle est plus difficile que la recherche d'un élément nommé non basé sur un modèle dans une page.  Vous devez tout d'abord déterminer le modèle appliqué en obtenant la valeur de propriété <xref:System.Windows.Controls.Control.Template%2A> du contrôle où le modèle est appliqué.  Vous appelez ensuite la version de modèle de <xref:System.Windows.FrameworkTemplate.FindName%2A>, en passant le contrôle où le modèle a été appliqué comme deuxième paramètre.  
  
 Si vous êtes auteur de contrôle et que vous générez une convention où un élément nommé particulier dans un modèle appliqué est la cible pour un comportement défini par le contrôle lui\-même, vous pouvez utiliser la méthode <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> de votre code d'implémentation de contrôle.  La méthode <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> est protégée, de sorte que seul l'auteur du contrôle y a accès.  
  
 Si vous travaillez à partir d'un modèle et que vous devez récupérer la portée de nom XAML à laquelle le modèle est appliqué, récupérez la valeur de <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, puis appelez <xref:System.Windows.FrameworkElement.FindName%2A>.  Un exemple de travail dans le modèle serait si vous écrivez l'implémentation du gestionnaire d'événements où l'événement sera déclenché à partir d'un élément dans un modèle appliqué.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## Portées de nom XAML et API associées à des noms  
 <xref:System.Windows.FrameworkElement> a <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> et les méthodes <xref:System.Windows.FrameworkElement.UnregisterName%2A>.  Si l'objet sur lequel vous appelez ces méthodes possède une portée de nom XAML, les méthodes appellent les méthodes de la portée de nom XAML pertinente.  Sinon, l'élément parent est vérifié pour voir s'il possède une portée de nom XAML, et ce processus continue de manière récursive jusqu'à ce qu'une portée de nom XAML soit trouvée \(en raison du comportement du processeur XAML, la présence d'une portée de nom XAML à la racine est garantie\).  <xref:System.Windows.FrameworkContentElement> a des comportements analogues, à ceci près qu'aucun <xref:System.Windows.FrameworkContentElement> ne possédera jamais une portée de nom XAML.  Les méthodes existent sur <xref:System.Windows.FrameworkContentElement> afin que les appels puissent être envoyés par la suite à un élément parent <xref:System.Windows.FrameworkElement>.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> est utilisé pour mapper une nouvelle portée de nom XAML à un objet existant.  Vous pouvez appeler <xref:System.Windows.NameScope.SetNameScope%2A> plusieurs fois pour réinitialiser ou effacer la portée de nom XAML, mais il ne s'agit pas d'une pratique courante.  De même, <xref:System.Windows.NameScope.GetNameScope%2A> n'est pas généralement utilisé à partir du code.  
  
### Implémentations de portées de nom XAML  
 Les classes suivantes implémentent <xref:System.Windows.Markup.INameScope> directement :  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> n'utilise pas de noms ou de portées de nom XAML ; il utilise à la place des clés, parce qu'il s'agit d'une implémentation de dictionnaire.  La seule raison pour laquelle <xref:System.Windows.ResourceDictionary> implémente <xref:System.Windows.Markup.INameScope> est que cela lui permet de lever des exceptions au code utilisateur qui aident à clarifier la distinction entre une véritable portée de nom XAML et la manière dont un <xref:System.Windows.ResourceDictionary> gère les clés, et également pour de s'assurer que les portées de nom XAML ne sont pas appliquées à un <xref:System.Windows.ResourceDictionary> par des éléments parents.  
  
 <xref:System.Windows.FrameworkTemplate> et <xref:System.Windows.Style> implémentent <xref:System.Windows.Markup.INameScope> via des définitions d'interface explicites.  Les implémentations explicites permettent à ces portées de nom XAML de se comporter de manière conventionnelle lorsqu'on y accède via l'interface <xref:System.Windows.Markup.INameScope> \(ce qui constitue la manière dont les portées de nom XAML sont communiquées par les processus internes [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]\).  En revanche, les définitions d'interface explicites ne font pas partie de la partie API classique de <xref:System.Windows.FrameworkTemplate> et <xref:System.Windows.Style>, étant donné que vous ne devez que rarement appeler directement les méthodes <xref:System.Windows.Markup.INameScope> sur <xref:System.Windows.FrameworkTemplate> et <xref:System.Windows.Style>, et devez à la place utiliser une autre API telle que <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Les classes suivantes définissent leurs propres portées de nom XAML en utilisant la classe d'assistance <xref:System.Windows.NameScope?displayProperty=fullName> et en se connectant à son implémentation de portée de nom XAML par le biais de la propriété jointe <xref:System.Windows.NameScope.NameScope%2A?displayProperty=fullName> :  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## Voir aussi  
 [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)   
 [x:Name, directive](../../../../docs/framework/xaml-services/x-name-directive.md)