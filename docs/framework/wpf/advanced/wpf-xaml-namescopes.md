---
title: "Portées de nom XAML WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22b0354a0821021239140527793dc34e3911a733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-xaml-namescopes"></a>Portées de nom XAML WPF
Les portées de nom XAML correspondent à un concept qui identifie des objets définis en XAML. Les noms dans une portée de nom XAML peuvent être utilisés pour établir des relations entre les noms définis en XAML des objets et leurs instances équivalentes dans une arborescence d’objets. En règle générale, les portées de nom XAML dans du code managé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées lors du chargement des racines d’une page XAML spécifique pour une application XAML. Portées de nom XAML en tant qu’objet de programmation sont définies par le <xref:System.Windows.Markup.INameScope> de l’interface et sont également implémentées par la classe pratique <xref:System.Windows.NameScope>.  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Portées de nom dans les applications XAML chargées  
 Dans un contexte plus large de programmation ou d’informatique, les concepts de programmation incluent souvent le principe d’un identificateur ou d’un nom unique, qui peut être utilisé pour accéder à un objet. Pour les systèmes qui utilisent des identificateurs ou des noms, la portée de nom définit les limites à l’intérieur desquelles un processus ou une technique recherche si un objet de ce nom est demandé, ou les limites dans lesquelles l’unicité des noms qui identifient est appliquée. Ces principes généraux sont vrais pour les portées de nom XAML. Dans WPF, les portées de nom XAML sont créées sur l’élément racine d’une page XAML quand la page est chargée. Chaque nom spécifié dans la page XAML en commençant à la racine de la page est ajouté à une portée de nom XAML pertinente.  
  
 Dans WPF XAML, les éléments qui sont des éléments racine courants (tels que <xref:System.Windows.Controls.Page>, et <xref:System.Windows.Window>) contrôlent toujours une portée de nom XAML. Si un élément tel que <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> est l’élément racine de la page dans le balisage, un [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] processeur ajoute un <xref:System.Windows.Controls.Page> racine implicitement afin que le <xref:System.Windows.Controls.Page> peut fournir une portée de nom XAML travail.  
  
> [!NOTE]
>  Les actions de génération WPF créent une portée de nom XAML pour une production XAML même si aucun attribut `Name` ou `x:Name` n’est défini sur les éléments dans la balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Si vous essayez d’utiliser deux fois le même nom dans une portée de nom XAML, une exception est levée. Pour du XAML WPF qui a du code-behind et qui fait partie d’une application compilée, l’exception est levée au moment de la génération par les actions de génération WPF, lors de la création de la classe générée pour la page pendant la compilation initiale du balisage. Pour le XAML qui n’est compilé par balisage par aucune action de génération, des exceptions liées aux problèmes de portée de nom XAML peuvent être déclenchées lors du chargement du XAML. Les concepteurs XAML peuvent également anticiper les problèmes de portée de nom XAML au moment du design.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Ajout d’objets à des arborescences d’objets d’exécution  
 Le moment où le XAML est analysé correspond au moment une portée de nom XAML WPF est créée et définie. Si vous ajoutez un objet à une arborescence d’objets après l’analyse du code XAML ayant généré cette arborescence, une valeur `Name` ou `x:Name` sur le nouvel objet ne met pas automatiquement à jour les informations contenues dans une portée de nom XAML. Pour ajouter un nom d’un objet dans une portée de nom XAML WPF après le chargement de XAML, vous devez appeler l’implémentation appropriée de <xref:System.Windows.Markup.INameScope.RegisterName%2A> sur l’objet qui définit la portée de nom XAML, qui est généralement la racine de la page XAML. Si le nom n’est pas enregistré, l’objet ajouté ne peut pas être référencée par nom via des méthodes telles que <xref:System.Windows.FrameworkElement.FindName%2A>, et vous ne pouvez pas utiliser ce nom pour le ciblage d’animation.  
  
 Le scénario le plus courant pour les développeurs d’applications est que vous allez utiliser <xref:System.Windows.FrameworkElement.RegisterName%2A> pour enregistrer les noms dans la portée de nom XAML sur la racine actuelle de la page. <xref:System.Windows.FrameworkElement.RegisterName%2A>fait partie d’un scénario important pour les animations qui ciblent des objets pour les animations. Pour plus d’informations, consultez [Vue d’ensemble des plans conceptuels](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
 Si vous appelez <xref:System.Windows.FrameworkElement.RegisterName%2A> sur un objet autre que l’objet qui définit la portée de nom XAML, le nom est encore inscrite à la portée de nom XAML que l’objet appelant est conservé, comme si vous aviez appelé <xref:System.Windows.FrameworkElement.RegisterName%2A> sur la portée de nom XAML définissant l’objet.  
  
### <a name="xaml-namescopes-in-code"></a>Portées de nom XAML dans du code  
 Vous pouvez créer et ensuite utiliser des portées de nom XAML dans du code. Les API et les concepts impliqués dans la création de portée de nom XAML sont les mêmes, même pour une utilisation du code pure, car le processeur XAML pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ces API et concepts quand il traite le XAML lui-même. Les concepts et l’API existent principalement pour pouvoir rechercher des objets par nom dans une arborescence d’objets définie partiellement ou entièrement en XAML.  
  
 Pour les applications qui sont créées par programme et non à partir de XAML chargé, l’objet qui définit la portée de nom XAML doit implémenter <xref:System.Windows.Markup.INameScope>, ou être un <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> classe dérivée pour prendre en charge la création d’une portée de nom XAML sur ses instances.  
  
 De même, pour tout élément qui n’est pas chargé et traité par un processeur XAML, la portée de nom XAML pour l’objet n’est pas créée ou initialisée par défaut. Vous devez créer explicitement une nouvelle portée de nom XAML pour tout objet dans lequel vous prévoyez d’inscrire des noms par la suite. Pour créer une portée de nom XAML, vous appelez la méthode statique <xref:System.Windows.NameScope.SetNameScope%2A> (méthode). Spécifiez l’objet qui sera propriétaire en tant que le `dependencyObject` paramètre et une nouvelle <xref:System.Windows.NameScope.%23ctor%2A> appel de constructeur en tant que le `value` paramètre.  
  
 Si l’objet fourni en tant que `dependencyObject` pour <xref:System.Windows.NameScope.SetNameScope%2A> n’est pas un <xref:System.Windows.Markup.INameScope> mise en œuvre, <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement>, l’appel <xref:System.Windows.FrameworkElement.RegisterName%2A> sur n’importe quel enfant éléments n’a aucun effet. Si vous ne parvenez pas à créer la nouvelle portée de nom XAML explicitement, les appels à <xref:System.Windows.FrameworkElement.RegisterName%2A> lève une exception.  
  
 Pour obtenir un exemple d’utilisation des API de portée de nom XAML dans du code, consultez [Définir une portée de nom](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Portées de nom XAML dans les styles et les modèles  
 Les styles et les modèles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent de réutiliser et de réappliquer le contenu d’une manière simple. Toutefois, les styles et les modèles peuvent également inclure des éléments avec des noms XAML définis au niveau d’un modèle. Ce même modèle peut être utilisé plusieurs fois dans une page. Pour cette raison, les styles et les modèles définissent tous deux leurs propres portées de nom XAML, indépendamment de l’emplacement où le style ou le modèle est appliqué dans une arborescence d’objets.  
  
 Prenons l'exemple suivant :  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ici, le même modèle est appliqué à deux boutons différents. Si les modèles n’avaient pas de portées de nom XAML discrètes, le nom `TheBorder` utilisé dans le modèle provoquerait un conflit de noms dans la portée de nom XAML. Chaque instanciation du modèle a sa propre portée de nom XAML. Ainsi, dans cet exemple, la portée de nom XAML de chaque modèle instancié contient un et un seul nom.  
  
 Les styles définissent également leur propre portée de nom XAML, principalement pour que des noms particuliers puissent être affectés aux différentes parties des plans conceptuels. Ces noms activent des comportements spécifiques des contrôles qui ciblent les éléments de ce nom, même si le modèle a été redéfini dans le cadre de la personnalisation du contrôle.  
  
 En raison des portées de nom XAML distinctes, rechercher des éléments nommés dans un modèle est plus difficile que rechercher dans une page un élément nommé non basé sur un modèle. Vous devez tout d’abord déterminer le modèle appliqué en obtenant la <xref:System.Windows.Controls.Control.Template%2A> valeur de la propriété du contrôle où le modèle est appliqué. Vous appelez ensuite la version du modèle de <xref:System.Windows.FrameworkTemplate.FindName%2A>, en passant le contrôle où le modèle a été appliqué comme deuxième paramètre.  
  
 Si vous êtes l’auteur du contrôle et que vous générez une convention où un élément nommé particulier dans un modèle appliqué est la cible pour un comportement qui est défini par le contrôle lui-même, vous pouvez utiliser la <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> méthode depuis votre code d’implémentation d’un contrôle. Le <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> méthode est protégée, seul l’auteur du contrôle y a accès.  
  
 Si vous travaillez à partir d’un modèle et accéder à la portée de nom XAML où le modèle est appliqué, obtenir la valeur de <xref:System.Windows.FrameworkElement.TemplatedParent%2A>, puis appelez <xref:System.Windows.FrameworkElement.FindName%2A> il. Un exemple de travail à l’intérieur du modèle est l’écriture de l’implémentation du gestionnaire d’événements là où l’événement est déclenché à partir d’un élément dans un modèle appliqué.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Portées de nom XAML et API relatives aux noms  
 <xref:System.Windows.FrameworkElement>a <xref:System.Windows.FrameworkElement.FindName%2A>, <xref:System.Windows.FrameworkElement.RegisterName%2A> et <xref:System.Windows.FrameworkElement.UnregisterName%2A> méthodes. Si l’objet sur lequel vous appelez ces méthodes a une portée de nom XAML, les méthodes font les appels au sein des méthodes de la portée de nom XAML appropriée. Sinon, l’élément parent est vérifié pour voir s’il détient une portée de nom XAML, et ce processus continue de manière récursive jusqu’à ce qu’une portée de nom XAML soit trouvée (en raison du comportement du processeur XAML, la présence d’une portée de nom XAML à la racine est garantie). <xref:System.Windows.FrameworkContentElement>a des comportements analogues, à l’exception qui aucun <xref:System.Windows.FrameworkContentElement> possédera jamais une portée de nom XAML. Les méthodes existent sur <xref:System.Windows.FrameworkContentElement> afin que les appels peuvent être transférés par la suite à un <xref:System.Windows.FrameworkElement> élément parent.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>est utilisé pour mapper une nouvelle portée de nom XAML à un objet existant. Vous pouvez appeler <xref:System.Windows.NameScope.SetNameScope%2A> plusieurs fois pour réinitialiser ou effacer le code XAML portée de nom, mais qui n’est pas une utilisation commune. En outre, <xref:System.Windows.NameScope.GetNameScope%2A> n’est pas généralement utilisé à partir du code.  
  
### <a name="xaml-namescope-implementations"></a>Implémentations de portée de nom XAML  
 Les classes suivantes implémentent <xref:System.Windows.Markup.INameScope> directement :  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>n’utilise pas de noms XAML ou les portées de nom ; Il utilise des clés à la place, car il s’agit d’une implémentation de dictionnaire. La seule raison pour laquelle <xref:System.Windows.ResourceDictionary> implémente <xref:System.Windows.Markup.INameScope> est afin qu’il peut lever des exceptions au code utilisateur qui aident à clarifier la distinction entre une portée de nom XAML true et la manière dont un <xref:System.Windows.ResourceDictionary> gère les clés et également pour vous assurer que les portées de nom XAML ne sont pas appliquées à un <xref:System.Windows.ResourceDictionary> par des éléments parents.  
  
 <xref:System.Windows.FrameworkTemplate>et <xref:System.Windows.Style> implémenter <xref:System.Windows.Markup.INameScope> via des définitions d’interface explicite. Les implémentations explicites permettent à ces portées de nom XAML se comportent de façon conventionnelle lorsqu’ils sont accessibles via la <xref:System.Windows.Markup.INameScope> interface, qui est la manière dont les portées de nom XAML sont communiquées par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] processus internes. Mais les définitions d’interface explicite ne font pas partie de la surface API classique de <xref:System.Windows.FrameworkTemplate> et <xref:System.Windows.Style>, car vous devrez rarement appeler le <xref:System.Windows.Markup.INameScope> méthodes sur <xref:System.Windows.FrameworkTemplate> et <xref:System.Windows.Style> directement et à la place utiliser une autre API comme <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Les classes suivantes définissent leur propre portée de nom XAML, à l’aide de la <xref:System.Windows.NameScope?displayProperty=nameWithType> classe d’assistance et en vous connectant à son implémentation de la portée de nom XAML via la <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> propriété attachée :  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Voir aussi  
 [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)  
 [x:Name, directive](../../../../docs/framework/xaml-services/x-name-directive.md)
