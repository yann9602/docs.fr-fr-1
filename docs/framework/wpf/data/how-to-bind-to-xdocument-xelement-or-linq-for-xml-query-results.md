---
title: "Comment&#160;: effectuer une liaison avec XDocument, XElement ou LINQ pour des r&#233;sultats de requ&#234;te XML | Microsoft Docs"
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
  - "liaison de données (WPF), lier à XDocument"
  - "liaison de données (WPF), lier à XElement"
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 21
---
# Comment&#160;: effectuer une liaison avec XDocument, XElement ou LINQ pour des r&#233;sultats de requ&#234;te XML
Cet exemple montre comment lier des données XML à un <xref:System.Windows.Controls.ItemsControl> au moyen d'un <xref:System.Xml.Linq.XDocument>.  
  
## Exemple  
 Le code XAML suivant définit un <xref:System.Windows.Controls.ItemsControl> et inclut un modèle de données pour les données de type `Planet` dans l'espace de noms XML `http://planetsNS`.  Un type de données XML qui occupe un espace de noms doit inclure l'espace de noms entre accolades et s'il apparaît là où une extension de balisage XAML pourrait apparaître, il doit précéder l'espace de noms avec une séquence d'échappement d'accolade.  Ce code effectue une liaison aux propriétés dynamiques qui correspondent aux méthodes <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> de la classe <xref:System.Xml.Linq.XElement>.  Les propriétés dynamiques permettent au XAML de créer une liaison avec les propriétés dynamiques qui partagent les noms de méthodes.  Pour en savoir plus, consultez [Propriétés dynamiques de LINQ to XML](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md).  Notez la manière dont la déclaration d'espace de noms par défaut pour le XML ne s'applique pas aux noms d'attribut.  
  
 [!code-xml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 Le code C\# suivant appelle <xref:System.Xml.Linq.XDocument.Load%2A> et définit le contexte des données du panneau d’empilement à tous les sous\-éléments de l'élément nommé `SolarSystemPlanets` dans l'espace de noms XML `http://planetsNS`.  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 Les données XML peuvent être stockées comme une ressource XAML en utilisant <xref:System.Windows.Data.ObjectDataProvider>.  Pour obtenir un exemple complet, consultez [Code source L2DBForm.xaml](../Topic/L2DBForm.xaml%20Source%20Code.md).  L'exemple suivant montre comment le code peut définir le contexte de données sur une ressource d'objet.  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 Les propriétés dynamiques qui effectuent un mappage vers <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> fournissent une grande souplesse au XAML.  Votre code peut également créer une liaison avec les résultats d'une requête LINQ pour XML.  Cet exemple crée une liaison avec les résultats de la requête classés par une valeur d'élément.  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## Voir aussi  
 [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [Vue d'ensemble de la liaison de données WPF avec LINQ to XML](../Topic/WPF%20Data%20Binding%20with%20LINQ%20to%20XML%20Overview.md)   
 [Exemple de liaison de données WPF à l'aide de LINQ to XML](../Topic/WPF%20Data%20Binding%20Using%20LINQ%20to%20XML%20Example.md)   
 [Propriétés dynamiques de LINQ to XML](../Topic/LINQ%20to%20XML%20Dynamic%20Properties.md)