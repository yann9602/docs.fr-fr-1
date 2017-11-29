---
title: "Comment : effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML"
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
- data binding [WPF], binding to XDocument
- data binding [WPF], binding to XElement
ms.assetid: 6a629a49-fe1c-465d-b76a-3dcbf4307b64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b39c45a7c85155a0fb46e8e176da5979e52e6e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results"></a><span data-ttu-id="60237-102">Comment : effectuer une liaison avec XDocument, XElement ou LINQ pour des résultats de requête XML</span><span class="sxs-lookup"><span data-stu-id="60237-102">How to: Bind to XDocument, XElement, or LINQ for XML Query Results</span></span>
<span data-ttu-id="60237-103">Cet exemple montre comment lier des données XML à une <xref:System.Windows.Controls.ItemsControl> à l’aide de <xref:System.Xml.Linq.XDocument>.</span><span class="sxs-lookup"><span data-stu-id="60237-103">This example demonstrates how to bind XML data to an <xref:System.Windows.Controls.ItemsControl> using <xref:System.Xml.Linq.XDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60237-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="60237-104">Example</span></span>  
 <span data-ttu-id="60237-105">Le code XAML suivant définit un <xref:System.Windows.Controls.ItemsControl> et inclut un modèle de données pour les données de type `Planet` dans le `http://planetsNS` espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="60237-105">The following XAML code defines an <xref:System.Windows.Controls.ItemsControl> and includes a data template for data of type `Planet` in the `http://planetsNS` XML namespace.</span></span> <span data-ttu-id="60237-106">Un type de données XML qui occupe un espace de noms doit inclure l’espace de noms entre accolades, et s’il s’affiche là où une extension de balisage XAML pourrait apparaître, il doit précéder l’espace de noms avec une séquence d’échappement d’accolades.</span><span class="sxs-lookup"><span data-stu-id="60237-106">An XML data type that occupies a namespace must include the namespace in braces, and if it appears where a XAML markup extension could appear, it must precede the namespace with a brace escape sequence.</span></span> <span data-ttu-id="60237-107">Ce code lie aux propriétés dynamiques qui correspondent à la <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> méthodes de la <xref:System.Xml.Linq.XElement> classe.</span><span class="sxs-lookup"><span data-stu-id="60237-107">This code binds to dynamic properties that correspond to the <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> methods of the <xref:System.Xml.Linq.XElement> class.</span></span> <span data-ttu-id="60237-108">Les propriétés dynamiques permettent à XAML de se lier aux propriétés dynamiques qui partagent les noms des méthodes.</span><span class="sxs-lookup"><span data-stu-id="60237-108">Dynamic properties enable XAML to bind to dynamic properties that share the names of methods.</span></span> <span data-ttu-id="60237-109">Pour en savoir plus, consultez [Propriétés dynamiques LINQ to XML](/visualstudio/designers/linq-to-xml-dynamic-properties).</span><span class="sxs-lookup"><span data-stu-id="60237-109">To learn more, see [LINQ to XML Dynamic Properties](/visualstudio/designers/linq-to-xml-dynamic-properties).</span></span> <span data-ttu-id="60237-110">Notez comment la déclaration d’espace de noms par défaut pour XML ne s’applique pas aux noms d’attribut.</span><span class="sxs-lookup"><span data-stu-id="60237-110">Notice how the default namespace declaration for the XML does not apply to attribute names.</span></span>  
  
 [!code-xaml[XLinqExample#StackPanelResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
[!code-xaml[XLinqExample#ItemsControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#itemscontrol)]  
  
 <span data-ttu-id="60237-111">Le code c# suivant appelle <xref:System.Xml.Linq.XDocument.Load%2A> et définit le contexte de données du Panneau de configuration pile à tous les sous-éléments de l’élément nommé `SolarSystemPlanets` dans le `http://planetsNS` espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="60237-111">The following C# code calls <xref:System.Xml.Linq.XDocument.Load%2A> and sets the stack panel data context to all subelements of the element named `SolarSystemPlanets` in the `http://planetsNS` XML namespace.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromFile](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromfile)]
 [!code-vb[XLinqExample#LoadDCFromFile](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromfile)]  
  
 <span data-ttu-id="60237-112">Données XML peuvent être stockées comme une ressource XAML à l’aide <xref:System.Windows.Data.ObjectDataProvider>.</span><span class="sxs-lookup"><span data-stu-id="60237-112">XML data can be stored as a XAML resource using <xref:System.Windows.Data.ObjectDataProvider>.</span></span> <span data-ttu-id="60237-113">Pour obtenir un exemple complet, consultez la page [Code source L2DBForm.xaml](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span><span class="sxs-lookup"><span data-stu-id="60237-113">For a complete example, see  [L2DBForm.xaml Source Code](http://msdn.microsoft.com/library/624e96d4-6d27-4195-8ac2-2f3835f6c57e).</span></span> <span data-ttu-id="60237-114">L’exemple suivant montre comment le code peut définir le contexte de données sur une ressource d’objet.</span><span class="sxs-lookup"><span data-stu-id="60237-114">The following sample shows how code can set the data context to an object resource.</span></span>  
  
 [!code-csharp[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#loaddcfromxaml)]
 [!code-vb[XLinqExample#LoadDCFromXAML](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#loaddcfromxaml)]  
  
 <span data-ttu-id="60237-115">Les propriétés dynamiques qui mappent aux <xref:System.Xml.Linq.XContainer.Element%2A> et <xref:System.Xml.Linq.XElement.Attribute%2A> offrent une souplesse dans XAML.</span><span class="sxs-lookup"><span data-stu-id="60237-115">The dynamic properties that map to <xref:System.Xml.Linq.XContainer.Element%2A> and <xref:System.Xml.Linq.XElement.Attribute%2A> provide flexibility within XAML.</span></span> <span data-ttu-id="60237-116">Votre code peut également être lié aux résultats d’une requête LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="60237-116">Your code can also bind to the results of a LINQ for XML query.</span></span> <span data-ttu-id="60237-117">Cet exemple se lie aux résultats de la requête triés par une valeur d’élément.</span><span class="sxs-lookup"><span data-stu-id="60237-117">This example binds to query results ordered by an element value.</span></span>  
  
 [!code-csharp[XLinqExample#BindToResults](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml.cs#bindtoresults)]
 [!code-vb[XLinqExample#BindToResults](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/XLinqExample/visualbasic/window1.xaml.vb#bindtoresults)]  
  
## <a name="see-also"></a><span data-ttu-id="60237-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60237-118">See Also</span></span>  
 [<span data-ttu-id="60237-119">Vue d'ensemble des sources de liaison</span><span class="sxs-lookup"><span data-stu-id="60237-119">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="60237-120">Vue d’ensemble de la liaison de données WPF avec LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="60237-120">WPF Data Binding with LINQ to XML Overview</span></span>](/visualstudio/designers/wpf-data-binding-with-linq-to-xml-overview)  
 [<span data-ttu-id="60237-121">Exemple de liaison de données WPF à l’aide de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="60237-121">WPF Data Binding Using LINQ to XML Example</span></span>](/visualstudio/designers/wpf-data-binding-using-linq-to-xml-example)  
 [<span data-ttu-id="60237-122">Propriétés dynamiques LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="60237-122">LINQ to XML Dynamic Properties</span></span>](/visualstudio/designers/linq-to-xml-dynamic-properties)
