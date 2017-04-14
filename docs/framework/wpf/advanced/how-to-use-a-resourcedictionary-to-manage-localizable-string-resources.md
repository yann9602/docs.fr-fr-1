---
title: "Comment&#160;: utiliser un ResourceDictionary pour g&#233;rer des ressources de type cha&#238;ne localisables | Microsoft Docs"
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
  - "localisation (WPF), empaqueter des ressources chaîne"
  - "empaqueter des ressources chaîne"
  - "ResourceDictionary (WPF)"
  - "ressources (WPF), empaqueter des ressources chaîne"
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# Comment&#160;: utiliser un ResourceDictionary pour g&#233;rer des ressources de type cha&#238;ne localisables
Cet exemple indique comment utiliser un <xref:System.Windows.ResourceDictionary> pour empaqueter des ressources de type chaîne localisables pour des applications [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].  
  
### Pour utiliser un ResourceDictionary pour gérer des ressources de type chaîne localisables  
  
1.  Créez un <xref:System.Windows.ResourceDictionary> qui contient les chaînes à localiser.  Le code suivant est fourni à titre d'exemple.  
  
     [!code-xml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     Ce code définit une ressource de chaîne, `localizedMessage`, de type <xref:System.String>, à partir de l'espace de noms <xref:System> dans mscorlib.dll.  
  
2.  Ajoutez le <xref:System.Windows.ResourceDictionary> à votre application à l'aide du code suivant.  
  
     [!code-xml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  Utilisez la ressource de chaîne à partir du balisage à l'aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme suit.  
  
     [!code-xml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  Utilisez la ressource de chaîne de code\-behind à l'aide de code comme suit.  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  Localisez l'application.  Pour plus d'informations, consultez [Localiser une application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).