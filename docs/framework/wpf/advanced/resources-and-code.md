---
title: "Ressources et code | Microsoft Docs"
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
  - "clés, utiliser des objets en tant que"
  - "code procédural, accéder à des ressources à partir de"
  - "code procédural, créer des ressources avec"
  - "ressources, accéder à partir de code procédural"
  - "ressources, créer avec du code procédural"
ms.assetid: c1cfcddb-e39c-41c8-a7f3-60984914dfae
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# Ressources et code
Cette vue d'ensemble est consacrée à la possibilité d'utiliser ou de créer des ressources [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] en utilisant du code et non la syntaxe [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  Pour plus d'informations sur l'utilisation des ressources en général et sur les ressources d'un point de vue de la syntaxe [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], consultez [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
   
  
<a name="accessing"></a>   
## Accès aux ressources à partir du code  
 Les clés qui identifient les ressources si elles sont définies via [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] servent également à récupérer des ressources spécifiques si vous les demandez dans du code.  La façon la plus simple de récupérer une ressource depuis le code est d'appeler la méthode <xref:System.Windows.FrameworkElement.FindResource%2A> ou <xref:System.Windows.FrameworkElement.TryFindResource%2A> à partir d'objets d'infrastructure de votre application.  Ces méthodes diffèrent au niveau de leur comportement lorsque la clé demandée est introuvable.  <xref:System.Windows.FrameworkElement.FindResource%2A> lève une exception ; <xref:System.Windows.FrameworkElement.TryFindResource%2A> ne lève pas d'exception mais renvoie `null`.  Chaque méthode prend la clé de ressource comme paramètre d'entrée et retourne un objet faiblement typé.  Une clé de ressource est généralement un chaîne mais il arrive que ce ne soit pas le cas ; consultez la section [Utilisation d'objets comme clés](#objectaskey) pour plus de détails.  En principe, vous devez convertir l'objet retourné dans le type requis par la propriété que vous définissez lorsque vous demandez la ressource.  La logique de recherche pour la résolution d'une ressource du code est la même que dans le cas d'une référence de ressource dynamique [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  La recherche des ressources part de l'élément appelant et continue sur les éléments parents successifs de l'[arborescence logique](GTMT).  Si nécessaire, la recherche se poursuit sur les ressources de l'application, les thèmes et les ressources du système.  Une demande de ressource effectuée par code tiendra compte des modifications intervenues lors de l'exécution dans les dictionnaires de ressources qui peuvent être ultérieures au chargement de ce dictionnaire par [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], ainsi que des modifications des ressources du système en temps réel.  
  
 Voici un bref exemple de code qui recherche une ressource par clé et utilise la valeur retournée pour définir une propriété implémentée en tant que gestionnaire d'événements <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
 [!code-csharp[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertiesOvwSupport/CSharp/page3.xaml.cs#resourceproceduralget)]
 [!code-vb[PropertiesOvwSupport#ResourceProceduralGet](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertiesOvwSupport/visualbasic/page3.xaml.vb#resourceproceduralget)]  
  
 Une autre méthode d'assignation d'une référence de ressource est <xref:System.Windows.FrameworkElement.SetResourceReference%2A>.  Cette méthode prend deux paramètres : la clé de la ressource et l'identificateur d'une propriété de dépendance particulière qui est présente sur l'instance de l'élément auquel la valeur de ressource doit être assignée.  Cette méthode est identique fonctionnellement et offre l'avantage de ne pas nécessiter de conversion des valeurs de retour.  
  
 Il existe encore une autre façon d'accéder aux ressources par programme : en accédant au contenu de la propriété <xref:System.Windows.FrameworkElement.Resources%2A> comme dictionnaire.  Accéder au dictionnaire contenu dans cette propriété vous permet également d'ajouter de nouvelles ressources aux collections existantes, de vérifier si un nom de clé donné est déjà pris dans la collection et d'effectuer d'autres opérations de dictionnaire\/collection.  Si vous écrivez une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entièrement en code, vous pouvez également créer toute la collection en code, lui assigner des clés, puis affecter la collection terminée à la propriété <xref:System.Windows.FrameworkElement.Resources%2A> d'un élément établi.  Cette tâche est décrite dans la section suivante.  
  
 Vous pouvez indexer n'importe quelle collection de <xref:System.Windows.FrameworkElement.Resources%2A> donnée en utilisant une clé spécifique comme index, mais en sachant que ce mode d'accès à la ressource ne suit pas les règles d'exécution normales de la résolution des ressources.  Vous n'accédez qu'à cette collection particulière.  La recherche de ressources ne s'étendra pas à la racine ou à l'application si aucun objet valide n'a été trouvé au niveau de la clé demandée.  Cependant, dans certains cas, cette approche peut offrir des avantages de performance précisément grâce au fait que la portée de la recherche de clé est plus restreinte.  Consultez la classe <xref:System.Windows.ResourceDictionary> pour plus de détails sur la façon de travailler directement avec le dictionnaire des ressources.  
  
<a name="creating"></a>   
## Création de ressources par code  
 Si vous voulez créer une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] entièrement avec du code, vous souhaitez probablement créer les ressources de cette application dans le code également.  Pour ce faire, créez une instance de <xref:System.Windows.ResourceDictionary>, puis ajoutez toutes les ressources de ce dictionnaire au moyen d'appels successifs de <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=fullName>.  Ensuite, utilisez le <xref:System.Windows.ResourceDictionary> ainsi créé pour définir la propriété <xref:System.Windows.FrameworkElement.Resources%2A> sur un élément qui est présent dans une portée de page, ou les <xref:System.Windows.Application.Resources%2A?displayProperty=fullName>.  Vous pourriez également gérer le <xref:System.Windows.ResourceDictionary> en tant qu'objet autonome sans l'ajouter à un élément.  Cependant, si vous procédez de cette façon, vous devez accéder aux ressources qu'il contient par clé d'élément, comme s'il s'agissait d'un dictionnaire générique.  Un <xref:System.Windows.ResourceDictionary> non attaché à une propriété `Resources` d'un élément ne ferait pas partie de l'arborescence des éléments et n'a pas de portée dans la séquence de recherche qui peut être utilisée par <xref:System.Windows.FrameworkElement.FindResource%2A> et des méthodes apparentées.  
  
<a name="objectaskey"></a>   
## Utilisation d'objets comme clés  
 Dans la plupart des cas d'utilisation des ressources, la clé de la ressource sera définie comme étant une chaîne.  Cependant, diverses fonctionnalités de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] n'utilisent délibérément pas un type de chaîne pour spécifier des clés, mais un objet.  La possibilité d'indexer une ressource à l'aide d'un objet est utilisée par la prise en charge des styles et des thèmes de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  Les styles des thèmes qui deviennent le style par défaut d'un contrôle auquel aucun style n'est explicitement affecté, sont indexés chacun par le <xref:System.Type> du contrôle auquel ils doivent s'appliquer.  L'indexation par le type fournit un mécanisme de recherche fiable qui fonctionne sur des instances par défaut de chaque type de contrôle, et le type peut être détecté par réflexion et servir pour affecter des styles à des classes dérivées même si le type dérivé n'a pas autrement de style par défaut.  Vous pouvez spécifier une clé <xref:System.Type> pour une ressource définie en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] au moyen de l'[x:Type, extension de balisage](../../../../docs/framework/xaml-services/x-type-markup-extension.md).  Il existe des extensions similaires pour d'autres utilisations de clés sans chaînes qui prennent en charge des fonctionnalités [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], telles que [ComponentResourceKey, extension de balisage](../../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).  
  
## Voir aussi  
 [Ressources XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [Application d'un style et création de modèles](../../../../docs/framework/wpf/controls/styling-and-templating.md)