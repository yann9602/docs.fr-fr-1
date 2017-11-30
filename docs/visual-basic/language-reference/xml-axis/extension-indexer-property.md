---
title: "Propriété d’indexeur d’extension (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlPropertyExtensionIndexer
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML extension indexer [Visual Basic]
- extension indexer [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99d14b6e54a59ffc904a9e786c22498d23ee8ab6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="extension-indexer-property-visual-basic"></a><span data-ttu-id="476d2-102">Propriété d’indexeur d’extension (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="476d2-102">Extension Indexer Property (Visual Basic)</span></span>
<span data-ttu-id="476d2-103">Fournit un accès aux différents éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="476d2-103">Provides access to individual elements in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="476d2-104">Syntax</span></span>  
  
```  
object(index)  
```  
  
## <a name="parts"></a><span data-ttu-id="476d2-105">Composants</span><span class="sxs-lookup"><span data-stu-id="476d2-105">Parts</span></span>  
  
|<span data-ttu-id="476d2-106">Terme</span><span class="sxs-lookup"><span data-stu-id="476d2-106">Term</span></span>|<span data-ttu-id="476d2-107">Définition</span><span class="sxs-lookup"><span data-stu-id="476d2-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="476d2-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="476d2-108">Required.</span></span> <span data-ttu-id="476d2-109">Collection requêtable.</span><span class="sxs-lookup"><span data-stu-id="476d2-109">A queryable collection.</span></span> <span data-ttu-id="476d2-110">Autrement dit, une collection qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="476d2-110">That is, a collection that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>|  
|<span data-ttu-id="476d2-111">(</span><span class="sxs-lookup"><span data-stu-id="476d2-111">(</span></span>|<span data-ttu-id="476d2-112">Requis.</span><span class="sxs-lookup"><span data-stu-id="476d2-112">Required.</span></span> <span data-ttu-id="476d2-113">Indique le début de la propriété d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="476d2-113">Denotes the start of the indexer property.</span></span>|  
|`index`|<span data-ttu-id="476d2-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="476d2-114">Required.</span></span> <span data-ttu-id="476d2-115">Expression entière qui spécifie la position de base zéro d’un élément de la collection.</span><span class="sxs-lookup"><span data-stu-id="476d2-115">An integer expression that specifies the zero-based position of an element of the collection.</span></span>|  
|<span data-ttu-id="476d2-116">)</span><span class="sxs-lookup"><span data-stu-id="476d2-116">)</span></span>|<span data-ttu-id="476d2-117">Requis.</span><span class="sxs-lookup"><span data-stu-id="476d2-117">Required.</span></span> <span data-ttu-id="476d2-118">Indique la fin de la propriété d’indexeur.</span><span class="sxs-lookup"><span data-stu-id="476d2-118">Denotes the end of the indexer property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="476d2-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="476d2-119">Return Value</span></span>  
 <span data-ttu-id="476d2-120">L’objet à partir de l’emplacement spécifié dans la collection, ou `Nothing` si l’index est hors limites.</span><span class="sxs-lookup"><span data-stu-id="476d2-120">The object from the specified location in the collection, or `Nothing` if the index is out of range.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="476d2-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="476d2-121">Remarks</span></span>  
 <span data-ttu-id="476d2-122">Vous pouvez utiliser la propriété d’indexeur d’extension pour accéder aux différents éléments d’une collection.</span><span class="sxs-lookup"><span data-stu-id="476d2-122">You can use the extension indexer property to access individual elements in a collection.</span></span> <span data-ttu-id="476d2-123">Cette propriété d’indexeur est généralement utilisée sur la sortie des propriétés d’axe XML.</span><span class="sxs-lookup"><span data-stu-id="476d2-123">This indexer property is typically used on the output of XML axis properties.</span></span> <span data-ttu-id="476d2-124">L’enfant XML et les propriétés d’axe de descendant XML retournent des collections de <xref:System.Xml.Linq.XElement> objets ou une valeur d’attribut.</span><span class="sxs-lookup"><span data-stu-id="476d2-124">The XML child and XML descendent axis properties return collections of <xref:System.Xml.Linq.XElement> objects or an attribute value.</span></span>  
  
 <span data-ttu-id="476d2-125">Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur convertit les propriétés indexeur d’extension en appels à la `ElementAtOrDefault` (méthode).</span><span class="sxs-lookup"><span data-stu-id="476d2-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler converts extension indexer properties to calls to the `ElementAtOrDefault` method.</span></span> <span data-ttu-id="476d2-126">Contrairement à un indexeur de tableau, le `ElementAtOrDefault` retourne de la méthode `Nothing` si l’index est hors limites.</span><span class="sxs-lookup"><span data-stu-id="476d2-126">Unlike an array indexer, the `ElementAtOrDefault` method returns `Nothing` if the index is out of range.</span></span> <span data-ttu-id="476d2-127">Ce comportement est utile lorsque vous ne pouvez pas facilement déterminer le nombre d’éléments dans une collection.</span><span class="sxs-lookup"><span data-stu-id="476d2-127">This behavior is useful when you cannot easily determine the number of elements in a collection.</span></span>  
  
 <span data-ttu-id="476d2-128">Cette propriété d’indexeur est semblable à une propriété d’extension pour les collections qui implémentent <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601>: il est utilisé uniquement si la collection n’a pas d’indexeur ou une propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="476d2-128">This indexer property is like an extension property for collections that implement <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>: it is used only if the collection does not have an indexer or a default property.</span></span>  
  
 <span data-ttu-id="476d2-129">Pour accéder à la valeur du premier élément dans une collection de <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> des objets, vous pouvez utiliser le code XML `Value` propriété.</span><span class="sxs-lookup"><span data-stu-id="476d2-129">To access the value of the first element in a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects, you can use the XML `Value` property.</span></span> <span data-ttu-id="476d2-130">Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="476d2-130">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="476d2-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="476d2-131">Example</span></span>  
 <span data-ttu-id="476d2-132">L’exemple suivant montre comment utiliser l’indexeur d’extension pour accéder à la deuxième nœud enfant dans une collection de <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="476d2-132">The following example shows how to use the extension indexer to access the second child node in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="476d2-133">La collection est accessible à l’aide de la propriété d’axe enfant, qui obtient tous les éléments enfants nommés `phone` dans le `contact` objet.</span><span class="sxs-lookup"><span data-stu-id="476d2-133">The collection is accessed by using the child axis property, which gets all child elements named `phone` in the `contact` object.</span></span>  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/extension-indexer-property_1.vb)]  
  
 <span data-ttu-id="476d2-134">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="476d2-134">This code displays the following text:</span></span>  
  
 `Second phone number: 425-555-0145`  
  
## <a name="see-also"></a><span data-ttu-id="476d2-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="476d2-135">See Also</span></span>  
 <xref:System.Xml.Linq.XElement>  
 [<span data-ttu-id="476d2-136">Propriétés d’axe XML</span><span class="sxs-lookup"><span data-stu-id="476d2-136">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [<span data-ttu-id="476d2-137">Littéraux XML</span><span class="sxs-lookup"><span data-stu-id="476d2-137">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)  
 [<span data-ttu-id="476d2-138">Création de code XML dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="476d2-138">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="476d2-139">Propriété de valeur XML</span><span class="sxs-lookup"><span data-stu-id="476d2-139">XML Value Property</span></span>](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
