---
title: "Comment : obtenir et définir la fenêtre principale de l’Application"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows objects [WPF], setting
- setting windows objects [WPF]
- windows objects [WPF], getting
- getting windows objects [WPF]
ms.assetid: ec902bc4-4a59-46f5-8ec1-963b46789356
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d6bca158172fd3fc31526287c6d4a9928a8ea0c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-get-and-set-the-main-application-window"></a><span data-ttu-id="887f8-102">Comment : obtenir et définir la fenêtre principale de l’Application</span><span class="sxs-lookup"><span data-stu-id="887f8-102">How to: Get and Set the Main Application Window</span></span>
<span data-ttu-id="887f8-103">Cet exemple montre comment obtenir et définir la fenêtre d’application principale.</span><span class="sxs-lookup"><span data-stu-id="887f8-103">This example shows how to get and set the main application window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="887f8-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="887f8-104">Example</span></span>  
 <span data-ttu-id="887f8-105">La première <xref:System.Windows.Window> qui est instancié dans un [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application est automatiquement définie par <xref:System.Windows.Application> en tant que fenêtre d’application principale.</span><span class="sxs-lookup"><span data-stu-id="887f8-105">The first <xref:System.Windows.Window> that is instantiated within a [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] application is automatically set by <xref:System.Windows.Application> as the main application window.</span></span> <span data-ttu-id="887f8-106">La première <xref:System.Windows.Window> pour être instancié sera certainement la fenêtre qui est spécifiée comme le démarrage [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (voir <xref:System.Windows.Application.StartupUri%2A>).</span><span class="sxs-lookup"><span data-stu-id="887f8-106">The first <xref:System.Windows.Window> to be instantiated will most likely be the window that is specified as the startup [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] (see <xref:System.Windows.Application.StartupUri%2A>).</span></span>  
  
 <span data-ttu-id="887f8-107">Le premier <xref:System.Windows.Window> peut également être instancié à l’aide de code.</span><span class="sxs-lookup"><span data-stu-id="887f8-107">The first <xref:System.Windows.Window> could also be instantiated using code.</span></span> <span data-ttu-id="887f8-108">Par exemple ouvre une fenêtre pendant le démarrage de l’application, comme suit :</span><span class="sxs-lookup"><span data-stu-id="887f8-108">One example is opening a window during application startup, like the following:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/App.xaml.cs#firstwindowusingcodecodebehind)]
 [!code-vb[HOWTOWindowManagementSnippets#FirstWindowUsingCodeCODEBEHIND](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/application.xaml.vb#firstwindowusingcodecodebehind)]  
  
 <span data-ttu-id="887f8-109">Parfois, le premier instancié <xref:System.Windows.Window> n’est pas réellement dans la fenêtre principale de l’application par exemple, un écran de démarrage.</span><span class="sxs-lookup"><span data-stu-id="887f8-109">Sometimes, the first instantiated <xref:System.Windows.Window> is not actually the main application window e.g. a splash screen.</span></span> <span data-ttu-id="887f8-110">Dans ce cas, vous pouvez spécifier la fenêtre principale de l’application à l’aide de la balise, comme suit :</span><span class="sxs-lookup"><span data-stu-id="887f8-110">In this case, you can specify the main application window using markup, like the following:</span></span>  
  
 [!code-xaml[ApplicationMainWindowSnippets#SetApplicationMainWindowXAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/ApplicationMainWindowSnippets/XAML/App.xaml#setapplicationmainwindowxaml)]  
  
 <span data-ttu-id="887f8-111">Si la fenêtre principale est spécifiée automatiquement ou manuellement, vous pouvez obtenir la fenêtre principale à partir de <xref:System.Windows.Application.MainWindow%2A> utilisant le code suivant, comme suit :</span><span class="sxs-lookup"><span data-stu-id="887f8-111">Whether the main window is specified automatically or manually, you can get the main window from <xref:System.Windows.Application.MainWindow%2A> using the following code, like the following:</span></span>  
  
 [!code-csharp[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ApplicationMainWindowSnippets/CSharp/App.xaml.cs#getapplicationmainwindowcode)]
 [!code-vb[ApplicationMainWindowSnippets#GetApplicationMainWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ApplicationMainWindowSnippets/visualbasic/application.xaml.vb#getapplicationmainwindowcode)]
