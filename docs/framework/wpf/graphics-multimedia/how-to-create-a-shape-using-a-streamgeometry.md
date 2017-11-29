---
title: "Comment : créer une forme à l'aide d'un StreamGeometry"
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
- graphics [WPF], shapes
- shapes [WPF], creating with StreamGeometry class
ms.assetid: 08f7c8ce-074b-49cd-9aba-cc9592d4ee51
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: caa97d0dbd4c847892e164ecb168349c38f7f271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-shape-using-a-streamgeometry"></a><span data-ttu-id="740c4-102">Comment : créer une forme à l'aide d'un StreamGeometry</span><span class="sxs-lookup"><span data-stu-id="740c4-102">How to: Create a Shape Using a StreamGeometry</span></span>
<span data-ttu-id="740c4-103"><xref:System.Windows.Media.StreamGeometry>est une alternative légère à <xref:System.Windows.Media.PathGeometry> pour créer des formes géométriques.</span><span class="sxs-lookup"><span data-stu-id="740c4-103"><xref:System.Windows.Media.StreamGeometry> is light-weight alternative to <xref:System.Windows.Media.PathGeometry> for creating geometric shapes.</span></span> <span data-ttu-id="740c4-104">Utilisez un <xref:System.Windows.Media.StreamGeometry> lorsque vous devez décrire une géométrie complexe, mais ne souhaitez pas que la surcharge de prendre en charge la liaison de données, les animations ni les modifications.</span><span class="sxs-lookup"><span data-stu-id="740c4-104">Use a <xref:System.Windows.Media.StreamGeometry> when you need to describe a complex geometry but do not want the overhead of supporting data binding, animation, or modification.</span></span> <span data-ttu-id="740c4-105">Par exemple, en raison de son efficacité, la <xref:System.Windows.Media.StreamGeometry> classe est un bon choix pour décrire des ornements.</span><span class="sxs-lookup"><span data-stu-id="740c4-105">For example, because of its efficiency, the <xref:System.Windows.Media.StreamGeometry> class is a good choice for describing adorners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="740c4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="740c4-106">Example</span></span>  
 <span data-ttu-id="740c4-107">L’exemple suivant utilise la syntaxe d’attribut pour créer un triangulaire <xref:System.Windows.Media.StreamGeometry> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="740c4-107">The following example uses attribute syntax to create a triangular <xref:System.Windows.Media.StreamGeometry> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GeometriesMiscSnippets_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GeometriesMiscSnippets_snip/XAML/StreamGeometryExample.xaml#streamgeometrytriangleexamplewholepage)]  
  
 <span data-ttu-id="740c4-108">Pour plus d’informations sur <xref:System.Windows.Media.StreamGeometry> la syntaxe d’attribut, consultez la [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span><span class="sxs-lookup"><span data-stu-id="740c4-108">For more information about <xref:System.Windows.Media.StreamGeometry> attribute syntax, see the [Path Markup Syntax](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) page.</span></span>  
  
## <a name="example"></a><span data-ttu-id="740c4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="740c4-109">Example</span></span>  
 <span data-ttu-id="740c4-110">L’exemple suivant utilise un <xref:System.Windows.Media.StreamGeometry> pour définir un triangle dans le code.</span><span class="sxs-lookup"><span data-stu-id="740c4-110">The next example uses a <xref:System.Windows.Media.StreamGeometry> to define a triangle in code.</span></span> <span data-ttu-id="740c4-111">L’exemple crée d’abord un <xref:System.Windows.Media.StreamGeometry>, puis obtient un <xref:System.Windows.Media.StreamGeometryContext> et l’utilise pour décrire le triangle.</span><span class="sxs-lookup"><span data-stu-id="740c4-111">First, the example creates a <xref:System.Windows.Media.StreamGeometry>, then obtains a <xref:System.Windows.Media.StreamGeometryContext> and uses it to describe the triangle.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryTriangleExample.cs#streamgeometrytriangleexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryTriangleExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometrytriangleexample.vb#streamgeometrytriangleexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="740c4-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="740c4-112">Example</span></span>  
 <span data-ttu-id="740c4-113">L’exemple suivant crée une méthode qui utilise un <xref:System.Windows.Media.StreamGeometry> et <xref:System.Windows.Media.StreamGeometryContext> pour définir une forme géométrique en fonction des paramètres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="740c4-113">The next example creates a method that uses a <xref:System.Windows.Media.StreamGeometry> and <xref:System.Windows.Media.StreamGeometryContext> to define a geometric shape based on specified parameters.</span></span>  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/StreamGeometryExample.cs#streamgeometryexamplewholepage)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#StreamGeometryExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/streamgeometryexample.vb#streamgeometryexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="740c4-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="740c4-114">See Also</span></span>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.StreamGeometry>  
 <xref:System.Windows.Media.StreamGeometryContext>  
 [<span data-ttu-id="740c4-115">Créer une forme à l’aide d’un PathGeometry</span><span class="sxs-lookup"><span data-stu-id="740c4-115">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)  
 [<span data-ttu-id="740c4-116">Vue d’ensemble de Geometry</span><span class="sxs-lookup"><span data-stu-id="740c4-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
