---
title: "Propriété d’axe Descendant XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyDescendantsAxis
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
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
ms.openlocfilehash: e84a8bb989ebbed57595ebf93cef620027a04328
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="167a6-102">Propriété d'axe descendant XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="167a6-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="167a6-103">Fournit l’accès aux descendants de ce qui suit : un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="167a6-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="167a6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="167a6-104">Syntax</span></span>  
  
```  
  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="167a6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="167a6-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="167a6-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="167a6-106">Required.</span></span> <span data-ttu-id="167a6-107">Un <xref:System.Xml.Linq.XElement>objet, un <xref:System.Xml.Linq.XDocument>objet, une collection de <xref:System.Xml.Linq.XElement>objets, ou une collection de <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="167a6-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="167a6-108">...<</span><span class="sxs-lookup"><span data-stu-id="167a6-108">...<</span></span>  
 <span data-ttu-id="167a6-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="167a6-109">Required.</span></span> <span data-ttu-id="167a6-110">Indique le début d’une propriété d’axe descendant.</span><span class="sxs-lookup"><span data-stu-id="167a6-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="167a6-111">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="167a6-111">Required.</span></span> <span data-ttu-id="167a6-112">Nom des nœuds descendants auxquels accéder, sous la forme [`prefix``:`]`name`.</span><span class="sxs-lookup"><span data-stu-id="167a6-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="167a6-113">Élément</span><span class="sxs-lookup"><span data-stu-id="167a6-113">Part</span></span>|<span data-ttu-id="167a6-114">Description</span><span class="sxs-lookup"><span data-stu-id="167a6-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="167a6-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="167a6-115">Optional.</span></span> <span data-ttu-id="167a6-116">Préfixe d’espace de noms XML pour le nœud descendant.</span><span class="sxs-lookup"><span data-stu-id="167a6-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="167a6-117">Doit être un espace de noms XML global qui est défini en utilisant un `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="167a6-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="167a6-118">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="167a6-118">Required.</span></span> <span data-ttu-id="167a6-119">Nom local du nœud descendant.</span><span class="sxs-lookup"><span data-stu-id="167a6-119">Local name of the descendant node.</span></span> <span data-ttu-id="167a6-120">Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="167a6-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="167a6-121">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="167a6-121">Required.</span></span> <span data-ttu-id="167a6-122">Indique la fin d’une propriété d’axe descendant.</span><span class="sxs-lookup"><span data-stu-id="167a6-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="167a6-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="167a6-123">Return Value</span></span>  
 <span data-ttu-id="167a6-124">Une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="167a6-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="167a6-125">Remarques</span><span class="sxs-lookup"><span data-stu-id="167a6-125">Remarks</span></span>  
 <span data-ttu-id="167a6-126">Vous pouvez utiliser une propriété d’axe descendant XML pour accéder aux nœuds descendants par nom d’un <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objet, ou à partir d’une collection de <xref:System.Xml.Linq.XElement>ou <xref:System.Xml.Linq.XDocument>objets.</xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="167a6-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="167a6-127">Utilisez le code XML `Value` propriété pour accéder à la valeur du premier nœud descendant dans la collection retournée.</span><span class="sxs-lookup"><span data-stu-id="167a6-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="167a6-128">Pour plus d’informations, consultez [propriété de valeur XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span><span class="sxs-lookup"><span data-stu-id="167a6-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="167a6-129">Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur convertit des propriétés d’axes descendants en appels à la <xref:System.Xml.Linq.XContainer.Descendants%2A>méthode.</xref:System.Xml.Linq.XContainer.Descendants%2A></span><span class="sxs-lookup"><span data-stu-id="167a6-129">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="167a6-130">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="167a6-130">XML Namespaces</span></span>  
 <span data-ttu-id="167a6-131">Le nom d’une propriété d’axe descendant peut utiliser uniquement les espaces de noms XML déclarés globalement avec le `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="167a6-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="167a6-132">Il ne peut pas utiliser les espaces de noms XML déclarés localement dans les littéraux d’éléments XML.</span><span class="sxs-lookup"><span data-stu-id="167a6-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="167a6-133">Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="167a6-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="167a6-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="167a6-134">Example</span></span>  
 <span data-ttu-id="167a6-135">L’exemple suivant montre comment accéder à la valeur du premier nœud descendant nommé `name` et les valeurs de tous les nœuds descendants nommés `phone` à partir de la `contacts` objet.</span><span class="sxs-lookup"><span data-stu-id="167a6-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 <span data-ttu-id="167a6-136">[!code-vb[VbXMLSamples&#25;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="167a6-136">[!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="167a6-137">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="167a6-137">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="167a6-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="167a6-138">Example</span></span>  
 <span data-ttu-id="167a6-139">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="167a6-139">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="167a6-140">Il utilise ensuite le préfixe d’espace de noms pour créer un littéral XML et accéder à la valeur du premier nœud enfant avec le nom qualifié `ns:name`.</span><span class="sxs-lookup"><span data-stu-id="167a6-140">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 <span data-ttu-id="167a6-141">[!code-vb[VbXMLSamples&#26;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="167a6-141">[!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="167a6-142">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="167a6-142">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="167a6-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="167a6-143">See Also</span></span>  
 <span data-ttu-id="167a6-144"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="167a6-144"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="167a6-145"> [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="167a6-145"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="167a6-146"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="167a6-146"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="167a6-147"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="167a6-147"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="167a6-148"> [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="167a6-148"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
