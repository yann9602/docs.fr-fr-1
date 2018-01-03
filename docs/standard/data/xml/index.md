---
title: "Documents et données XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 22a2eb72dc06a644171c143a61698e661d2c66c6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="d0acb-102">Documents et données XML</span><span class="sxs-lookup"><span data-stu-id="d0acb-102">XML Documents and Data</span></span>
<span data-ttu-id="d0acb-103">Le .NET Framework fournit un jeu de classes complet et intégré qui vous permet de créer facilement des applications capables de traiter du code XML.</span><span class="sxs-lookup"><span data-stu-id="d0acb-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="d0acb-104">Les classes dans les espaces de noms suivants prennent en charge l’analyse et l’écriture de code XML, l’édition de donnés XML en mémoire, la validation de données et la transformation XSLT.</span><span class="sxs-lookup"><span data-stu-id="d0acb-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>  
  
-   <xref:System.Xml>  
  
-   <xref:System.Xml.XPath>  
  
-   <xref:System.Xml.Xsl>  
  
-   <xref:System.Xml.Schema>  
  
-   <xref:System.Xml.Linq>  
  
 <span data-ttu-id="d0acb-105">Pour obtenir une liste complète, consultez la page web [Espaces de noms System.Xml](http://msdn.microsoft.com/library/gg145036.aspx).</span><span class="sxs-lookup"><span data-stu-id="d0acb-105">For a full list, see the [System.Xml Namespaces](http://msdn.microsoft.com/library/gg145036.aspx) webpage.</span></span>  
  
 <span data-ttu-id="d0acb-106">Les classes dans ces espaces de noms prennent en charge les recommandations World Wide Web Consortium (W3C).</span><span class="sxs-lookup"><span data-stu-id="d0acb-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="d0acb-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="d0acb-107">For example:</span></span>  
  
-   <span data-ttu-id="d0acb-108">La classe <xref:System.Xml.XmlDocument?displayProperty=nameWithType> implémente les recommandations du [W3C relatives aux modèles objet de documents (DOM) de niveau 1](http://www.w3.org/TR/REC-DOM-Level-1/) et [2 (standard)](http://www.w3.org/TR/DOM-Level-2-Core/).</span><span class="sxs-lookup"><span data-stu-id="d0acb-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](http://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](http://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>  
  
-   <span data-ttu-id="d0acb-109">Les classes <xref:System.Xml.XmlReader?displayProperty=nameWithType> et <xref:System.Xml.XmlWriter?displayProperty=nameWithType> sont conformes aux recommandations du [W3C relatives à XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) et aux [espaces de noms dans XML](http://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="d0acb-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](http://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](http://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>  
  
-   <span data-ttu-id="d0acb-110">Les schémas de la classe <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> sont conformes aux recommandations du [W3C relatives aux structures (Part 1)](http://www.w3.org/TR/xmlschema-1/) et aux [types de données (Part 2) du schéma XML](http://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="d0acb-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](http://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](http://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>  
  
-   <span data-ttu-id="d0acb-111">Les classes de l’espace de noms <xref:System.Xml.Xsl?displayProperty=nameWithType> prennent en charge les transformations XSLT qui sont conformes à la recommandation [W3C XSLT 1.0](http://www.w3.org/TR/xslt).</span><span class="sxs-lookup"><span data-stu-id="d0acb-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](http://www.w3.org/TR/xslt) recommendation.</span></span>  
  
 <span data-ttu-id="d0acb-112">Les classes XML du .NET Framework offrent les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="d0acb-112">The XML classes in the .NET Framework provide these benefits:</span></span>  
  
-   <span data-ttu-id="d0acb-113">**Productivité** :</span><span class="sxs-lookup"><span data-stu-id="d0acb-113">**Productivity.**</span></span> <span data-ttu-id="d0acb-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) facilite la programmation avec XML et offre une expérience de requête similaire à SQL.</span><span class="sxs-lookup"><span data-stu-id="d0acb-114">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>  
  
-   <span data-ttu-id="d0acb-115">**Extensibilité** :</span><span class="sxs-lookup"><span data-stu-id="d0acb-115">**Extensibility.**</span></span> <span data-ttu-id="d0acb-116">Les classes XML du .NET Framework sont extensibles grâce à l'utilisation de classes de base abstraites et de méthodes virtuelles.</span><span class="sxs-lookup"><span data-stu-id="d0acb-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="d0acb-117">Par exemple, vous pouvez créer une classe dérivée de la classe <xref:System.Xml.XmlUrlResolver> qui stocke le flux mis en cache sur le disque local.</span><span class="sxs-lookup"><span data-stu-id="d0acb-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>  
  
-   <span data-ttu-id="d0acb-118">**Architecture enfichable** :</span><span class="sxs-lookup"><span data-stu-id="d0acb-118">**Pluggable architecture.**</span></span> <span data-ttu-id="d0acb-119">Le .NET Framework propose une architecture dans laquelle les composants peuvent s'utiliser réciproquement et où les données peuvent être transmises en continu entre les composants.</span><span class="sxs-lookup"><span data-stu-id="d0acb-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="d0acb-120">Par exemple, un magasin de données, tel qu'un objet <xref:System.Xml.XPath.XPathDocument> ou <xref:System.Xml.XmlDocument>, peut être transformé à l'aide de la classe <xref:System.Xml.Xsl.XslCompiledTransform>, et la sortie peut ensuite être soit transmise sous la forme de flux à un autre magasin, soit retournée sous la forme d'un flux à partir d'un service web.</span><span class="sxs-lookup"><span data-stu-id="d0acb-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>  
  
-   <span data-ttu-id="d0acb-121">**Performances**</span><span class="sxs-lookup"><span data-stu-id="d0acb-121">**Performance.**</span></span> <span data-ttu-id="d0acb-122">Pour améliorer les performances des applications, certaines des classes XML du .NET Framework prennent en charge un modèle basé sur les flux de données ayant les caractéristiques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d0acb-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>  
  
    -   <span data-ttu-id="d0acb-123">Mise en cache minimale pour une analyse avant uniquement et de type pull (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="d0acb-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="d0acb-124">Validation avant uniquement (<xref:System.Xml.XmlReader>).</span><span class="sxs-lookup"><span data-stu-id="d0acb-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>  
  
    -   <span data-ttu-id="d0acb-125">Navigation par curseur qui minimise la création de nœuds à un seul nœud virtuel, tout en permettant l'accès aléatoire au document (<xref:System.Xml.XPath.XPathNavigator>).</span><span class="sxs-lookup"><span data-stu-id="d0acb-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>  
  
     <span data-ttu-id="d0acb-126">Pour de meilleures performances chaque fois que le traitement XSLT est nécessaire, vous pouvez utiliser la classe <xref:System.Xml.XPath.XPathDocument> qui est un magasin optimisé en lecture seule pour les requêtes XPath, conçu pour fonctionner de manière efficace avec la classe <xref:System.Xml.Xsl.XslCompiledTransform>.</span><span class="sxs-lookup"><span data-stu-id="d0acb-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
-   <span data-ttu-id="d0acb-127">**Intégration à ADO.NET** :</span><span class="sxs-lookup"><span data-stu-id="d0acb-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="d0acb-128">les classes XML et [ADO.NET](../../../../docs/framework/data/adonet/index.md) sont étroitement intégrés afin de rassembler les données relationnelles et XML.</span><span class="sxs-lookup"><span data-stu-id="d0acb-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="d0acb-129">La classe <xref:System.Data.DataSet> est un cache en mémoire de données extraites d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="d0acb-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="d0acb-130">La classe <xref:System.Data.DataSet> a la capacité de lire et d'écrire du XML à l'aide des classes <xref:System.Xml.XmlReader> et <xref:System.Xml.XmlWriter>, de rendre persistante sa structure de schéma relationnel interne sous la forme de schémas XML (XSD) et de déduire la structure de schéma d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="d0acb-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0acb-131">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d0acb-131">In This Section</span></span>  
 [<span data-ttu-id="d0acb-132">Options de traitement XML</span><span class="sxs-lookup"><span data-stu-id="d0acb-132">XML Processing Options</span></span>](../../../../docs/standard/data/xml/xml-processing-options.md)  
 <span data-ttu-id="d0acb-133">Présente les options de traitement des données XML.</span><span class="sxs-lookup"><span data-stu-id="d0acb-133">Discusses options for processing XML data.</span></span>  
  
 [<span data-ttu-id="d0acb-134">Traitement de données XML en mémoire</span><span class="sxs-lookup"><span data-stu-id="d0acb-134">Processing XML Data In-Memory</span></span>](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md)  
 <span data-ttu-id="d0acb-135">Présente les trois modèles de traitement des données XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d0acb-135">Discusses the three models for processing XML data in-memory.</span></span> <span data-ttu-id="d0acb-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), la classe <xref:System.Xml.XmlDocument> (basée sur le DOM (Document Object Model) W3C) et la classe <xref:System.Xml.XPath.XPathDocument> (basée sur le modèle de données XPath).</span><span class="sxs-lookup"><span data-stu-id="d0acb-136">[LINQ to XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>  
  
 [<span data-ttu-id="d0acb-137">Transformations XSLT</span><span class="sxs-lookup"><span data-stu-id="d0acb-137">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 <span data-ttu-id="d0acb-138">Décrit comment utiliser le processeur XSLT.</span><span class="sxs-lookup"><span data-stu-id="d0acb-138">Describes how to use the XSLT processor.</span></span>  
  
 [<span data-ttu-id="d0acb-139">Modèle Objet du schéma (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="d0acb-139">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)  
 <span data-ttu-id="d0acb-140">Décrit les classes utilisées pour créer et manipuler des schémas XML (XSD) en fournissant une classe <xref:System.Xml.Schema.XmlSchema> pour le chargement et la modification d'un schéma.</span><span class="sxs-lookup"><span data-stu-id="d0acb-140">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>  
  
 [<span data-ttu-id="d0acb-141">Intégration de XML aux données relationnelles et à ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0acb-141">XML Integration with Relational Data and ADO.NET</span></span>](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)  
 <span data-ttu-id="d0acb-142">Décrit comment le .NET Framework permet un accès synchrone en temps réel aux représentations relationnelles et hiérarchiques des données via l'objet <xref:System.Data.DataSet> et l'objet <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="d0acb-142">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>  
  
 [<span data-ttu-id="d0acb-143">Gestion d’espaces de noms dans un document XML</span><span class="sxs-lookup"><span data-stu-id="d0acb-143">Managing Namespaces in an XML Document</span></span>](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)  
 <span data-ttu-id="d0acb-144">Décrit comment la classe <xref:System.Xml.XmlNamespaceManager> est utilisée pour stocker et gérer des informations d'espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d0acb-144">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>  
  
 [<span data-ttu-id="d0acb-145">Prise en charge du type dans les classes System.Xml</span><span class="sxs-lookup"><span data-stu-id="d0acb-145">Type Support in the System.Xml Classes</span></span>](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)  
 <span data-ttu-id="d0acb-146">Décrit comment les types de données XML sont mappés aux types CLR, comment convertir des types de données XML, ainsi que d'autres fonctionnalités de prise en charge des types dans les classes <xref:System.Xml>.</span><span class="sxs-lookup"><span data-stu-id="d0acb-146">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d0acb-147">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d0acb-147">Related Sections</span></span>  
 [<span data-ttu-id="d0acb-148">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0acb-148">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 <span data-ttu-id="d0acb-149">Présente des informations sur la manière d'accéder à des données à l'aide d'ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="d0acb-149">Provides information on how to access data using ADO.NET.</span></span>  
  
 [<span data-ttu-id="d0acb-150">Sécurité</span><span class="sxs-lookup"><span data-stu-id="d0acb-150">Security</span></span>](../../../../docs/standard/security/index.md)  
 <span data-ttu-id="d0acb-151">Offre une vue d'ensemble du système de sécurité .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0acb-151">Provides an overview of the .NET Framework security system.</span></span>  
  
 [<span data-ttu-id="d0acb-152">Centre de développement XML</span><span class="sxs-lookup"><span data-stu-id="d0acb-152">XML Developer Center</span></span>](http://go.microsoft.com/fwlink/?linkid=42458)  
 <span data-ttu-id="d0acb-153">Fournit des informations techniques supplémentaires, des fichiers à télécharger, des groupes de discussion et d'autres ressources utiles aux développeurs XML.</span><span class="sxs-lookup"><span data-stu-id="d0acb-153">Provides additional technical information, downloads, newsgroups, and other resources for XML developers.</span></span>
