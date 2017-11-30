---
title: "Accès à des données XML à l’aide de XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c57b46e6-5c77-408f-bc4e-67a5dcc9cc05
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 27f5bccc2ab5f229e8b726b3bff18ea7a590f5c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-xml-data-using-xpathnavigator"></a><span data-ttu-id="3ef21-102">Accès à des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-102">Accessing XML Data using XPathNavigator</span></span>
<span data-ttu-id="3ef21-103">La classe <xref:System.Xml.XPath.XPathNavigator> fournit des méthodes permettant de parcourir des nœuds, d'extraire des données XML et d'accéder à des données XML fortement typées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3ef21-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to navigate nodes, extract XML data and access strongly typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3ef21-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3ef21-104">In This Section</span></span>  
 [<span data-ttu-id="3ef21-105">Navigation de jeu de nœud à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-105">Node Set Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="3ef21-106">Décrit les méthodes de navigation dans les collections de nœuds de la classe <xref:System.Xml.XPath.XPathNavigator> utilisées pour parcourir des nœuds dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3ef21-106">Describes the node set navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class used to navigate nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="3ef21-107">Attribut et la navigation entre les nœuds de Namespace à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-107">Attribute and Namespace Node Navigation Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 <span data-ttu-id="3ef21-108">Décrit les méthodes de navigation dans les attributs et les espaces de noms de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3ef21-108">Describes the attribute and namespace node navigation methods of the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="3ef21-109">Extraire des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-109">Extract XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/extract-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3ef21-110">Décrit les différentes méthodes d'extraction de données XML à partir d'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3ef21-110">Describes the various methods of extracting XML data from an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object.</span></span>  
  
 [<span data-ttu-id="3ef21-111">L’accès à fortement typée des données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-111">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="3ef21-112">Décrit l'accès à des données XML fortement typées dans un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument> à l'aide de la classe <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="3ef21-112">Describes accessing strongly-typed XML data in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
 [<span data-ttu-id="3ef21-113">Fonctions et Variables définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="3ef21-113">User Defined Functions and Variables</span></span>](../../../../docs/standard/data/xml/user-defined-functions-and-variables.md)  
 <span data-ttu-id="3ef21-114">Décrit l'implémentation d'une classe <xref:System.Xml.Xsl.XsltContext> personnalisée avec les interfaces <xref:System.Xml.Xsl.IXsltContextFunction> et <xref:System.Xml.Xsl.IXsltContextVariable> qui prennent en charge les fonctions et variables d'extension.</span><span class="sxs-lookup"><span data-stu-id="3ef21-114">Describes implementing a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef21-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ef21-115">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="3ef21-116">Traitement des données XML à l’aide du modèle de données XPath</span><span class="sxs-lookup"><span data-stu-id="3ef21-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="3ef21-117">La lecture des données XML à l’aide de XPathDocument et XmlDocument</span><span class="sxs-lookup"><span data-stu-id="3ef21-117">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)  
 [<span data-ttu-id="3ef21-118">Sélection, évaluation et mise en correspondance les données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-118">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="3ef21-119">Modification de données XML à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-119">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="3ef21-120">Validation de schéma à l’aide de XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="3ef21-120">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
