---
title: "Propriété de valeur XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionValue
helpviewer_keywords:
- Value property [Visual Basic]
- Visual Basic code, accessing XML
- XML axis [Visual Basic], Value
- XML Value property [Visual Basic]
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d9294c2d1d83dce3bca2abc22ee9c70296fc8014
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2017
---
# <a name="xml-value-property-visual-basic"></a><span data-ttu-id="c2e39-102">Propriété de valeur XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2e39-102">XML Value Property (Visual Basic)</span></span>
<span data-ttu-id="c2e39-103">Fournit l’accès à la valeur du premier élément d’une collection de <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="c2e39-103">Provides access to the value of the first element of a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2e39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2e39-104">Syntax</span></span>  
  
```  
object.Value  
```  
  
## <a name="parts"></a><span data-ttu-id="c2e39-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c2e39-105">Parts</span></span>  
  
|<span data-ttu-id="c2e39-106">Terme</span><span class="sxs-lookup"><span data-stu-id="c2e39-106">Term</span></span>|<span data-ttu-id="c2e39-107">Définition</span><span class="sxs-lookup"><span data-stu-id="c2e39-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="c2e39-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c2e39-108">Required.</span></span> <span data-ttu-id="c2e39-109">Collection d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="c2e39-109">Collection of <xref:System.Xml.Linq.XElement> objects.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="c2e39-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2e39-110">Return Value</span></span>  
 <span data-ttu-id="c2e39-111">A `String` qui contient la valeur du premier élément de la collection, ou `Nothing` si la collection est vide.</span><span class="sxs-lookup"><span data-stu-id="c2e39-111">A `String` that contains the value of the first element of the collection, or `Nothing` if the collection is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2e39-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="c2e39-112">Remarks</span></span>  
 <span data-ttu-id="c2e39-113">Le <xref:System.Xml.Linq.XElement.Value%2A> propriété permet d’accéder à la valeur du premier élément dans une collection de <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="c2e39-113">The <xref:System.Xml.Linq.XElement.Value%2A> property makes it easy to access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c2e39-114">Cette propriété vérifie d’abord si la collection contient au moins un objet.</span><span class="sxs-lookup"><span data-stu-id="c2e39-114">This property first checks whether the collection contains at least one object.</span></span> <span data-ttu-id="c2e39-115">Si la collection est vide, cette propriété retourne `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c2e39-115">If the collection is empty, this property returns `Nothing`.</span></span> <span data-ttu-id="c2e39-116">Sinon, cette propriété retourne la valeur de la <xref:System.Xml.Linq.XElement.Value%2A> propriété du premier élément dans la collection.</span><span class="sxs-lookup"><span data-stu-id="c2e39-116">Otherwise, this property returns the value of the <xref:System.Xml.Linq.XElement.Value%2A> property of the first element in the collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2e39-117">Quand vous accédez à la valeur d’un attribut XML à l’aide du ' @' identificateur, la valeur d’attribut est retournée en tant qu’un `String` et vous n’avez pas besoin de spécifier explicitement le <xref:System.Xml.Linq.XAttribute.Value%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="c2e39-117">When you access the value of an XML attribute using the '@' identifier, the attribute value is returned as a `String` and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="c2e39-118">Pour accéder aux autres éléments d’une collection, vous pouvez utiliser la propriété indexeur d’extension XML.</span><span class="sxs-lookup"><span data-stu-id="c2e39-118">To access other elements in a collection, you can use the XML extension indexer property.</span></span> <span data-ttu-id="c2e39-119">Pour plus d’informations, consultez [propriété d’indexeur d’Extension](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span><span class="sxs-lookup"><span data-stu-id="c2e39-119">For more information, see [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md).</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="c2e39-120">Héritage</span><span class="sxs-lookup"><span data-stu-id="c2e39-120">Inheritance</span></span>  
 <span data-ttu-id="c2e39-121">La plupart des utilisateurs n’aura pas d’implémenter <xref:System.Collections.Generic.IEnumerable%601>et peuvent donc ignorer cette section.</span><span class="sxs-lookup"><span data-stu-id="c2e39-121">Most users will not have to implement <xref:System.Collections.Generic.IEnumerable%601>, and can therefore ignore this section.</span></span>  
  
 <span data-ttu-id="c2e39-122">Le <xref:System.Xml.Linq.XElement.Value%2A> propriété est une propriété d’extension pour les types qui implémentent `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="c2e39-122">The <xref:System.Xml.Linq.XElement.Value%2A> property is an extension property for types that implement `IEnumerable(Of XElement)`.</span></span> <span data-ttu-id="c2e39-123">La liaison de cette propriété d’extension est similaire à la liaison de méthodes d’extension : si un type implémente l’une des interfaces et définit une propriété portant le nom « Valeur », cette propriété est prioritaire sur la propriété d’extension.</span><span class="sxs-lookup"><span data-stu-id="c2e39-123">The binding of this extension property is like the binding of extension methods: if a type implements one of the interfaces and defines a property that has the name "Value", that property has precedence over the extension property.</span></span> <span data-ttu-id="c2e39-124">En d’autres termes, cela <xref:System.Xml.Linq.XElement.Value%2A> propriété peut être substituée en définissant une nouvelle propriété dans une classe qui implémente `IEnumerable(Of XElement)`.</span><span class="sxs-lookup"><span data-stu-id="c2e39-124">In other words, this <xref:System.Xml.Linq.XElement.Value%2A> property can be overridden by defining a new property in a class that implements `IEnumerable(Of XElement)`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2e39-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2e39-125">Example</span></span>  
 <span data-ttu-id="c2e39-126">L’exemple suivant montre comment utiliser le <xref:System.Xml.Linq.XElement.Value%2A> propriété pour accéder au premier nœud dans une collection de <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="c2e39-126">The following example shows how to use the <xref:System.Xml.Linq.XElement.Value%2A> property to access the first node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="c2e39-127">L’exemple utilise la propriété d’axe enfant pour obtenir la collection de tous les nœuds enfants nommés `phone` qui se trouvent dans le `contact` objet.</span><span class="sxs-lookup"><span data-stu-id="c2e39-127">The example uses the child axis property to get the collection of all child nodes named `phone` that are in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_1.vb)]  
  
 <span data-ttu-id="c2e39-128">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c2e39-128">This code displays the following text:</span></span>  
  
 `Phone number: 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="c2e39-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="c2e39-129">Example</span></span>  
 <span data-ttu-id="c2e39-130">L’exemple suivant montre comment obtenir la valeur d’un attribut XML à partir d’une collection de <xref:System.Xml.Linq.XAttribute> objets.</span><span class="sxs-lookup"><span data-stu-id="c2e39-130">The following example shows how to get the value of an XML attribute from a collection of <xref:System.Xml.Linq.XAttribute> objects.</span></span> <span data-ttu-id="c2e39-131">L’exemple utilise la propriété axe d’attribut pour afficher la valeur de la `type` attribut pour tous les `phone` éléments.</span><span class="sxs-lookup"><span data-stu-id="c2e39-131">The example uses the attribute axis property to display the value of the `type` attribute for all of the `phone` elements.</span></span>  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-value-property_2.vb)]  
  
 <span data-ttu-id="c2e39-132">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c2e39-132">This code displays the following text:</span></span>  
  
 `home`  
  
 `work`  
  
## <a name="see-also"></a><span data-ttu-id="c2e39-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2e39-133">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="c2e39-134">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="c2e39-134">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="c2e39-135">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="c2e39-135">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="c2e39-136">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2e39-136">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="c2e39-137">Méthodes d’extension</span><span class="sxs-lookup"><span data-stu-id="c2e39-137">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="c2e39-138">Propriété d’indexeur d’extension</span><span class="sxs-lookup"><span data-stu-id="c2e39-138">Extension Indexer Property</span></span>](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)  
 [<span data-ttu-id="c2e39-139">Propriété d’axe enfant XML</span><span class="sxs-lookup"><span data-stu-id="c2e39-139">XML Child Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="c2e39-140">Propriété d’axe d’attribut XML</span><span class="sxs-lookup"><span data-stu-id="c2e39-140">XML Attribute Axis Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
