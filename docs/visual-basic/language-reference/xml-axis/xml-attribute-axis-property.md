---
title: "Propriété d’axe attribut XML (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlPropertyAttributeAxis
dev_langs:
- VB
helpviewer_keywords:
- attribute axis property [Visual Basic]
- Visual Basic code, accessing XML
- XML attribute axis property [Visual Basic]
- XML axis [Visual Basic], attribute
- XML [Visual Basic], accessing
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
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
ms.openlocfilehash: a3c327f4448287bcf6c45b9b6e26a1ef9ba13c16
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="xml-attribute-axis-property-visual-basic"></a><span data-ttu-id="06f9b-102">Propriété d'axe d'attribut XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06f9b-102">XML Attribute Axis Property (Visual Basic)</span></span>
<span data-ttu-id="06f9b-103">Fournit l’accès à la valeur d’un attribut pour un <xref:System.Xml.Linq.XElement>objet ou au premier élément dans une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="06f9b-103">Provides access to the value of an attribute for an <xref:System.Xml.Linq.XElement> object or to the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06f9b-104">Syntax</span></span>  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## <a name="parts"></a><span data-ttu-id="06f9b-105">Composants</span><span class="sxs-lookup"><span data-stu-id="06f9b-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="06f9b-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06f9b-106">Required.</span></span> <span data-ttu-id="06f9b-107">Un <xref:System.Xml.Linq.XElement>objet ou une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="06f9b-107">An <xref:System.Xml.Linq.XElement> object or a collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="06f9b-108">.@</span><span class="sxs-lookup"><span data-stu-id="06f9b-108">.@</span></span>  
 <span data-ttu-id="06f9b-109">Requis.</span><span class="sxs-lookup"><span data-stu-id="06f9b-109">Required.</span></span> <span data-ttu-id="06f9b-110">Indique le début d’une propriété d’axe d’attribut.</span><span class="sxs-lookup"><span data-stu-id="06f9b-110">Denotes the start of an attribute axis property.</span></span>  
  
 <  
 <span data-ttu-id="06f9b-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="06f9b-111">Optional.</span></span> <span data-ttu-id="06f9b-112">Indique le début du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="06f9b-112">Denotes the beginning of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 `attribute`  
 <span data-ttu-id="06f9b-113">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06f9b-113">Required.</span></span> <span data-ttu-id="06f9b-114">Nom de l’attribut auquel accéder, du formulaire [`prefix`:]`name`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-114">Name of the attribute to access, of the form [`prefix`:]`name`.</span></span>  
  
|<span data-ttu-id="06f9b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="06f9b-115">Part</span></span>|<span data-ttu-id="06f9b-116">Description</span><span class="sxs-lookup"><span data-stu-id="06f9b-116">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="06f9b-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="06f9b-117">Optional.</span></span> <span data-ttu-id="06f9b-118">Préfixe d’espace de noms XML pour l’attribut.</span><span class="sxs-lookup"><span data-stu-id="06f9b-118">XML namespace prefix for the attribute.</span></span> <span data-ttu-id="06f9b-119">Doit être un espace de noms XML global défini avec une instruction `Imports`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-119">Must be a global XML namespace defined with an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="06f9b-120">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="06f9b-120">Required.</span></span> <span data-ttu-id="06f9b-121">Nom d’attribut local.</span><span class="sxs-lookup"><span data-stu-id="06f9b-121">Local attribute name.</span></span> <span data-ttu-id="06f9b-122">Consultez la page [nom des attributs et éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="06f9b-122">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="06f9b-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="06f9b-123">Optional.</span></span> <span data-ttu-id="06f9b-124">Indique la fin du nom de l’attribut lorsque `attribute` n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="06f9b-124">Denotes the end of the name of the attribute when `attribute` is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06f9b-125">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="06f9b-125">Return Value</span></span>  
 <span data-ttu-id="06f9b-126">Chaîne qui contient la valeur de `attribute`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-126">A string that contains the value of `attribute`.</span></span> <span data-ttu-id="06f9b-127">Si le nom de l’attribut n’existe pas, `Nothing` est retourné.</span><span class="sxs-lookup"><span data-stu-id="06f9b-127">If the attribute name does not exist, `Nothing` is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f9b-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="06f9b-128">Remarks</span></span>  
 <span data-ttu-id="06f9b-129">Vous pouvez utiliser une propriété d’axe XML attribut pour accéder à la valeur d’un attribut par nom d’un <xref:System.Xml.Linq.XElement>objet ou du premier élément dans une collection de <xref:System.Xml.Linq.XElement>objets.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="06f9b-129">You can use an XML attribute axis property to access the value of an attribute by name from an <xref:System.Xml.Linq.XElement> object or from the first element in a collection of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="06f9b-130">Vous pouvez récupérer une valeur d’attribut par nom ou ajouter un nouvel attribut à un élément en spécifiant un nouveau nom précédé par l’identificateur @.</span><span class="sxs-lookup"><span data-stu-id="06f9b-130">You can retrieve an attribute value by name, or add a new attribute to an element by specifying a new name preceded by the @ identifier.</span></span>  
  
 <span data-ttu-id="06f9b-131">Lorsque vous faites référence à un attribut XML en utilisant l’identificateur @, la valeur d’attribut est retournée sous forme de chaîne et vous n’avez pas besoin de spécifier explicitement le <xref:System.Xml.Linq.XAttribute.Value%2A>propriété.</xref:System.Xml.Linq.XAttribute.Value%2A></span><span class="sxs-lookup"><span data-stu-id="06f9b-131">When you refer to an XML attribute using the @ identifier, the attribute value is returned as a string and you do not need to explicitly specify the <xref:System.Xml.Linq.XAttribute.Value%2A> property.</span></span>  
  
 <span data-ttu-id="06f9b-132">Les règles d’affectation de noms pour les attributs XML diffèrent des règles d’affectation de noms pour les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identificateurs.</span><span class="sxs-lookup"><span data-stu-id="06f9b-132">The naming rules for XML attributes differ from the naming rules for [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] identifiers.</span></span> <span data-ttu-id="06f9b-133">Pour accéder à un attribut XML qui a un nom qui n’est pas un identificateur Visual Basic valid, placez le nom entre crochets pointus (\< et >).</span><span class="sxs-lookup"><span data-stu-id="06f9b-133">To access an XML attribute that has a name that is not a valid Visual Basic identifier, enclose the name in angle brackets (\< and >).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="06f9b-134">Espaces de noms XML</span><span class="sxs-lookup"><span data-stu-id="06f9b-134">XML Namespaces</span></span>  
 <span data-ttu-id="06f9b-135">Le nom de la propriété d’axe d’attribut peut utiliser uniquement des préfixes d’espace de noms XML, déclarés globalement à l’aide de la `Imports` instruction.</span><span class="sxs-lookup"><span data-stu-id="06f9b-135">The name in an attribute axis property can use only XML namespace prefixes declared globally by using the `Imports` statement.</span></span> <span data-ttu-id="06f9b-136">Il ne peut pas utiliser des préfixes d'espace de noms XML déclarés localement dans des littéraux d'éléments XML.</span><span class="sxs-lookup"><span data-stu-id="06f9b-136">It cannot use XML namespace prefixes declared locally within XML element literals.</span></span> <span data-ttu-id="06f9b-137">Pour plus d’informations, consultez [l’instruction Imports (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="06f9b-137">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06f9b-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="06f9b-138">Example</span></span>  
 <span data-ttu-id="06f9b-139">L’exemple suivant montre comment obtenir les valeurs des attributs XML nommés `type` à partir d’une collection d’éléments XML nommés `phone`.</span><span class="sxs-lookup"><span data-stu-id="06f9b-139">The following example shows how to get the values of the XML attributes named `type` from a collection of XML elements that are named `phone`.</span></span>  
  
 <span data-ttu-id="06f9b-140">[!code-vb[VbXMLSamples&#12;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="06f9b-140">[!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]</span></span>  
  
 <span data-ttu-id="06f9b-141">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="06f9b-141">This code displays the following text:</span></span>  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## <a name="example"></a><span data-ttu-id="06f9b-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="06f9b-142">Example</span></span>  
 <span data-ttu-id="06f9b-143">L’exemple suivant montre comment créer des attributs pour un élément XML de façon déclarative, dans le cadre du XML et dynamiquement en ajoutant un attribut à une instance d’un <xref:System.Xml.Linq.XElement>objet.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="06f9b-143">The following example shows how to create attributes for an XML element both declaratively, as part of the XML, and dynamically by adding an attribute to an instance of an <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="06f9b-144">Le `type` attribut est créé de façon déclarative et `owne`r attribut est créée dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="06f9b-144">The `type` attribute is created declaratively and the `owne`r attribute is created dynamically.</span></span>  
  
 <span data-ttu-id="06f9b-145">[!code-vb[VbXMLSamples&#44;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="06f9b-145">[!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]</span></span>  
  
 <span data-ttu-id="06f9b-146">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="06f9b-146">This code displays the following text:</span></span>  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## <a name="example"></a><span data-ttu-id="06f9b-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="06f9b-147">Example</span></span>  
 <span data-ttu-id="06f9b-148">L’exemple suivant utilise la syntaxe de crochets pointus pour obtenir la valeur de l’attribut XML nommé `number-type`, qui n’est pas un identificateur valide dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="06f9b-148">The following example uses the angle bracket syntax to get the value of the XML attribute named `number-type`, which is not a valid identifier in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="06f9b-149">[!code-vb[VbXMLSamples&#13;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="06f9b-149">[!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]</span></span>  
  
 <span data-ttu-id="06f9b-150">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="06f9b-150">This code displays the following text:</span></span>  
  
 `Phone type: work`  
  
## <a name="example"></a><span data-ttu-id="06f9b-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="06f9b-151">Example</span></span>  
 <span data-ttu-id="06f9b-152">L'exemple suivant déclare `ns` en tant que préfixe d'espace de noms XML.</span><span class="sxs-lookup"><span data-stu-id="06f9b-152">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="06f9b-153">Il utilise ensuite le préfixe d’espace de noms pour créer un littéral XML et accéder au premier nœud enfant avec le nom qualifié «`ns:name`».</span><span class="sxs-lookup"><span data-stu-id="06f9b-153">It then uses the prefix of the namespace to create an XML literal and access the first child node with the qualified name "`ns:name`".</span></span>  
  
 <span data-ttu-id="06f9b-154">[!code-vb[VbXMLSamples&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="06f9b-154">[!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]</span></span>  
  
 <span data-ttu-id="06f9b-155">Ce code affiche le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="06f9b-155">This code displays the following text:</span></span>  
  
 `Phone type: home`  
  
## <a name="see-also"></a><span data-ttu-id="06f9b-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06f9b-156">See Also</span></span>  
 <span data-ttu-id="06f9b-157"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="06f9b-157"><xref:System.Xml.Linq.XElement></span></span>   
<span data-ttu-id="06f9b-158"> [Propriétés d’axe XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span><span class="sxs-lookup"><span data-stu-id="06f9b-158"> [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md) </span></span>  
<span data-ttu-id="06f9b-159"> [Littéraux XML](../../../visual-basic/language-reference/xml-literals/index.md) </span><span class="sxs-lookup"><span data-stu-id="06f9b-159"> [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md) </span></span>  
<span data-ttu-id="06f9b-160"> [Création de code XML en Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="06f9b-160"> [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="06f9b-161"> [Nom des attributs et des éléments XML déclarés](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span><span class="sxs-lookup"><span data-stu-id="06f9b-161"> [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)</span></span>
