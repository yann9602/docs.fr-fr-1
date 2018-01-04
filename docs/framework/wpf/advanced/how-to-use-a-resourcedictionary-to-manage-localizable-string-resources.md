---
title: "Guide pratique pour utiliser un ResourceDictionary pour gérer des ressources de type chaîne localisables"
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
- resources [WPF], packaging string resources
- packaging string resources [WPF]
- ResourceDictionary [WPF]
- localization [WPF], packaging string resources
ms.assetid: 19e7d9a5-20df-4ad3-b157-fe6515902e5e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fba115ea8c954da177afcacbf679f41474e2b68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="6eb9c-102">Guide pratique pour utiliser un ResourceDictionary pour gérer des ressources de type chaîne localisables</span><span class="sxs-lookup"><span data-stu-id="6eb9c-102">How to: Use a ResourceDictionary to Manage Localizable String Resources</span></span>
<span data-ttu-id="6eb9c-103">Cet exemple montre comment utiliser un <xref:System.Windows.ResourceDictionary> pour empaqueter des ressources chaîne localisable pour [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] applications.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-103">This example shows how to use a <xref:System.Windows.ResourceDictionary> to package localizable string resources for [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] applications.</span></span>  
  
### <a name="to-use-a-resourcedictionary-to-manage-localizable-string-resources"></a><span data-ttu-id="6eb9c-104">Pour utiliser un ResourceDictionary pour gérer des ressources de type chaîne localisables</span><span class="sxs-lookup"><span data-stu-id="6eb9c-104">To use a ResourceDictionary to manage localizable string resources</span></span>  
  
1.  <span data-ttu-id="6eb9c-105">Créer un <xref:System.Windows.ResourceDictionary> qui contient les chaînes que vous souhaitez localiser.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-105">Create a <xref:System.Windows.ResourceDictionary> that contains the strings you would like to localize.</span></span> <span data-ttu-id="6eb9c-106">Le code suivant fournit un exemple.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-106">The following code shows an example.</span></span>  
  
     [!code-xaml[StringLocalizationSample#StringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/StringResources.xaml#stringresourcedictionary)]  
  
     <span data-ttu-id="6eb9c-107">Ce code définit une ressource de chaîne, `localizedMessage`, de type <xref:System.String>, à partir de la <xref:System> espace de noms dans mscorlib.dll.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-107">This code defines a string resource, `localizedMessage`, of type <xref:System.String>, from the <xref:System> namespace in mscorlib.dll.</span></span>  
  
2.  <span data-ttu-id="6eb9c-108">Ajouter le <xref:System.Windows.ResourceDictionary> à votre application, utilisez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-108">Add the <xref:System.Windows.ResourceDictionary> to your application, using the following code.</span></span>  
  
     [!code-xaml[StringLocalizationSample#ReferencingStringResourceDictionary](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/App.xaml#referencingstringresourcedictionary)]  
  
3.  <span data-ttu-id="6eb9c-109">Utilisez la ressource de chaîne à partir du balisage, à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] comme suit.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-109">Use the string resource from markup, using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] like the following.</span></span>  
  
     [!code-xaml[StringLocalizationSample#GetLocalizedResourceFromMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml#getlocalizedresourcefrommarkup)]  
  
4.  <span data-ttu-id="6eb9c-110">Utilisez la ressource de chaîne à partir du code-behind, à l’aide de code semblable au suivant.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-110">Use the string resource from code-behind, using code like the following.</span></span>  
  
     [!code-csharp[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StringLocalizationSample/CSharp/MainWindow.xaml.cs#getlocalizedresourcefromcode)]
     [!code-vb[StringLocalizationSample#GetLocalizedResourceFromCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringLocalizationSample/VisualBasic/MainWindow.xaml.vb#getlocalizedresourcefromcode)]  
  
5.  <span data-ttu-id="6eb9c-111">Localisez l’application.</span><span class="sxs-lookup"><span data-stu-id="6eb9c-111">Localize the application.</span></span> <span data-ttu-id="6eb9c-112">Pour plus d’informations, consultez [localiser une Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span><span class="sxs-lookup"><span data-stu-id="6eb9c-112">For more information, see [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md).</span></span>
