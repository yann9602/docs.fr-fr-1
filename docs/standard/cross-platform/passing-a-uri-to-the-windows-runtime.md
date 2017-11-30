---
title: Transmission d'un URI au Windows Runtime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Runtime, .NET Framework support for
- Windows Runtime, passing a URI to
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4ef77fb9e196abf046e0d4648a49b5d4d3fad47e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="passing-a-uri-to-the-windows-runtime"></a>Transmission d'un URI au Windows Runtime
Les méthodes Windows Runtime n'acceptent que des URI absolus. Si vous transmettez un URI relatif à une méthode [!INCLUDE[wrt](../../../includes/wrt-md.md)], une exception <xref:System.ArgumentException> est levée. Voici pourquoi : lorsque vous utilisez la [!INCLUDE[wrt](../../../includes/wrt-md.md)] dans le code .NET Framework, le [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) classe apparaît sous la forme <xref:System.Uri?displayProperty=nameWithType> dans Intellisense. Le <xref:System.Uri?displayProperty=nameWithType> classe autorise les URI relatifs, mais la [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) n’est pas le cas de classe. Il en va de même pour les méthodes que vous exposez dans les composants [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=nameWithType>. Toutefois, pour les utilisateurs de votre composant, la signature inclut [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376). Un URI transmis à votre composant doit être un URI absolu.  
  
 Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.  
  
## <a name="detecting-and-using-an-absolute-uri"></a>Détection et utilisation d'un URI absolu  
 Utilisez la propriété <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> pour vous assurer qu'un URI est absolu avant de le transmettre au [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a>Utilisation d'un URI absolu pour une ressource dans le package d'application  
 Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.  
  
 L’exemple suivant montre comment définir la [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) propriété pour un [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) contrôle et la [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) propriété pour un [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) contrôle pour les ressources qui sont contenus dans un dossier nommé Pages, à l’aide de XAML et le code.  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 Pour plus d’informations sur ces schémas, consultez [modèles URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) dans le centre de développement Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
