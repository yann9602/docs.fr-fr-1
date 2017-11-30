---
title: "Validation de schéma XML (XSD) avec XmlSchemaSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 359b10eb-ec05-4cc6-ac96-c2b060afc4de
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a6cf857ccecbdac88453fd1fba6e93d609196b1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xml-schema-xsd-validation-with-xmlschemaset"></a><span data-ttu-id="9f973-102">Validation de schéma XML (XSD) avec XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="9f973-102">XML Schema (XSD) Validation with XmlSchemaSet</span></span>
<span data-ttu-id="9f973-103">Les documents XML peuvent être validés par rapport à un schéma XSD (XML Schema Definition) dans un objet <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="9f973-103">XML documents can be validated against an XML schema definition language (XSD) schema in an <xref:System.Xml.Schema.XmlSchemaSet>.</span></span>  
  
## <a name="validating-xml-documents"></a><span data-ttu-id="9f973-104">Validation de documents XML</span><span class="sxs-lookup"><span data-stu-id="9f973-104">Validating XML Documents</span></span>  
 <span data-ttu-id="9f973-105">Les documents XML sont validés par la méthode <xref:System.Xml.XmlReader.Create%2A> de la classe <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9f973-105">XML documents are validated by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class.</span></span> <span data-ttu-id="9f973-106">Pour valider un document XML, vous construisez un objet <xref:System.Xml.XmlReaderSettings> qui contient un schéma de langage XSD (XML Schema Definition) permettant de valider le document XML.</span><span class="sxs-lookup"><span data-stu-id="9f973-106">To validate an XML document, construct an <xref:System.Xml.XmlReaderSettings> object that contains an XML schema definition language (XSD) schema with which to validate the XML document.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f973-107">Le <xref:System.Xml.Schema> espace de noms contient des méthodes d’extension qui facilitent la validation d’une arborescence XML par rapport à un fichier XSD lors de l’utilisation [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="9f973-107">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XSD file when using [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span> <span data-ttu-id="9f973-108">Pour plus d’informations sur la validation de documents XML avec LINQ to XML, consultez [Comment : valider le XSD à l’aide de](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span><span class="sxs-lookup"><span data-stu-id="9f973-108">For more information on validating XML documents with LINQ to XML, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b).</span></span>  
  
 <span data-ttu-id="9f973-109">Vous pouvez ajouter un schéma individuel ou un jeu de schémas (sous forme de <xref:System.Xml.Schema.XmlSchemaSet>) à un <xref:System.Xml.Schema.XmlSchemaSet> en le passant en tant que paramètre à la méthode <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> de <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="9f973-109">An individual schema or a set of schemas (as an <xref:System.Xml.Schema.XmlSchemaSet>) can be added to an <xref:System.Xml.Schema.XmlSchemaSet> by passing either one as a parameter to the <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> method of <xref:System.Xml.Schema.XmlSchemaSet>.</span></span> <span data-ttu-id="9f973-110">Notez que lorsque vous validez un document, son espace de noms cible doit correspondre à celui de l'espace de noms cible du jeu de schémas.</span><span class="sxs-lookup"><span data-stu-id="9f973-110">Note that when validating a document the target namespace of the document must match the target namespace of the schema in the schema set.</span></span>  
  
 <span data-ttu-id="9f973-111">Voici un exemple de document XML.</span><span class="sxs-lookup"><span data-stu-id="9f973-111">The following is an example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#5](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xml#5)]  
  
 <span data-ttu-id="9f973-112">Voici le schéma qui valide l'exemple de document XML.</span><span class="sxs-lookup"><span data-stu-id="9f973-112">The following is the schema that validates the example XML document.</span></span>  
  
 [!code-xml[XSDInference Examples#6](../../../../samples/snippets/xml/VS_Snippets_Data/XSDInference Examples/XML/contosoBooks.xsd#6)]  
  
 <span data-ttu-id="9f973-113">Dans l'exemple de code suivant, le schéma ci-dessus est ajouté à la propriété <xref:System.Xml.Schema.XmlSchemaSet> de l'objet <xref:System.Xml.XmlReaderSettings.Schemas%2A> de l'objet <xref:System.Xml.XmlReaderSettings>.</span><span class="sxs-lookup"><span data-stu-id="9f973-113">In the code example that follows, the schema above is added to the <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> object.</span></span> <span data-ttu-id="9f973-114">L'objet <xref:System.Xml.XmlReaderSettings> est passé sous forme de paramètre à la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader> qui valide le document XML ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="9f973-114">The <xref:System.Xml.XmlReaderSettings> object is passed as a parameter to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object, which validates the XML document above.</span></span>  
  
 <span data-ttu-id="9f973-115">La propriété <xref:System.Xml.XmlReaderSettings.ValidationType%2A> de l'objet <xref:System.Xml.XmlReaderSettings> est définie sur `Schema` pour effectuer la validation du document XML par la méthode <xref:System.Xml.XmlReader.Create%2A> de l'objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9f973-115">The <xref:System.Xml.XmlReaderSettings.ValidationType%2A> property of the <xref:System.Xml.XmlReaderSettings> object is set to `Schema` to enforce validation of the XML document by the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> object.</span></span> <span data-ttu-id="9f973-116">Un objet <xref:System.Xml.Schema.ValidationEventHandler> est ajouté à l'objet <xref:System.Xml.XmlReaderSettings> pour gérer tous les événements <xref:System.Xml.Schema.XmlSeverityType.Warning> ou <xref:System.Xml.Schema.XmlSeverityType.Error> déclenchés par des erreurs trouvées lors du processus de validation du document et du schéma XML.</span><span class="sxs-lookup"><span data-stu-id="9f973-116">A <xref:System.Xml.Schema.ValidationEventHandler> is added to the <xref:System.Xml.XmlReaderSettings> object to handle any <xref:System.Xml.Schema.XmlSeverityType.Warning> or <xref:System.Xml.Schema.XmlSeverityType.Error> events raised by errors found during the validation process of both the XML document and the schema.</span></span>  
  
 [!code-cpp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaSetOverall Example/CPP/xmlschemasetexample.cpp#1)]
 [!code-csharp[XmlSchemaSetOverall Example#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaSetOverall Example/CS/xmlschemasetexample.cs#1)]
 [!code-vb[XmlSchemaSetOverall Example#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaSetOverall Example/VB/xmlschemasetexample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9f973-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f973-117">See Also</span></span>  
 [<span data-ttu-id="9f973-118">XmlSchemaSet pour la Compilation du schéma</span><span class="sxs-lookup"><span data-stu-id="9f973-118">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="9f973-119">Utilisation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="9f973-119">Working with XML Schemas</span></span>](../../../../docs/standard/data/xml/working-with-xml-schemas.md)
