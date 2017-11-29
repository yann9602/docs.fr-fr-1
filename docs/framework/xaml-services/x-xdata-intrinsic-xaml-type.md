---
title: "x:XData, type XAML intrinsèque"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:XData
- XData
- xXData
helpviewer_keywords:
- XAML [XAML Services], x:XData directive element
- XData in XAML [XAML Services]
- x:XData XAML directive element [XAML Services]
ms.assetid: 7ce209c2-621b-4977-b643-565f7e663534
caps.latest.revision: "17"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 3e448c28be6515748254e267b70f3c898b9226a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xxdata-intrinsic-xaml-type"></a><span data-ttu-id="81839-102">x:XData, type XAML intrinsèque</span><span class="sxs-lookup"><span data-stu-id="81839-102">x:XData Intrinsic XAML Type</span></span>
<span data-ttu-id="81839-103">Active le positionnement des îlots de données XML dans une production XAML.</span><span class="sxs-lookup"><span data-stu-id="81839-103">Enables placement of XML data islands within a XAML production.</span></span> <span data-ttu-id="81839-104">Éléments XML `x:XData` ne doivent pas être traités par les processeurs XAML comme s’ils faisaient partie de l’espace de noms XAML par défaut d’agissant ou tout autre espace de noms XAML.</span><span class="sxs-lookup"><span data-stu-id="81839-104">XML elements within `x:XData` should not be treated by XAML processors as if they are a part of the acting default XAML namespace or any other XAML namespace.</span></span> <span data-ttu-id="81839-105">`x:XData`peut contenir arbitraire XML bien formé.</span><span class="sxs-lookup"><span data-stu-id="81839-105">`x:XData` can contain arbitrary well-formed XML.</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="81839-106">Utilisation d'éléments objet XAML</span><span class="sxs-lookup"><span data-stu-id="81839-106">XAML Object Element Usage</span></span>  
  
```  
<x:XData>  
  <elementDataRoot>  
    [elementData]  
  </elementDataRoot>  
</x:XData>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="81839-107">Valeurs XAML</span><span class="sxs-lookup"><span data-stu-id="81839-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`elementDataRoot`|<span data-ttu-id="81839-108">L’élément racine unique de l’îlot de données incorporé.</span><span class="sxs-lookup"><span data-stu-id="81839-108">The single root element of the enclosed data island.</span></span> <span data-ttu-id="81839-109">La plupart des consommateurs éventuels, XML qui ne dispose pas d’une racine unique est considéré comme non valide.</span><span class="sxs-lookup"><span data-stu-id="81839-109">For most eventual consumers, XML that does not have a single root is considered invalid.</span></span> <span data-ttu-id="81839-110">En particulier, une racine unique est obligatoire si le `x:XData` est destiné à une source de données XML WPF ou bien d’autres technologies qui utilisent des sources XML pour la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="81839-110">In particular, a single root is required if the `x:XData` is intended as an XML data source for WPF or many other technologies that use XML sources for data binding.</span></span>|  
|`[elementData]`|<span data-ttu-id="81839-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="81839-111">Optional.</span></span> <span data-ttu-id="81839-112">Code XML qui représente les données XML.</span><span class="sxs-lookup"><span data-stu-id="81839-112">XML that represents the XML data.</span></span> <span data-ttu-id="81839-113">N’importe quel nombre d’éléments peut être contenu comme données d’élément et les éléments imbriqués peuvent être contenus dans d’autres éléments ; Toutefois, les règles générales de XML s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="81839-113">Any number of elements can be contained as element data and nested elements can be contained in other elements; however, the general rules of XML apply.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81839-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="81839-114">Remarks</span></span>  
 <span data-ttu-id="81839-115">Les éléments XML dans un `x:XData` objet peut déclarer de nouveau tous les espaces de noms possibles et les préfixes le conteneur XMLDOM dans les données.</span><span class="sxs-lookup"><span data-stu-id="81839-115">The XML elements within an `x:XData` object can re-declare all possible namespaces and prefixes of the containing XMLDOM within the data.</span></span>  
  
 <span data-ttu-id="81839-116">L’accès par programme aux données XML et le `x:XData` type XAML intrinsèque est possible dans les Services XAML .NET Framework via la <xref:System.Windows.Markup.XData> classe.</span><span class="sxs-lookup"><span data-stu-id="81839-116">Programmatic access to XML data and the `x:XData` intrinsic XAML type is possible in .NET Framework XAML Services through the <xref:System.Windows.Markup.XData> class.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="81839-117">Notes d’utilisation WPF</span><span class="sxs-lookup"><span data-stu-id="81839-117">WPF Usage Notes</span></span>  
 <span data-ttu-id="81839-118">Le `x:XData` objet est principalement utilisé comme un objet enfant d’un <xref:System.Windows.Data.XmlDataProvider>, ou bien, comme l’objet enfant de la <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> propriété (en XAML, cela est exprimé en général dans la syntaxe d’élément de propriété).</span><span class="sxs-lookup"><span data-stu-id="81839-118">The `x:XData` object is primarily used as a child object of an <xref:System.Windows.Data.XmlDataProvider>, or alternatively, as the child object of the <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> property (in XAML, this is typically expressed in property element syntax).</span></span>  
  
 <span data-ttu-id="81839-119">Généralement, les données doivent redéfinir l’espace de noms XML base dans l’îlot de données en tant que nouvel espace de noms XML par défaut (défini sur une chaîne vide).</span><span class="sxs-lookup"><span data-stu-id="81839-119">The data should typically redefine the base XML namespace within the data island to be a new default XML namespace (set to an empty string).</span></span> <span data-ttu-id="81839-120">C’est plus facile pour les îlots de données simples, car le <xref:System.Windows.Data.Binding.XPath%2A> expressions sont utilisées pour référencer et lier les données peuvent éviter l’inclusion de préfixes.</span><span class="sxs-lookup"><span data-stu-id="81839-120">This is easiest for simple data islands because the <xref:System.Windows.Data.Binding.XPath%2A> expressions that are used to reference and bind to the data can avoid inclusion of prefixes.</span></span> <span data-ttu-id="81839-121">Les îlots de données plus complexes peuvent définir plusieurs préfixes pour les données et utiliser un préfixe spécifique pour l’espace de noms XML à la racine.</span><span class="sxs-lookup"><span data-stu-id="81839-121">More complex data islands might define multiple prefixes for the data and use a specific prefix for the XML namespace at the root.</span></span> <span data-ttu-id="81839-122">Dans ce cas, tous les <xref:System.Windows.Data.Binding.XPath%2A> références d’expression doivent inclure le préfixe mappé en l’espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="81839-122">In this case, all <xref:System.Windows.Data.Binding.XPath%2A> expression references should include the appropriate namespace-mapped prefix.</span></span> <span data-ttu-id="81839-123">Pour plus d’informations, consultez [Vue d’ensemble de la liaison de données](../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="81839-123">For more information, see [Data Binding Overview](../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="81839-124">Techniquement, `x:XData` peut être utilisé en tant que le contenu de n’importe quelle propriété de type <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="81839-124">Technically, `x:XData` can be used as the content of any property of type <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="81839-125">Toutefois, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> est la seule implémentation apparente.</span><span class="sxs-lookup"><span data-stu-id="81839-125">However, <xref:System.Windows.Data.XmlDataProvider.XmlSerializer%2A?displayProperty=nameWithType> is the only prominent implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81839-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81839-126">See Also</span></span>  
 <xref:System.Windows.Data.XmlDataProvider>  
 [<span data-ttu-id="81839-127">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="81839-127">Data Binding Overview</span></span>](../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="81839-128">Binding, extension de balisage</span><span class="sxs-lookup"><span data-stu-id="81839-128">Binding Markup Extension</span></span>](../../../docs/framework/wpf/advanced/binding-markup-extension.md)
