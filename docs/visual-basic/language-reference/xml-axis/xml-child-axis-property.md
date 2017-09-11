---
title: "Propriété d’axe enfant XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyChildAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 2ccdacdadf219b9c928558f07e0890be6471d40a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-child-axis-property-visual-basic"></a><span data-ttu-id="c54dd-102">Propriété d'axe enfant XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c54dd-102">XML Child Axis Property (Visual Basic)</span></span>
<span data-ttu-id="c54dd-103">Fournit l’accès aux enfants de l’un des éléments suivants : un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c54dd-103">Provides access to the children of one of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c54dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c54dd-104">Syntax</span></span>  
  
```  
  
object.<child>  
```  
  
## <a name="parts"></a><span data-ttu-id="c54dd-105">Composants</span><span class="sxs-lookup"><span data-stu-id="c54dd-105">Parts</span></span>  
  
|<span data-ttu-id="c54dd-106">Terme</span><span class="sxs-lookup"><span data-stu-id="c54dd-106">Term</span></span>|<span data-ttu-id="c54dd-107">Définition</span><span class="sxs-lookup"><span data-stu-id="c54dd-107">Definition</span></span>|  
|---|---|  
|`object`|<span data-ttu-id="c54dd-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c54dd-108">Required.</span></span> <span data-ttu-id="c54dd-109">Un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c54dd-109">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>|  
|<span data-ttu-id="c54dd-110">.<</span><span class="sxs-lookup"><span data-stu-id="c54dd-110">.<</span></span>|<span data-ttu-id="c54dd-111">Requis.</span><span class="sxs-lookup"><span data-stu-id="c54dd-111">Required.</span></span> <span data-ttu-id="c54dd-112">Indique le début d'une propriété d'axe enfant.</span><span class="sxs-lookup"><span data-stu-id="c54dd-112">Denotes the start of a child axis property.</span></span>|  
|`child`|<span data-ttu-id="c54dd-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c54dd-113">Required.</span></span> <span data-ttu-id="c54dd-114">Nom des nœuds enfants auxquels accéder, sous la forme [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-114">Name of the child nodes to access, of the form [`prefix``:`]`name`.</span></span><br /><br /><span data-ttu-id="c54dd-115"> -   `Prefix`-Facultatif.</span><span class="sxs-lookup"><span data-stu-id="c54dd-115"> -   `Prefix` - Optional.</span></span> <span data-ttu-id="c54dd-116">Préfixe d'espace de noms XML pour le nœud enfant.</span><span class="sxs-lookup"><span data-stu-id="c54dd-116">XML namespace prefix for the child node.</span></span> <span data-ttu-id="c54dd-117">Doit être un espace de noms XML global défini avec une instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-117">Must be a global XML namespace defined with an `Imports` statement.</span></span><br /><span data-ttu-id="c54dd-118">-   `Name`-Requis.</span><span class="sxs-lookup"><span data-stu-id="c54dd-118">-   `Name` - Required.</span></span> <span data-ttu-id="c54dd-119">Nom de nœud enfant local.</span><span class="sxs-lookup"><span data-stu-id="c54dd-119">Local child node name.</span></span> <span data-ttu-id="c54dd-120">Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c54dd-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
|>|<span data-ttu-id="c54dd-121">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="c54dd-121">Required.</span></span> <span data-ttu-id="c54dd-122">Indique la fin d'une propriété d'axe enfant.</span><span class="sxs-lookup"><span data-stu-id="c54dd-122">Denotes the end of a child axis property.</span></span>|  
  
## <a name="return-value"></a><span data-ttu-id="c54dd-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c54dd-123">Return Value</span></span>  
 <span data-ttu-id="c54dd-124">Une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c54dd-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c54dd-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="c54dd-125">Remarks</span></span>  
 <span data-ttu-id="c54dd-126">Vous pouvez utiliser une propriété d’axe enfant XML pour accéder aux nœuds enfants par nom d’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet, ou à partir d’une collection de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c54dd-126">You can use an XML child axis property to access child nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="c54dd-127">Utilisez la propriété XML `Value` pour accéder à la valeur du premier nœud enfant dans la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="c54dd-127">Use the XML `Value` property to access the value of the first child node in the returned collection.</span></span> <span data-ttu-id="c54dd-128">Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="c54dd-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="c54dd-129">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit les propriétés de l’axe enfant en appels à la <xref:System.Xml.Linq.XContainer.Elements%2A>méthode.</xref:System.Xml.Linq.XContainer.Elements%2A></span><span class="sxs-lookup"><span data-stu-id="c54dd-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts child axis properties to calls to the <xref:System.Xml.Linq.XContainer.Elements%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="c54dd-130">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="c54dd-130">XML Namespaces</span></span>  
 <span data-ttu-id="c54dd-131">Le nom inclus dans une propriété d'axe enfant peut utiliser uniquement des préfixes d'espace de noms XML déclarés globalement à l'aide de l'instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-131">The name in a child axis property can use only XML namespace prefixes declared globally with the `Imports` statement.</span></span> <span data-ttu-id="c54dd-132">Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML.</span><span class="sxs-lookup"><span data-stu-id="c54dd-132">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="c54dd-133">Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="c54dd-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c54dd-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="c54dd-134">Example</span></span>  
 <span data-ttu-id="c54dd-135">L'exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de l'objet `contact`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-135">The following example shows how to access the child nodes named `phone` from the `contact` object.</span></span>  
  
 <span data-ttu-id="c54dd-136">[!code-vb[VbXMLSamples&#17;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c54dd-136">[!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="c54dd-137">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c54dd-137">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="c54dd-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="c54dd-138">Example</span></span>  
 <span data-ttu-id="c54dd-139">L'exemple suivant montre comment accéder aux nœuds enfants nommés `phone` à partir de la collection retournée par la propriété d'axe enfant `contact` de l'objet `contacts`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-139">The following example shows how to access the child nodes named `phone` from the collection returned by the `contact` child axis property of the `contacts` object.</span></span>  
  
 <span data-ttu-id="c54dd-140">[!code-vb[VbXMLSamples&#18;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c54dd-140">[!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="c54dd-141">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c54dd-141">This code displays the following text:</span></span>  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="c54dd-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="c54dd-142">Example</span></span>  
 <span data-ttu-id="c54dd-143">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="c54dd-143">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="c54dd-144">Il utilise ensuite le préfixe de l'espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="c54dd-144">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="c54dd-145">[!code-vb[VbXMLSamples n °&19;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c54dd-145">[!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="c54dd-146">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="c54dd-146">This code displays the following text:</span></span>  
  
 `Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="c54dd-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c54dd-147">See Also</span></span>  
 <span data-ttu-id="c54dd-148"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c54dd-148"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="c54dd-149"> [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c54dd-149"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="c54dd-150"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="c54dd-150"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="c54dd-151"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="c54dd-151"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="c54dd-152"> [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="c54dd-152"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
