---
title: "Comment&#160;: naviguer vers l&#39;avant ou vers l&#39;arri&#232;re dans l&#39;historique de navigation | Microsoft Docs"
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
  - "history, navigation, naviguer vers l'avant"
  - "navigation, dans l'historique de navigation (vers l'avant)"
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: naviguer vers l&#39;avant ou vers l&#39;arri&#232;re dans l&#39;historique de navigation
Cet exemple montre comment naviguer vers l'avant ou vers le aux entrées dans l'historique de navigation.  
  
## Exemple  
 Le code qui s'exécute du contenu dans les hôtes suivants peuvent naviguer dans l'historique de navigation en accédant à avant ou arrière, une entrée à la fois.  
  
-   <xref:System.Windows.Navigation.NavigationWindow> à l'aide de <xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame> à l'aide de <xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 Avant de pouvoir accéder à l'entrée en avant, vous devez d'abord vérifier qu'il existe des entrées avant de l'historique de navigation en inspectant la propriété de **CanGoForward** .  Pour accéder à l'entrée en avant, vous appelez la méthode de **GoForward** .  L'exemple suivant illustre ce principe :  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 Avant de pouvoir naviguer vers l'arrière d'une entrée, vous devez d'abord vérifier qu'il existe des entrées dans l'historique de navigation arrière en inspectant la propriété de **CanGoBack** .  Pour naviguer vers l'arrière d'une entrée, appelez la méthode de **GoBack** .  L'exemple suivant illustre ce principe :  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**, **GoForward**, **CanGoBack**, et **GoBack** sont implémentés par <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, et <xref:System.Windows.Navigation.NavigationService>.  
  
> [!NOTE]
>  Si vous appelez **GoForward**, et il n'y a aucune entrée avant de l'historique de navigation, ou si vous appelez **GoBack**, et s'il n'y aucune entrée dans l'historique de navigation arrière, <xref:System.InvalidOperationException> est levée.