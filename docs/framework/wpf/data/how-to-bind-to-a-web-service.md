---
title: "Comment&#160;: effectuer une liaison &#224; un service Web | Microsoft Docs"
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
  - "lier des données, service Web"
  - "liaison de données, service Web"
  - "service Web (liaison)"
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: effectuer une liaison &#224; un service Web
Cet exemple montre comment effectuer des liaisons à des objets retournés par des appels à des méthodes service Web.  
  
## Exemple  
 Cet exemple utilise [MSDN\/TechNet Publishing System \(MTPS\) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) pour récupérer la liste des langues prises en charge par un document spécifié.  
  
 Avant d'appeler un service Web, vous devez créer une référence pour ce service.  Pour créer une référence Web au service MTPS à l'aide de [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], exécutez les étapes suivantes :  
  
1.  Ouvrez votre projet dans [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter une référence Web**.  
  
3.  Dans la boîte de dialogue, tapez pour **URL** l'adresse [http:\/\/services.msdn.microsoft.com\/contentservices\/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4.  Cliquez sur **Aller à**, puis sur **Ajouter une référence**.  
  
 Ensuite, vous appelez la méthode service Web et affectez à <xref:System.Windows.FrameworkElement.DataContext%2A> de la fenêtre ou du contrôle approprié l'objet retourné.  La méthode **GetContent** du service MTPS transmet une référence à l'objet **getContentRequest**.  Par conséquent, l'exemple suivant établit d'abord un objet de requête :  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Une fois le <xref:System.Windows.FrameworkElement.DataContext%2A> défini, vous pouvez créer des liaisons avec les propriétés de l'objet définies pour le <xref:System.Windows.FrameworkElement.DataContext%2A>.  Dans cet exemple, le <xref:System.Windows.FrameworkElement.DataContext%2A> a la valeur de l'objet **getContentResponse** retourné par la méthode **GetContent**.  Dans l'exemple suivant, le <xref:System.Windows.Controls.ItemsControl> effectue une liaison aux valeurs **locale** de **availableVersionsAndLocales** de **getContentResponse**, et les affiche.  
  
 [!code-xml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Pour plus d'informations sur la structure de **getContentResponse**, consultez [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## Voir aussi  
 [Vue d'ensemble de la liaison de données](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [Vue d'ensemble des sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [Rendre des données disponibles pour la liaison en XAML](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)