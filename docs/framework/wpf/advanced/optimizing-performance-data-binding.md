---
title: "Optimisation des performances&#160;: liaison de donn&#233;es | Microsoft Docs"
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
  - "lier des données, performances"
  - "liaison de données, performances"
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Optimisation des performances&#160;: liaison de donn&#233;es
La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] offre un moyen simple et cohérent aux applications de présenter et d'interagir avec les données.  Les éléments peuvent être liés aux données de diverses sources de données sous la forme d'objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Cette rubrique fournit des recommandations sur les performances de la liaison de données.  
  
   
  
<a name="HowDataBindingReferencesAreResolved"></a>   
## Comment sont résolues les références de liaison de données  
 Avant de discuter des problèmes de performances des liaisons de données, il est utile d'explorer comment le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] résout des références d'objet pour la liaison.  
  
 La source d'une liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] peut être tout objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Vous pouvez créer une liaison avec des propriétés, sous\-propriétés ou indexeurs d'un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Les références de liaison sont résolues en utilisant la réflexion [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] ou un <xref:System.ComponentModel.ICustomTypeDescriptor>.  Voici trois méthodes permettant de résoudre des références d'objet pour la liaison.  
  
 La première méthode implique l'utilisation de la réflexion.  Dans ce cas, l'objet <xref:System.Reflection.PropertyInfo> est utilisé pour découvrir les attributs de la propriété et fournit l'accès aux métadonnées de propriété.  Lors de l'utilisation de l'interface <xref:System.ComponentModel.ICustomTypeDescriptor>, le moteur de liaison de données utilise cette interface pour accéder aux valeurs de propriété.  L'interface <xref:System.ComponentModel.ICustomTypeDescriptor> est particulièrement utile dans les cas où l'objet n'a pas de jeu statique de propriétés.  
  
 Les notifications de modification des propriétés peuvent être fournies en implémentant l'interface <xref:System.ComponentModel.INotifyPropertyChanged> ou en utilisant les notifications de modification associées au <xref:System.ComponentModel.TypeDescriptor>.  Toutefois, la stratégie privilégiée pour implémenter les notifications de modification des propriétés est d'utiliser <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Si l'objet source est un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] et que la propriété source est une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], le moteur de liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] doit utiliser en premier la réflexion sur l'objet source pour obtenir le <xref:System.ComponentModel.TypeDescriptor>, puis effectuer une requête pour un <xref:System.ComponentModel.PropertyDescriptor>.  Cette séquence d'opérations de réflexion peut potentiellement prendre beaucoup de temps d'une perspective de performance.  
  
 La deuxième méthode pour résoudre des références d'objet implique un objet source [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui implémente l'interface <xref:System.ComponentModel.INotifyPropertyChanged>, et une propriété source qui est une propriété [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Dans ce cas, le moteur de liaison de données utilise directement la réflexion sur le type de source et obtient la propriété requise.  Ce n'est pas encore la méthode optimale, mais elle sera plus avantageuse en terme de spécifications de jeu de travail que la première méthode.  
  
 La troisième méthode pour résoudre des références d'objet implique un objet source <xref:System.Windows.DependencyObject> et une propriété source <xref:System.Windows.DependencyProperty>.  Dans ce cas, le moteur de liaison de données n'a pas besoin d'utiliser la réflexion.  À la place, le moteur de propriété et le moteur de liaison de données résolvent ensemble la référence de propriété de manière indépendante.  C'est la méthode optimale pour résoudre des références d'objet utilisées pour la liaison de données.  
  
 La table suivante compare la vitesse des données liant la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> de mille éléments <xref:System.Windows.Controls.TextBlock> utilisant ces trois méthodes.  
  
|**Liaison de la propriété Text d'un TextBlock**|**Temps de liaison \(ms\)**|**Temps de rendu \-\- inclut la liaison \(ms\)**|  
|-----------------------------------------------------|---------------------------------|------------------------------------------------------|  
|Sur la propriété d'un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]|115|314|  
|Sur une propriété d'un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui implémente <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Sur une <xref:System.Windows.DependencyProperty> d'un <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## Liaison à des grands objets CLR  
 Il y a un impact sur les performances significatif lorsque vous liez les données avec un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] unique avec des milliers de propriétés.  Vous pouvez réduire cet impact en divisant l'objet unique en plusieurs objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] avec moins de propriétés.  La table montre les temps de liaison et de rendu pour la liaison de données avec un grand objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] unique contre plusieurs objets plus petits.  
  
|**Liaison de données de 1000 objets TextBlock**|**Temps de liaison \(ms\)**|**Temps de rendu \-\- inclut la liaison \(ms\)**|  
|-----------------------------------------------------|---------------------------------|------------------------------------------------------|  
|Sur un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] avec 1000 propriétés|950|1200|  
|Sur 1000 objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] avec une propriété|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## Liaison sur un objet ItemsSource  
 Considérez un scénario dans lequel vous avez un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> qui comporte une liste d'employés que vous souhaitez afficher dans <xref:System.Windows.Controls.ListBox>.  Pour créer une correspondance entre ces deux objets, vous devrez lier votre liste d'employés à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListBox>.  Toutefois, supposez qu'un nouvel employé a rejoint votre groupe.  Vous pouvez penser que pour insérer cette nouvelle personne dans vos valeurs <xref:System.Windows.Controls.ListBox> limitées, il vous suffirait d'ajouter cette personne à votre liste d'employés et d'attendre que cette modification soit reconnue automatiquement par le moteur de liaison de données.  Cette hypothèse vous prouverait le contraire ; en réalité, la modification ne se sera pas répercutée automatiquement dans la <xref:System.Windows.Controls.ListBox>.  La raison est que l'objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> ne déclenche pas automatiquement de collection d'événement modifié.  Afin que la <xref:System.Windows.Controls.ListBox> récupère les modifications, vous devriez recréer votre liste d'employés et la rattacher à la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListBox>.  Bien que cette solution fonctionne, elle engendre un impact énorme sur les performances.  Chaque fois vous réaffectez le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListBox> à un nouvel objet, la <xref:System.Windows.Controls.ListBox> rejette d'abord ses éléments précédents et régénère sa liste entière.  L'impact sur les performances est accru si votre <xref:System.Windows.Controls.ListBox> mappe sur un <xref:System.Windows.DataTemplate> complexe.  
  
 Une solution très efficace à ce problème est de transformer votre liste d'employés en <xref:System.Collections.ObjectModel.ObservableCollection%601>.  Un objet <xref:System.Collections.ObjectModel.ObservableCollection%601> déclenche une notification de modification que le moteur de liaison de données peut recevoir.  L'événement ajoute ou supprime un élément d'un <xref:System.Windows.Controls.ItemsControl> sans qu'il soit nécessaire de régénérer la liste entière.  
  
 La table suivante montre le temps qu'il faut pour mettre à jour la <xref:System.Windows.Controls.ListBox> \(avec la virtualization d'interface utilisateur désactivés\) lorsqu'un élément est ajouté.  Le nombre dans la première ligne représente le temps écoulé lorsque l'objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]<xref:System.Collections.Generic.List%601>est lié au <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de l'élément <xref:System.Windows.Controls.ListBox>.  Le nombre dans la deuxième ligne représente le temps écoulé lorsqu'une <xref:System.Collections.ObjectModel.ObservableCollection%601> est liée au <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de l'élément <xref:System.Windows.Controls.ListBox>.  Notez les gains de temps significatifs à l'aide de la stratégie de liaison de données <xref:System.Collections.ObjectModel.ObservableCollection%601>.  
  
|**Liaison de données de l'ItemsSource**|**Temps de mise à jour pour 1 élément \(ms\)**|  
|---------------------------------------------|----------------------------------------------------|  
|Sur un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601>|1656|  
|Sur une <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## Lier IList à ItemsControl non IEnumerable  
 Si vous avez le choix entre lier un <xref:System.Collections.Generic.IList%601> ou un <xref:System.Collections.IEnumerable> à un objet <xref:System.Windows.Controls.ItemsControl>, choisissez l'objet <xref:System.Collections.Generic.IList%601>.  La liaison de <xref:System.Collections.IEnumerable> sur un <xref:System.Windows.Controls.ItemsControl> force [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à créer un objet <xref:System.Collections.Generic.IList%601> de wrapper, ce qui signifie que vos performances subissent l'impact du traitement inutile d'un deuxième objet.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## Ne convertissez pas d'objets CLR en XML seulement pour la liaison de données.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous autorise à lier des données sur du contenu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] ; toutefois, la liaison de données sur du contenu [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] est plus lente que la liaison de données sur des objets [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)].  Ne convertissez pas de données d'objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] en XML si le seul but est pour la liaison de données.  
  
## Voir aussi  
 [Optimisation des performances des applications WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)   
 [Planification des performances des applications](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)   
 [Tirer parti du matériel](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)   
 [Disposition et conception](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)   
 [Graphiques 2D et acquisition d'images](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)   
 [Comportement d'objets](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)   
 [Ressources d'application](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)   
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)   
 [Autres recommandations relatives aux performances](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Procédure pas à pas : mise en cache de données d'application dans une application WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)