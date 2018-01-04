---
title: Guide pratique pour utiliser des ressources dans des applications localisables
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e025b42a72def81420de7d82dcf027405669ce78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-resources-in-localizable-applications"></a><span data-ttu-id="65b93-102">Guide pratique pour utiliser des ressources dans des applications localisables</span><span class="sxs-lookup"><span data-stu-id="65b93-102">How to: Use Resources in Localizable Applications</span></span>
<span data-ttu-id="65b93-103">La localisation consiste à adapter une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] à différentes cultures.</span><span class="sxs-lookup"><span data-stu-id="65b93-103">Localization means to adapt a [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] to different cultures.</span></span> <span data-ttu-id="65b93-104">Pour ce faire, le texte (tels que les titres, légendes, éléments de liste et ainsi de suite) doit être traduit.</span><span class="sxs-lookup"><span data-stu-id="65b93-104">To do this, text such as titles, captions, list box items and so forth have to be translated.</span></span> <span data-ttu-id="65b93-105">Pour faciliter la traduction, les éléments à traduire sont rassemblés dans des fichiers de ressources.</span><span class="sxs-lookup"><span data-stu-id="65b93-105">To make translation easier the items to be translated are collected into resource files.</span></span> <span data-ttu-id="65b93-106">Consultez [localiser une Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) pour plus d’informations sur la création d’un fichier de ressources pour la localisation.</span><span class="sxs-lookup"><span data-stu-id="65b93-106">See [Localize an Application](../../../../docs/framework/wpf/advanced/how-to-localize-an-application.md) for information on how to create a resource file for localization.</span></span> <span data-ttu-id="65b93-107">Pour rendre un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] localisable, les développeurs doivent générer toutes les ressources localisables dans un assembly de ressources d’application.</span><span class="sxs-lookup"><span data-stu-id="65b93-107">To make a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application localizable, developers need to build all the localizable resources into a resource assembly.</span></span> <span data-ttu-id="65b93-108">L’assembly de ressources est localisé dans différentes langues, et le code-behind utilise la gestion des ressources [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] à charger.</span><span class="sxs-lookup"><span data-stu-id="65b93-108">The resource assembly is localized into different languages, and the code-behind uses resource management [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] to load.</span></span> <span data-ttu-id="65b93-109">Un des fichiers requis pour un [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application est un fichier projet (.proj).</span><span class="sxs-lookup"><span data-stu-id="65b93-109">One of the files required for a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application is a project file (.proj).</span></span> <span data-ttu-id="65b93-110">Toutes les ressources que vous utilisez dans votre application doivent être comprises dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="65b93-110">All resources that you use in your application should be included in the project file.</span></span> <span data-ttu-id="65b93-111">L'exemple de code suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="65b93-111">The following code example shows this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65b93-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="65b93-112">Example</span></span>  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 <span data-ttu-id="65b93-113">Pour utiliser une ressource dans votre application, vous instanciez <xref:System.Resources.ResourceManager> et charger la ressource que vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="65b93-113">To use a resource in your application, you instantiate <xref:System.Resources.ResourceManager> and load the resource you want to use.</span></span> <span data-ttu-id="65b93-114">Le code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="65b93-114">The following demonstrates how to do this.</span></span>  
  
 [!code-csharp[LocalizationResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
