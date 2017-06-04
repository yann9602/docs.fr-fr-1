---
title: "Transmission d&#39;un URI au Windows Runtime | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Windows Runtime, prise en charge par le .NET Framework"
  - "Windows Runtime, transmission d’un URI"
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# Transmission d&#39;un URI au Windows Runtime
Les méthodes Windows Runtime n'acceptent que des URI absolus. Si vous transmettez un URI relatif à une méthode [!INCLUDE[wrt](../../../includes/wrt-md.md)], une exception <xref:System.ArgumentException> est levée. En effet, quand vous utilisez le [!INCLUDE[wrt](../../../includes/wrt-md.md)] dans du code .NET Framework, la classe [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) apparaît comme <xref:System.Uri?displayProperty=fullName> dans IntelliSense. La classe <xref:System.Uri?displayProperty=fullName> autorise les URI relatifs, contrairement à la classe [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376). Il en va de même pour les méthodes que vous exposez dans les composants [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=fullName>. Toutefois, pour les utilisateurs de votre composant, la signature inclut [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376). Un URI transmis à votre composant doit être un URI absolu.  
  
 Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.  
  
## Détection et utilisation d'un URI absolu  
 Utilisez la propriété <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=fullName> pour vous assurer qu'un URI est absolu avant de le transmettre au [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.  
  
## Utilisation d'un URI absolu pour une ressource dans le package d'application  
 Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.  
  
 L’exemple suivant montre comment affecter à la propriété [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) pour un contrôle [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) et à la propriété [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) pour un contrôle [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) des ressources contenues dans un dossier nommé Pages, à l’aide de XAML et de code.  
  
 [!code-xml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Pour plus d’informations sur ces schémas, consultez [Schémas URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) dans le Centre de développement Windows.  
  
## Voir aussi  
 [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)