---
title: "Comment : rendre des données disponibles pour la liaison en XAML"
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
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d734a7f17f8843ff284ac0854ac41d4a5b9f5584
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a><span data-ttu-id="a0326-102">Comment : rendre des données disponibles pour la liaison en XAML</span><span class="sxs-lookup"><span data-stu-id="a0326-102">How to: Make Data Available for Binding in XAML</span></span>
<span data-ttu-id="a0326-103">Cette rubrique décrit les différentes façons de vous rendre les données disponibles pour la liaison dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], en fonction des besoins de votre application.</span><span class="sxs-lookup"><span data-stu-id="a0326-103">This topic discusses the different ways you can make data available for binding in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], depending on the needs of your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0326-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a0326-104">Example</span></span>  
 <span data-ttu-id="a0326-105">Si vous avez un [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vous souhaitez lier à partir de l’objet [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], une façon de faire l’objet disponible pour la liaison est pour la définir en tant que ressource et lui donner un `x:Key`.</span><span class="sxs-lookup"><span data-stu-id="a0326-105">If you have a [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] object you would like to bind to from [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], one way you can make the object available for binding is to define it as a resource and give it an `x:Key`.</span></span> <span data-ttu-id="a0326-106">Dans l’exemple suivant, vous avez un `Person` objet avec une propriété de chaîne nommée `PersonName`.</span><span class="sxs-lookup"><span data-stu-id="a0326-106">In the following example, you have a `Person` object with a string property named `PersonName`.</span></span> <span data-ttu-id="a0326-107">Le `Person` objet est défini dans l’espace de noms appelé `SDKSample`.</span><span class="sxs-lookup"><span data-stu-id="a0326-107">The `Person` object is defined in the namespace called `SDKSample`.</span></span>  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 <span data-ttu-id="a0326-108">Vous pouvez ensuite la lier à l’objet dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a0326-108">You can then bind to the object in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], as shown in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="a0326-109">Vous pouvez également utiliser le <xref:System.Windows.Data.ObjectDataProvider> (classe), comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a0326-109">Alternatively, you can use the <xref:System.Windows.Data.ObjectDataProvider> class, as in the following example.</span></span>  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 <span data-ttu-id="a0326-110">Vous définissez la liaison de la même façon :</span><span class="sxs-lookup"><span data-stu-id="a0326-110">You define the binding the same way:</span></span>  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 <span data-ttu-id="a0326-111">Dans cet exemple particulier, le résultat est le même : vous avez un <xref:System.Windows.Controls.TextBlock> avec le contenu de texte `Joe`.</span><span class="sxs-lookup"><span data-stu-id="a0326-111">In this particular example, the result is the same: you have a <xref:System.Windows.Controls.TextBlock> with the text content `Joe`.</span></span> <span data-ttu-id="a0326-112">Toutefois, la <xref:System.Windows.Data.ObjectDataProvider> classe fournit des fonctionnalités telles que la capacité à lier au résultat d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a0326-112">However, the <xref:System.Windows.Data.ObjectDataProvider> class provides functionality such as the ability to bind to the result of a method.</span></span> <span data-ttu-id="a0326-113">Vous pouvez choisir d’utiliser la <xref:System.Windows.Data.ObjectDataProvider> classe si vous avez besoin de la fonctionnalité qu’elle fournit.</span><span class="sxs-lookup"><span data-stu-id="a0326-113">You can choose to use the <xref:System.Windows.Data.ObjectDataProvider> class if you need the functionality it provides.</span></span>  
  
 <span data-ttu-id="a0326-114">Toutefois, si vous établissez une liaison à un objet qui a déjà été créé, vous devez définir le `DataContext` dans le code, comme dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a0326-114">However, if you are binding to an object that has already been created, you need to set the `DataContext` in code, as in the following example.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="a0326-115">Pour accéder à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données de la liaison à l’aide du <xref:System.Windows.Data.XmlDataProvider> de classe, consultez [lier à l’aide de données XML, requêtes XMLDataProvider et XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span><span class="sxs-lookup"><span data-stu-id="a0326-115">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.XmlDataProvider> class, see [Bind to XML Data Using an XMLDataProvider and XPath Queries](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md).</span></span> <span data-ttu-id="a0326-116">Pour accéder à [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] les données de la liaison à l’aide du <xref:System.Windows.Data.ObjectDataProvider> de classe, consultez [lier à XDocument, XElement ou LINQ pour des résultats de requête XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span><span class="sxs-lookup"><span data-stu-id="a0326-116">To access [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data for binding using the <xref:System.Windows.Data.ObjectDataProvider> class, see [Bind to XDocument, XElement, or LINQ for XML Query Results](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).</span></span>  
  
 <span data-ttu-id="a0326-117">Pour plus d’informations sur les différentes méthodes que vous pouvez spécifier les données que vous liez à, consultez [spécifier la Source de liaison](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span><span class="sxs-lookup"><span data-stu-id="a0326-117">For information about the different ways you can specify the data you are binding to, see [Specify the Binding Source](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md).</span></span> <span data-ttu-id="a0326-118">Pour plus d’informations sur les types de données que vous pouvez lier à ou comment implémenter votre propre [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objets pour la liaison, consultez [vue d’ensemble des Sources de liaison](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a0326-118">For information about what types of data you can bind to or how to implement your own [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objects for binding, see [Binding Sources Overview](../../../../docs/framework/wpf/data/binding-sources-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0326-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0326-119">See Also</span></span>  
 [<span data-ttu-id="a0326-120">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="a0326-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="a0326-121">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="a0326-121">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
