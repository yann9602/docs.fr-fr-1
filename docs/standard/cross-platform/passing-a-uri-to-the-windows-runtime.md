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
# <a name="passing-a-uri-to-the-windows-runtime"></a><span data-ttu-id="4c3fa-102">Transmission d'un URI au Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="4c3fa-102">Passing a URI to the Windows Runtime</span></span>
<span data-ttu-id="4c3fa-103">Les méthodes Windows Runtime n'acceptent que des URI absolus.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-103">Windows Runtime methods accept only absolute URIs.</span></span> <span data-ttu-id="4c3fa-104">Si vous transmettez un URI relatif à une méthode [!INCLUDE[wrt](../../../includes/wrt-md.md)], une exception <xref:System.ArgumentException> est levée.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-104">If you pass a relative URI to a [!INCLUDE[wrt](../../../includes/wrt-md.md)] method, an <xref:System.ArgumentException> exception is thrown.</span></span> <span data-ttu-id="4c3fa-105">Voici pourquoi : lorsque vous utilisez la [!INCLUDE[wrt](../../../includes/wrt-md.md)] dans le code .NET Framework, le [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) classe apparaît sous la forme <xref:System.Uri?displayProperty=nameWithType> dans Intellisense.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-105">Here's why: When you use the [!INCLUDE[wrt](../../../includes/wrt-md.md)] in .NET Framework code, the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class appears as <xref:System.Uri?displayProperty=nameWithType> in Intellisense.</span></span> <span data-ttu-id="4c3fa-106">Le <xref:System.Uri?displayProperty=nameWithType> classe autorise les URI relatifs, mais la [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) n’est pas le cas de classe.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-106">The <xref:System.Uri?displayProperty=nameWithType> class allows relative URIs, but the [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) class does not.</span></span> <span data-ttu-id="4c3fa-107">Il en va de même pour les méthodes que vous exposez dans les composants [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c3fa-107">This is also true for methods you expose in [!INCLUDE[wrt](../../../includes/wrt-md.md)] Components.</span></span> <span data-ttu-id="4c3fa-108">Si votre composant expose une méthode qui prend un URI, la signature dans votre code inclut <xref:System.Uri?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-108">If your component exposes a method that takes a URI, the signature in your code includes <xref:System.Uri?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c3fa-109">Toutefois, pour les utilisateurs de votre composant, la signature inclut [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span><span class="sxs-lookup"><span data-stu-id="4c3fa-109">However, to users of your component, the signature includes [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376).</span></span> <span data-ttu-id="4c3fa-110">Un URI transmis à votre composant doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-110">A URI that is passed to your component must be an absolute URI.</span></span>  
  
 <span data-ttu-id="4c3fa-111">Cette rubrique montre comment détecter un URI absolu et comment en créer un pendant le référencement d'une ressource dans le package d'application.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-111">This topic shows how to detect an absolute URI and how to create one when referring to a resource in the app package.</span></span>  
  
## <a name="detecting-and-using-an-absolute-uri"></a><span data-ttu-id="4c3fa-112">Détection et utilisation d'un URI absolu</span><span class="sxs-lookup"><span data-stu-id="4c3fa-112">Detecting and using an absolute URI</span></span>  
 <span data-ttu-id="4c3fa-113">Utilisez la propriété <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> pour vous assurer qu'un URI est absolu avant de le transmettre au [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4c3fa-113">Use the <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=nameWithType> property to ensure that a URI is absolute before passing it to the [!INCLUDE[wrt](../../../includes/wrt-md.md)].</span></span> <span data-ttu-id="4c3fa-114">Utiliser cette propriété est plus efficace qu'intercepter et gérer l'exception <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-114">Using this property is more efficient than catching and handling the <xref:System.ArgumentException> exception.</span></span>  
  
## <a name="using-an-absolute-uri-for-a-resource-in-the-app-package"></a><span data-ttu-id="4c3fa-115">Utilisation d'un URI absolu pour une ressource dans le package d'application</span><span class="sxs-lookup"><span data-stu-id="4c3fa-115">Using an absolute URI for a resource in the app package</span></span>  
 <span data-ttu-id="4c3fa-116">Si vous souhaitez spécifier un URI pour une ressource qui se trouve dans votre package d'application, vous pouvez utiliser le schéma `ms-appx` ou `ms-appx-web` pour créer un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-116">If you want to specify a URI for a resource that your app package contains, you can use the `ms-appx` or `ms-appx-web` scheme to create an absolute URI.</span></span>  
  
 <span data-ttu-id="4c3fa-117">L’exemple suivant montre comment définir la [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) propriété pour un [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) contrôle et la [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) propriété pour un [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) contrôle pour les ressources qui sont contenus dans un dossier nommé Pages, à l’aide de XAML et le code.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-117">The following example shows how to set the [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) property for a [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) control and the [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) property for an [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) control to resources that are contained in a folder named Pages, using both XAML and code.</span></span>  
  
 [!code-xaml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 <span data-ttu-id="4c3fa-118">Pour plus d’informations sur ces schémas, consultez [modèles URI](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) dans le centre de développement Windows.</span><span class="sxs-lookup"><span data-stu-id="4c3fa-118">For more information about these schemes, see [URI schemes](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c3fa-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c3fa-119">See Also</span></span>  
 [<span data-ttu-id="4c3fa-120">Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="4c3fa-120">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
