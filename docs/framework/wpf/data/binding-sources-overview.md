---
title: "Vue d&#39;ensemble des sources de liaison | Microsoft Docs"
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
  - "lier des données, sources de liaison"
  - "sources de liaison"
  - "liaison de données, source de liaison"
ms.assetid: 2df2cd11-6aac-4bdf-ab7b-ea5f464cd5ca
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# Vue d&#39;ensemble des sources de liaison
Dans la liaison de données, l'objet de [source de liaison](GTMT) fait référence à l'objet dont vous obtenez vos données.  Cette rubrique traite des types d'objets que vous pouvez utiliser comme source de liaison.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="binding_sources"></a>   
## Types de sources de liaison  
 La liaison de données [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge les types suivants de [sources de liaison](GTMT) :  
  
|Source de liaison|Description|  
|-----------------------|-----------------|  
|Objets [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]|Vous pouvez créer une liaison aux propriétés publiques, sous\-propriétés, ainsi qu'aux indexeurs de n'importe quel objet [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  Le moteur de liaison utilise la réflexion [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pour obtenir les valeurs des propriétés.  Des objets qui implémentent <xref:System.ComponentModel.ICustomTypeDescriptor> ou possèdent un <xref:System.ComponentModel.TypeDescriptionProvider> enregistré utilisent également le moteur de liaison.<br /><br /> Pour plus d'informations sur l'implémentation d'une classe qui peut servir de source de liaison, consultez [Implémentation d'une classe pour la source de liaison](#classes) plus loin dans cette rubrique.|  
|objets dynamiques|Vous pouvez créer une liaison aux propriétés et aux indexeurs disponibles d'un objet qui implémente l'interface <xref:System.Dynamic.IDynamicMetaObjectProvider>.  Si vous pouvez accéder au membre dans le code, vous pouvez le lier.  Par exemple, si un objet dynamique vous permet d'accéder à un membre dans le code via `someObjet.AProperty`, vous pouvez le lier en affectant au chemin d'accès de liaison la valeur `AProperty`.|  
|Objets [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)]|Vous pouvez créer une liaison avec les objets [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)], <xref:System.Data.DataTable> par exemple. [!INCLUDE[TLA2#tla_adonet](../../../../includes/tla2sharptla-adonet-md.md)] <xref:System.Data.DataView> implémente l'interface <xref:System.ComponentModel.IBindingList>, qui fournit des notifications de modification que le moteur de liaison écoute.|  
|Objets [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]|Vous pouvez créer une liaison aux requêtes `XPath` et les exécuter sur <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlDocument> ou <xref:System.Xml.XmlElement>.  Une manière pratique d'accéder aux données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] qui constituent la [source de liaison](GTMT) dans le balisage consiste à utiliser un objet <xref:System.Windows.Data.XmlDataProvider>.  Pour plus d'informations, consultez [Effectuer une liaison à des données XML à l'aide d'un XMLDataProvider et de requêtes XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).<br /><br /> Vous pouvez également créer une liaison à un <xref:System.Xml.Linq.XElement> ou un <xref:System.Xml.Linq.XDocument>, ou encore aux résultats de requêtes exécutées sur des objets de ces types à l'aide de LINQ to XML.  Une manière commode d'utiliser LINQ to XML pour accéder aux données XML qui constituent la source de liaison dans le balisage consiste à utiliser un objet <xref:System.Windows.Data.ObjectDataProvider>.  Pour plus d'informations, consultez [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).|  
|Objets <xref:System.Windows.DependencyObject>|Vous pouvez créer une liaison aux [propriétés de dépendance](GTMT) de tout élément <xref:System.Windows.DependencyObject>.  Pour obtenir un exemple, consultez [Lier les propriétés de deux contrôles](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).|  
  
<a name="classes"></a>   
## Implémentation d'une classe pour la source de liaison  
 Vous pouvez créer vos propres sources de liaison.  Cette section traite des aspects que vous devez connaître si vous implémentez une classe  pour servir de source de liaison.  
  
### Implémentation de notifications de modification  
 Si vous utilisez une liaison <xref:System.Windows.Data.BindingMode> ou <xref:System.Windows.Data.BindingMode> \(car vous souhaitez que votre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] soit mise à jour lorsque les propriétés de la source de liaison changent dynamiquement\), vous devez implémenter un mécanisme de notification de modification de propriété approprié.  Le mécanisme recommandé consiste pour la classe dynamique [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] à implémenter l'interface <xref:System.ComponentModel.INotifyPropertyChanged>.  Pour plus d'informations, consultez [Implémenter la notification des modifications de propriétés](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Si vous créez un objet [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] qui n'implémente pas <xref:System.ComponentModel.INotifyPropertyChanged>, vous devez alors faire en sorte que votre propre système de notification s'assure que les données utilisées dans une liaison demeurent à jour.  Vous pouvez fournir des notifications de modification en prenant en charge le modèle `PropertyChanged` pour chaque propriété pour laquelle vous souhaitez disposer de notifications de modification.  Pour prendre en charge ce modèle, vous définissez un événement modifié *NomPropriété* pour chaque propriété, *NomPropriété* étant le nom de la propriété.  Vous déclenchez l'événement chaque fois que la propriété est modifiée.  
  
 Si votre source de liaison implémente l'un de ces mécanismes de notification, les mises à jour des cibles sont effectuées automatiquement.  Si, pour quelque raison, votre source de liaison ne fournit pas de notifications de modification de propriété adéquates, vous pouvez utiliser la méthode <xref:System.Windows.Data.BindingExpression.UpdateTarget%2A> pour mettre à jour explicitement la propriété cible.  
  
### Autres caractéristiques  
 La liste suivante fournit d'autres points importants à noter :  
  
-   Si vous souhaitez créer l'objet en [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], la classe doit avoir un constructeur par défaut.  Dans certains langages [!INCLUDE[TLA2#tla_net](../../../../includes/tla2sharptla-net-md.md)], tels que [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], le constructeur par défaut peut être créé pour vous.  
  
-   Les propriétés que vous utilisez en tant que sources de liaison pour une liaison doivent être des propriétés publiques de votre classe.  Vous ne pouvez pas accéder à des propriétés d'interface définies explicitement à des fins de liaison, ni à des propriétés protégées, privées, internes ou virtuelles ne possédant pas d'implémentation de base.  
  
-   Vous ne pouvez pas créer de liaison aux champs publics.  
  
-   Le type de propriété déclaré dans votre classe est le type qui est passé à la liaison.  Toutefois, le type utilisé par la liaison dépend du type de la propriété [cible de liaison](GTMT), et non pas de la propriété de la source de liaison.  En cas de différence de type, vous pouvez écrire un convertisseur pour gérer la manière dont votre propriété personnalisée est passée initialement à la liaison.  Pour plus d'informations, consultez <xref:System.Windows.Data.IValueConverter>.  
  
<a name="objects"></a>   
## Objets entiers utilisés comme source de liaison  
 Vous pouvez utiliser un objet entier comme source de liaison.  Vous pouvez spécifier une source de liaison à l'aide de la propriété <xref:System.Windows.Data.Binding.Source%2A> ou <xref:System.Windows.FrameworkElement.DataContext%2A>, puis fournir une déclaration de liaison vierge : `{Binding}`.  Les scénarios dans lesquels cela est utile incluent les liaisons avec des objets de type chaîne, les liaisons avec des objets possédant plusieurs propriétés qui vous intéressent, ou les liaisons avec des objets de collection.  Pour obtenir un exemple de création d'une liaison avec un objet de collection entier, consultez [Utiliser le modèle maître\/détail avec des données hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).  
  
 Notez que vous devrez peut\-être appliquer une logique personnalisée afin que les données soient pertinentes pour votre propriété cible liée.  La logique personnalisée peut être sous la forme d'un convertisseur personnalisé \(si la conversion de type par défaut n'existe pas\) ou un <xref:System.Windows.DataTemplate>.  Pour plus d'informations sur les convertisseurs, consultez la section Conversion de données de [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  Pour plus d'informations sur les modèles de données, consultez [Vue d'ensemble des modèles de données](../../../../docs/framework/wpf/data/data-templating-overview.md).  
  
<a name="collections"></a>   
## Utilisation d'objets de collection utilisés comme source de liaison  
 Souvent, l'objet que vous souhaitez utiliser comme source de liaison est une collection d'objets personnalisés.  Chaque objet sert de source pour une instance d'une liaison répétée.  Par exemple, vous pouvez avoir une collection `CustomerOrders`, composée d'objets `CustomerOrder`, au sein de laquelle votre application itère pour déterminer le nombre d'ordres qui existent et les données que chacun contient.  
  
 Vous pouvez énumérer toute collection qui implémente l'interface <xref:System.Collections.IEnumerable>.  Toutefois, pour paramétrer des liaisons dynamiques afin que les insertions ou suppressions dans la collection mettent automatiquement à jour l'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], la collection doit implémenter l'interface <xref:System.Collections.Specialized.INotifyCollectionChanged>.  Cette interface expose un événement qui doit être déclenché à chaque fois que la collection sous\-jacente est modifiée.  
  
 La classe <xref:System.Collections.ObjectModel.ObservableCollection%601> fournit une implémentation intégrée d'une collection de données exposant l'interface <xref:System.Collections.Specialized.INotifyCollectionChanged>.  Les objets de données individuels dans la collection doivent satisfaire aux spécifications décrites dans les sections précédentes.  Pour obtenir un exemple, consultez [Créer et effectuer une liaison à un ObservableCollection](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md).  Avant d'implémenter votre propre collection, pensez à utiliser <xref:System.Collections.ObjectModel.ObservableCollection%601> ou l'une des classes de collection existantes, telles que <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601> et <xref:System.ComponentModel.BindingList%601>, entre autres.  
  
 Le WPF ne crée jamais directement une liaison avec une collection.  Si vous spécifiez une collection comme source de liaison, WPF crée en fait une liaison à l'affichage par défaut de la collection.  Pour plus d'informations sur les affichages par défaut, consultez [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
 Si vous avez un scénario avancé et que vous souhaitez implémenter votre propre collection, envisagez d'utiliser l'interface <xref:System.Collections.IList>.  <xref:System.Collections.IList> fournit une collection non générique d'objets individuellement accessibles par index, qui peut améliorer la performance.  
  
<a name="permissions"></a>   
## Besoins d'autorisation dans la liaison de données  
 Lors de la liaison de données, vous devez considérer le niveau de confiance de l'application.  Le tableau suivant résume quels types de propriété peuvent être liés dans une application qui s'exécute en mode confiance totale ou confiance partielle :  
  
|Type de propriété<br /><br /> \(tous les modificateurs d'accès\)|Propriété de l'objet dynamique|Propriété de l'objet dynamique|Propriété CLR|Propriété CLR|Propriété de dépendance|Propriété de dépendance|  
|--------------------------------------------------------------|------------------------------------|------------------------------------|-------------------|-------------------|-----------------------------|-----------------------------|  
|**Niveau de confiance**|**Confiance totale**|**Confiance partielle**|**Confiance totale**|**Confiance partielle**|**Confiance totale**|**Confiance partielle**|  
|Classe publique|Oui|Oui|Oui|Oui|Oui|Oui|  
|Classe non publique|Oui|Non|Oui|Non|Oui|Oui|  
  
 Ce tableau décrit les points importants suivants à propos des spécifications d'autorisation dans la liaison de données :  
  
-   Pour les propriétés [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)], la liaison de données fonctionne tant que le moteur de liaison est en mesure d'accéder à la propriété de la source de liaison à l'aide de la réflexion.  Sinon, le moteur de liaison émet un avertissement stipulant que la propriété est introuvable et utilise la valeur de secours ou celle par défaut, si elle est disponible.  
  
-   Vous pouvez créer une liaison aux propriétés sur des objets dynamiques définis au moment de la compilation ou de l'exécution.  
  
-   Vous pouvez toujours créer une liaison avec les [propriétés de dépendance](GTMT).  
  
 Le besoin d'autorisation pour la liaison [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] est similaire : dans un bac à sable \(sandbox\) de confiance partielle, <xref:System.Windows.Data.XmlDataProvider> échoue lorsqu'il ne possède pas d'autorisations pour accéder aux données spécifiées.  
  
 Les objets avec un type anonyme sont internes.  Vous pouvez créer uniquement une liaison aux propriétés de types anonymes lors du fonctionnement avec une confiance totale.  Pour plus d'informations sur les types anonymes, consultez [Types anonymes \(Guide de programmation C\#\)](../Topic/Anonymous%20Types%20\(C%23%20Programming%20Guide\).md) ou [Types anonymes \(Visual Basic\)](../Topic/Anonymous%20Types%20\(Visual%20Basic\).md) \(Visual Basic\).  
  
 Pour plus d'informations sur le niveau de sécurité de confiance partielle, consultez [Sécurité de confiance partielle de WPF](../../../../docs/framework/wpf/wpf-partial-trust-security.md).  
  
## Voir aussi  
 <xref:System.Windows.Data.ObjectDataProvider>   
 <xref:System.Windows.Data.XmlDataProvider>   
 [Spécifier la source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)   
 [Vue d'ensemble de la liaison de données WPF avec LINQ to XML](../Topic/WPF%20Data%20Binding%20with%20LINQ%20to%20XML%20Overview.md)   
 [Liaison de données](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)