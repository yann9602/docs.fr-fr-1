---
title: "Comment&#160;: effectuer une liaison &#224; des donn&#233;es XML &#224; l&#39;aide d&#39;un XMLDataProvider et de requ&#234;tes XPath | Microsoft Docs"
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
  - "liaison, à des données XML à l'aide de requêtes XmlDataProvider"
  - "liaison de données, liaison à des données XML à l'aide de requêtes XmlDataProvider"
  - "XmlDataProvider, liaison à des données XML"
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: effectuer une liaison &#224; des donn&#233;es XML &#224; l&#39;aide d&#39;un XMLDataProvider et de requ&#234;tes XPath
Cet exemple montre comment effectuer une liaison à des données [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] à l'aide d'un <xref:System.Windows.Data.XmlDataProvider>.  
  
 Avec un <xref:System.Windows.Data.XmlDataProvider>, les données sous\-jacentes accessibles via la liaison de données dans votre application peuvent correspondre à n'importe quelle arborescence de nœuds [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)].  Autrement dit, un <xref:System.Windows.Data.XmlDataProvider> offre un moyen commode d'utiliser n'importe quelle arborescence de nœuds [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] en tant que [source de liaison](GTMT).  
  
## Exemple  
 Dans l'exemple suivant, les données sont directement incorporées en tant qu' [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] *îlot de données* dans la section <xref:System.Windows.FrameworkElement.Resources%2A>.  Un [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] îlot de données doit être encapsulé dans des balises `<x:XData>` et toujours avoir un nœud racine unique, qui est *Inventory* dans cet exemple.  
  
> [!NOTE]
>  Le nœud racine des données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] a un attribut **xmlns** qui définit l'espace de noms [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] à l'aide d'une chaîne vide.  Il s'agit d'une spécification pour l'application des requêtes XPath à un îlot de données qui est inline dans la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  Dans ce cas inline, le [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] \(et par conséquent, l'îlot de données\) hérite de l'espace de noms <xref:System.Windows>.  Vous devez donc définir un espace de noms vide pour que les requêtes XPath ne soient pas qualifiées par l'espace de noms <xref:System.Windows>, ce qui risque de mal orienter les requêtes.  
  
 [!code-xml[XMLDataSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 Comme le montre cet exemple, pour créer la même déclaration de liaison dans la syntaxe d'attributs, vous devez effectuer une séquence correcte d'échappement de caractères spéciaux.  Pour plus d'informations, consultez [Entités de caractères XML et XAML](../../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md).  
  
 La <xref:System.Windows.Controls.ListBox> affichera les éléments suivants lors de l'exécution de cet exemple.  Il s'agit des titres \(*Title*s\) de tous les éléments sous *Books* ayant une valeur *Stock* « *out* » ou une valeur *Number* de 3 ou supérieure ou égale à 8.  Notez qu'aucun élément *CD* élément n'est retourné parce que la valeur <xref:System.Windows.Data.XmlDataProvider.XPath%2A> définie sur le <xref:System.Windows.Data.XmlDataProvider> indique que seuls les éléments *Books* doivent être exposés \(ce qui définit essentiellement un filtre\).  
  
 ![Exemple XPath](../../../../docs/framework/wpf/data/media/xpathexample.png "XPathExample")  
  
 Dans cet exemple, les titres des ouvrages sont affichés car le <xref:System.Windows.Data.Binding.XPath%2A> de la liaison <xref:System.Windows.Controls.TextBlock> dans <xref:System.Windows.DataTemplate> a la valeur « *Titre* ».  Si vous voulez afficher la valeur d'un attribut, tel que *ISBN*, vous devez attribuer au <xref:System.Windows.Data.Binding.XPath%2A> la valeur « `@ISBN` ».  
  
 Les propriétés **XPath** dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont gérées par la méthode XmlNode.SelectNodes.  Vous pouvez modifier les requêtes **XPath** pour obtenir des résultats différents.  Voici quelques exemples de la requête <xref:System.Windows.Data.Binding.XPath%2A> sur l'élément lié <xref:System.Windows.Controls.ListBox> provenant de l'exemple précédent :  
  
-   `XPath="Book[1]"` retournera le premier élément du livre \(« XML en action »\).  Notez que les index **XPath** sont basés sur 1, et non pas sur 0.  
  
-   `XPath="Book[@*]"` retournera tous les éléments de livre avec tout attribut.  
  
-   `XPath="Book[last()-1]"` retournera l'avant dernier élément du livre \(« Présentation de Microsoft .NET »\).  
  
-   `XPath="*[position()>3]"` retournera tous les éléments du livre, sauf les trois premiers.  
  
 Lorsque vous exécutez une requête **XPath**, il retourne un <xref:System.Xml.XmlNode> ou une liste de XmlNodes.  <xref:System.Xml.XmlNode> est un objet [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)], ce qui signifie que vous pouvez utiliser la propriété <xref:System.Windows.Data.Binding.Path%2A> pour créer une liaison avec les propriétés [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)].  Reprenons l'exemple précédent.  Si le reste de l'exemple reste inchangé et que vous remplacez la liaison <xref:System.Windows.Controls.TextBlock> par ce qui est indiqué, vous verrez les noms des XmlNodes retournés dans la <xref:System.Windows.Controls.ListBox>.  Dans ce cas, le nom de tous les nœuds retournés est « *Livre* ».  
  
 [!code-xml[XmlDataSourceVariation#XmlNodePath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 Pour certaines applications, l'incorporation du code [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] en tant qu'îlot de données dans la page [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] source peut être gênante parce que le contenu exact des données doit être connu au moment de la compilation.  Par conséquent, l'obtention des données à partir d'un fichier [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] externe est également prise en charge, comme dans l'exemple suivant :  
  
 [!code-xml[XMLDataSource2#XmlFileExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 Si les données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] résident dans un fichier [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] distant, définissez l'accès aux données en assignant une [!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)] appropriée à l'attribut <xref:System.Windows.Data.XmlDataProvider.Source%2A> comme suit :  
  
```  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## Voir aussi  
 <xref:System.Windows.Data.ObjectDataProvider>   
 [Effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)   
 [Utiliser le modèle maître\/détail avec des données XML hiérarchiques](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)   
 [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Rubriques Comment](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)