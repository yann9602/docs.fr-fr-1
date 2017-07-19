---
title: "Proc&#233;dure&#160;: lier des donn&#233;es aux &#233;l&#233;ments Windows Presentation Foundation (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "liaison de données, Services de données WCF"
  - "Services de données WCF, liaison de données"
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: lier des donn&#233;es aux &#233;l&#233;ments Windows Presentation Foundation (WCF Data Services)
Avec [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], vous pouvez lier des éléments WPF \(Windows Presentation Foundation\) tels qu'un <xref:System.Windows.Controls.ListBox>`` ou <xref:System.Windows.Controls.ComboBox> à une instance de <xref:System.Data.Services.Client.DataServiceCollection%601>, qui gère les événements déclenchés par les contrôles pour garder <xref:System.Data.Services.Client.DataServiceContext> synchronisé avec les modifications apportées aux données dans les contrôles.  Pour plus d'informations, consultez [Liaison de données aux contrôles](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement.  Ce service et les classes de données clientes sont créés lorsque vous complétez le [démarrage rapide WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## Exemple  
 L'exemple suivant provient de la page code\-behind d'une page XAML \(Extensible Application Markup Language\) qui définit la fenêtre `SalesOrders` dans WPF.  Lorsque la fenêtre est chargée, <xref:System.Data.Services.Client.DataServiceCollection%601> est créé à partir du résultat d'une requête qui retourne des clients, filtrée par pays.  Toutes les pages de ce résultat paginé sont chargées ainsi que les ordres connexes, et sont liées à la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.StackPanel> qui est le contrôle de disposition racine pour la fenêtre WPF.  Pour plus d'informations, consultez [Chargement de contenu différé](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## Exemple  
 Le code XAML suivant définit la fenêtre `SalesOrders` dans WPF pour l'exemple précédent.  
  
 [!code-xml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## Exemple  
 L'exemple suivant provient de la page code\-behind d'une page XAML \(Extensible Application Markup Language\) qui définit la fenêtre `SalesOrders` dans WPF.  Lorsque la fenêtre est chargée, <xref:System.Data.Services.Client.DataServiceCollection%601> est créé à partir du résultat d'une requête qui retourne des clients avec les objets connexes, filtrée par pays.  Ce résultat est lié à la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> du <xref:System.Windows.Controls.StackPanel> qui est le contrôle de disposition racine pour la fenêtre WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## Exemple  
 Le code XAML suivant définit la fenêtre `SalesOrders` dans WPF pour l'exemple précédent.  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]