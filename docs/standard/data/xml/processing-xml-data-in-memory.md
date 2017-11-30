---
title: "Traitement de données XML en mémoire"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ec4ccbff095071b279e07cee6a1aab3ca830423f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="ea1ee-102">Traitement de données XML en mémoire</span><span class="sxs-lookup"><span data-stu-id="ea1ee-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="ea1ee-103">Microsoft .NET Framework comprend trois modèles pour le traitement des données XML : le <xref:System.Xml.XmlDocument> (classe), le <xref:System.Xml.XPath.XPathDocument> (classe), et [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span><span class="sxs-lookup"><span data-stu-id="ea1ee-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13).</span></span>  
  
 <span data-ttu-id="ea1ee-104">La classe <xref:System.Xml.XmlDocument> implémente les recommandations du W3C relatives aux modèles objet de document (DOM), niveaux 1 et 2 (noyau).</span><span class="sxs-lookup"><span data-stu-id="ea1ee-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="ea1ee-105">Le DOM est une représentation sous la forme d'une arborescence (cache) en mémoire d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="ea1ee-106">L'objet <xref:System.Xml.XmlDocument> et les classes y afférentes permettent de construire des documents XML, de charger et d'accéder à des données, de modifier des données et d'enregistrer des modifications.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="ea1ee-107">La classe <xref:System.Xml.XPath.XPathDocument> est un magasin de données en mémoire en lecture seule basé sur le modèle de données XPath.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="ea1ee-108">La classe <xref:System.Xml.XPath.XPathNavigator> propose plusieurs options de modification et fonctionnalités de navigation à l'aide d'un modèle de curseur entre des documents XML contenus dans la classe <xref:System.Xml.XPath.XPathDocument> en lecture seule ainsi que dans la classe <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="ea1ee-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) est le nouveau modèle dans le .NET Framework version 3.5 pour le traitement des données XML.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-109">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) is the new model in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="ea1ee-110">Il s’agit d’un modèle en mémoire qui exploite [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span><span class="sxs-lookup"><span data-stu-id="ea1ee-110">It is an in-memory model that leverages [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span> <span data-ttu-id="ea1ee-111">LINQ étend la syntaxe des langages C# et Visual Basic pour fournir de nouvelles capacités de requête.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea1ee-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ea1ee-112">In This Section</span></span>  
 [<span data-ttu-id="ea1ee-113">Traitement des données XML à l’aide du modèle DOM</span><span class="sxs-lookup"><span data-stu-id="ea1ee-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="ea1ee-114">Explique l'utilisation de l'objet <xref:System.Xml.XmlDocument> et des classes y afférentes pour le traitement de données XML.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="ea1ee-115">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="ea1ee-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="ea1ee-116">Explique l'utilisation des classes <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument> et <xref:System.Xml.XPath.XPathNavigator> pour le traitement de données XML.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="ea1ee-117">Traitement des données XML à l’aide de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="ea1ee-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="ea1ee-118">Fournit une brève vue d'ensemble de LINQ to XML et indique des liens vers la documentation LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="ea1ee-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ea1ee-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="ea1ee-119">Related Sections</span></span>  
 [<span data-ttu-id="ea1ee-120">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="ea1ee-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
