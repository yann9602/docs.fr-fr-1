---
title: "Sorties à partir de XslTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92bf2d7184ca2eb8b17c1d83130c66d1f33f0483
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="outputs-from-an-xsltransform"></a><span data-ttu-id="8e654-102">Sorties à partir de XslTransform</span><span class="sxs-lookup"><span data-stu-id="8e654-102">Outputs from an XslTransform</span></span>
<span data-ttu-id="8e654-103">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="8e654-103">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e654-104">La classe <xref:System.Xml.Xsl.XslTransform> est obsolète dans le [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e654-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="8e654-105">Vous pouvez effectuer des transformations XSLT (Extensible Stylesheet Language Transformation) à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="8e654-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="8e654-106">Consultez [à l’aide de la classe XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) et [migration depuis la classe XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="8e654-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="8e654-107">Dans la mesure où les feuilles de style peuvent déterminer le format de sortie à l'aide d'une instruction `<xsl:output>` avec l'attribut `method`, le tableau suivant décrit le format de sortie lors de l'utilisation de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> pour écrire la sortie, et le format de sortie est déclaré en tant qu'objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="8e654-107">Since style sheets can determine the output format using an `<xsl:output>` statement with the `method` attribute, the following table describes what the output format is when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is used to write the output, and the output format is declared as a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="8e654-108">Le tableau suivant décrit ce qui se produit lorsqu'un type de sortie est déclaré par la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> conjointement à l'utilisation d'une instruction `<xsl:output>` :</span><span class="sxs-lookup"><span data-stu-id="8e654-108">The following table describes what happens when an output type is declared by the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method in conjunction with the use of an `<xsl:output>` statement:</span></span>  
  
|<span data-ttu-id="8e654-109">\<xsl : output method = > attribut</span><span class="sxs-lookup"><span data-stu-id="8e654-109">\<xsl:output method = > attribute</span></span>|<span data-ttu-id="8e654-110">Format du résultat</span><span class="sxs-lookup"><span data-stu-id="8e654-110">Result format</span></span>|  
|-----------------------------------------|-------------------|  
|<span data-ttu-id="8e654-111">method="xml"</span><span class="sxs-lookup"><span data-stu-id="8e654-111">method="xml"</span></span>|<span data-ttu-id="8e654-112">XML</span><span class="sxs-lookup"><span data-stu-id="8e654-112">XML</span></span>|  
|<span data-ttu-id="8e654-113">method="html"</span><span class="sxs-lookup"><span data-stu-id="8e654-113">method="html"</span></span>|<span data-ttu-id="8e654-114">HTML</span><span class="sxs-lookup"><span data-stu-id="8e654-114">HTML</span></span>|  
|<span data-ttu-id="8e654-115">method="text"</span><span class="sxs-lookup"><span data-stu-id="8e654-115">method="text"</span></span>|<span data-ttu-id="8e654-116">Texte</span><span class="sxs-lookup"><span data-stu-id="8e654-116">Text</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8e654-117">Remarque : l'instruction `<xsl:output>` est ignorée lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="8e654-117">Note: The `<xsl:output>` statement is ignored when the output of the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="8e654-118">Les attributs suivants sont pris en charge lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> ou <xref:System.IO.TextWriter> :</span><span class="sxs-lookup"><span data-stu-id="8e654-118">The following attributes are supported when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream> or <xref:System.IO.TextWriter>:</span></span>  
  
-   <span data-ttu-id="8e654-119">encoding*</span><span class="sxs-lookup"><span data-stu-id="8e654-119">encoding*</span></span>  
  
-   <span data-ttu-id="8e654-120">omit-xml-declaration</span><span class="sxs-lookup"><span data-stu-id="8e654-120">omit-xml-declaration</span></span>  
  
-   <span data-ttu-id="8e654-121">autonomes</span><span class="sxs-lookup"><span data-stu-id="8e654-121">standalone</span></span>  
  
-   <span data-ttu-id="8e654-122">doctype-public</span><span class="sxs-lookup"><span data-stu-id="8e654-122">doctype-public</span></span>  
  
-   <span data-ttu-id="8e654-123">doctype-system</span><span class="sxs-lookup"><span data-stu-id="8e654-123">doctype-system</span></span>  
  
-   <span data-ttu-id="8e654-124">cdata-section-elements</span><span class="sxs-lookup"><span data-stu-id="8e654-124">cdata-section-elements</span></span>  
  
-   <span data-ttu-id="8e654-125">indent</span><span class="sxs-lookup"><span data-stu-id="8e654-125">indent</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8e654-126">*l'attribut encoding est ignoré lorsque la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> envoie sa sortie à un objet <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="8e654-126">*the encoding attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method is sending its output to a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="8e654-127">La propriété encoding sur l'objet <xref:System.IO.TextWriter> est utilisée à la place.</span><span class="sxs-lookup"><span data-stu-id="8e654-127">The encoding property on the <xref:System.IO.TextWriter> is used instead.</span></span>  
  
 <span data-ttu-id="8e654-128">Les attributs suivants sont ignorés lorsque la sortie de la méthode <xref:System.Xml.Xsl.XslTransform.Transform%2A> est un objet <xref:System.IO.Stream> :</span><span class="sxs-lookup"><span data-stu-id="8e654-128">The following attribute is ignored when the <xref:System.Xml.Xsl.XslTransform.Transform%2A> method output is a <xref:System.IO.Stream>:</span></span>  
  
-   <span data-ttu-id="8e654-129">version : la version est toujours 1.0 ;</span><span class="sxs-lookup"><span data-stu-id="8e654-129">version: the version is always 1.0</span></span>  
  
-   <span data-ttu-id="8e654-130">media-type : le type de média.</span><span class="sxs-lookup"><span data-stu-id="8e654-130">media-type: the media-type</span></span>  
  
## <a name="escaping-special-characters"></a><span data-ttu-id="8e654-131">Échappement de caractères spéciaux</span><span class="sxs-lookup"><span data-stu-id="8e654-131">Escaping Special Characters</span></span>  
 <span data-ttu-id="8e654-132">La balise `<xsl:text disable-output-escaping>` est utilisée pour indiquer si des caractères spéciaux doivent ou non être placés dans une séquence d'échappement dans un formulaire XML (par exemple, en substituant `<&lt>` au symbole `"<"`) ou laissés tels quels.</span><span class="sxs-lookup"><span data-stu-id="8e654-132">The `<xsl:text disable-output-escaping>` tag is used to indicate whether or not special characters need to be escaped into an XML form (for example, using `<&lt>` in place of the `"<"` symbol) or left in the present condition.</span></span> <span data-ttu-id="8e654-133">L'attribut `disable-output-escaping` est ignoré lors de la transformation en un objet <xref:System.Xml.XmlReader> ou <xref:System.Xml.XmlWriter> et n'a pas d'effet sur les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="8e654-133">The `disable-output-escaping` attribute is ignored when transforming to an <xref:System.Xml.XmlReader> or <xref:System.Xml.XmlWriter> object and has no effect on special characters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e654-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e654-134">See Also</span></span>  
 [<span data-ttu-id="8e654-135">XslTransform Class Implements the XSLT Processor</span><span class="sxs-lookup"><span data-stu-id="8e654-135">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
