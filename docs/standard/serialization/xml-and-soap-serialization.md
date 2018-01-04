---
title: "Sérialisation XML et SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 006727e70c58834a4e628f584a28302a62363844
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="xml-and-soap-serialization"></a><span data-ttu-id="9d928-102">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="9d928-102">XML and SOAP Serialization</span></span>
<span data-ttu-id="9d928-103">La sérialisation XML convertit (sérialise) les champs et les propriétés publics d'un objet ou les paramètres et valeurs de retour des méthodes, en un flux de données XML conforme à un document de langage XSD (XML Schema Definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="9d928-103">XML serialization converts (serializes) the public fields and properties of an object, or the parameters and return values of methods, into an XML stream that conforms to a specific XML Schema definition language (XSD) document.</span></span> <span data-ttu-id="9d928-104">La sérialisation XML permet d'obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format série (dans ce cas, XML) pour le stockage ou le transport.</span><span class="sxs-lookup"><span data-stu-id="9d928-104">XML serialization results in strongly typed classes with public properties and fields that are converted to a serial format (in this case, XML) for storage or transport.</span></span>  
  
 <span data-ttu-id="9d928-105">XML étant une norme ouverte, le flux de données XML peut être traité si nécessaire par toute application, quelle que soit la plateforme.</span><span class="sxs-lookup"><span data-stu-id="9d928-105">Because XML is an open standard, the XML stream can be processed by any application, as needed, regardless of platform.</span></span> <span data-ttu-id="9d928-106">Par exemple, les services Web XML créés à l'aide d'ASP.NET utilisent la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML qui passent des données entre des applications de services Web XML sur Internet ou des intranets.</span><span class="sxs-lookup"><span data-stu-id="9d928-106">For example, XML Web services created using ASP.NET use the <xref:System.Xml.Serialization.XmlSerializer> class to create XML streams that pass data between XML Web service applications throughout the Internet or on intranets.</span></span> <span data-ttu-id="9d928-107">Inversement, la désérialisation utilise le flux de données XML et reconstruit l'objet.</span><span class="sxs-lookup"><span data-stu-id="9d928-107">Conversely, deserialization takes such an XML stream and reconstructs the object.</span></span>  
  
 <span data-ttu-id="9d928-108">La sérialisation XML peut également être utilisée pour sérialiser des objets en flux XML se conformant à la spécification SOAP.</span><span class="sxs-lookup"><span data-stu-id="9d928-108">XML serialization can also be used to serialize objects into XML streams that conform to the SOAP specification.</span></span> <span data-ttu-id="9d928-109">SOAP est un protocole basé sur XML, conçu spécifiquement pour transporter des appels de procédure à l'aide de XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-109">SOAP is a protocol based on XML, designed specifically to transport procedure calls using XML.</span></span>  
  
 <span data-ttu-id="9d928-110">Pour sérialiser ou désérialiser des objets, utilisez la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9d928-110">To serialize or deserialize objects, use the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span> <span data-ttu-id="9d928-111">Pour créer les classes à sérialiser, utilisez l'outil XML Schema Definition.</span><span class="sxs-lookup"><span data-stu-id="9d928-111">To create the classes to be serialized, use the XML Schema Definition tool.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d928-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9d928-112">In This Section</span></span>  
 [<span data-ttu-id="9d928-113">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="9d928-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 <span data-ttu-id="9d928-114">Fournit une définition générale de la sérialisation, en particulier de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-114">Provides a general definition of serialization, particularly XML serialization.</span></span>  
  
 [<span data-ttu-id="9d928-115">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="9d928-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 <span data-ttu-id="9d928-116">Fournit des instructions pas à pas pour sérialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="9d928-116">Provides step-by-step instructions for serializing an object.</span></span>  
  
 [<span data-ttu-id="9d928-117">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="9d928-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 <span data-ttu-id="9d928-118">Fournit des instructions pas à pas pour désérialiser un objet.</span><span class="sxs-lookup"><span data-stu-id="9d928-118">Provides step-by-step instructions for deserializing an object.</span></span>  
  
 [<span data-ttu-id="9d928-119">Exemples de sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="9d928-119">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 <span data-ttu-id="9d928-120">Fournit des exemples qui illustrent les points essentiels de la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-120">Provides examples that demonstrate the basics of XML serialization.</span></span>  
  
 [<span data-ttu-id="9d928-121">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="9d928-121">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 <span data-ttu-id="9d928-122">Décrit comment utiliser l'outil XML Schema Definition pour créer des classes qui respectent un schéma de langage XSD particulier ou pour générer un schéma XML à partir d'un fichier .dll.</span><span class="sxs-lookup"><span data-stu-id="9d928-122">Describes how to use the XML Schema Definition tool to create classes that adhere to a particular XML Schema definition language (XSD) schema, or to generate an XML Schema from a .dll file.</span></span>  
  
 [<span data-ttu-id="9d928-123">Contrôle de la sérialisation XML à l’aide d’attributs</span><span class="sxs-lookup"><span data-stu-id="9d928-123">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 <span data-ttu-id="9d928-124">Décrit comment contrôler la sérialisation à l'aide d'attributs.</span><span class="sxs-lookup"><span data-stu-id="9d928-124">Describes how to control serialization by using attributes.</span></span>  
  
 [<span data-ttu-id="9d928-125">Attributs qui contrôlent la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="9d928-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 <span data-ttu-id="9d928-126">Répertorie les attributs utilisés pour contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-126">Lists the attributes that are used to control XML serialization.</span></span>  
  
 [<span data-ttu-id="9d928-127">Guide pratique pour spécifier un nom d’élément différent pour un flux XML</span><span class="sxs-lookup"><span data-stu-id="9d928-127">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 <span data-ttu-id="9d928-128">Présente un scénario avancé illustrant comment générer plusieurs flux de données XML en substituant la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="9d928-128">Presents an advanced scenario showing how to generate multiple XML streams by overriding the serialization.</span></span>  
  
 [<span data-ttu-id="9d928-129">Guide pratique pour contrôler la sérialisation de classes dérivées</span><span class="sxs-lookup"><span data-stu-id="9d928-129">How to: Control Serialization of Derived Classes</span></span>](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 <span data-ttu-id="9d928-130">Fournit un exemple de procédure de contrôle de la sérialisation de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9d928-130">Provides an example of how to control the serialization of derived classes.</span></span>  
  
 [<span data-ttu-id="9d928-131">Guide pratique pour qualifier des noms d’éléments XML et des noms d’attributs XML</span><span class="sxs-lookup"><span data-stu-id="9d928-131">How to: Qualify XML Element and XML Attribute Names</span></span>](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 <span data-ttu-id="9d928-132">Décrit comment définir et contrôler la manière dont les espaces de noms XML sont utilisés dans le flux de données XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-132">Describes how to define and control the way in which XML namespaces are used in the XML stream.</span></span>  
  
 [<span data-ttu-id="9d928-133">Sérialisation XML avec les services web XML</span><span class="sxs-lookup"><span data-stu-id="9d928-133">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 <span data-ttu-id="9d928-134">Explique la manière dont la sérialisation XML est utilisée dans les services Web XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-134">Explains how XML serialization is used in XML Web services.</span></span>  
  
 [<span data-ttu-id="9d928-135">Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="9d928-135">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <span data-ttu-id="9d928-136">Décrit comment utiliser la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML encodés selon le protocole SOAP et qui se conforment à la section 5 du document du World Wide Web Consortium (www.w3.org) intitulé « Simple Object Access Protocol (SOAP) 1.1 ».</span><span class="sxs-lookup"><span data-stu-id="9d928-136">Describes how to use the <xref:System.Xml.Serialization.XmlSerializer> class to create encoded SOAP XML streams that conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1."</span></span>  
  
 [<span data-ttu-id="9d928-137">Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="9d928-137">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 <span data-ttu-id="9d928-138">Décrit le processus permettant de substituer la sérialisation XML d'objets sous forme de messages SOAP.</span><span class="sxs-lookup"><span data-stu-id="9d928-138">Describes the process for overriding XML serialization of objects as SOAP messages.</span></span>  
  
 [<span data-ttu-id="9d928-139">Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="9d928-139">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 <span data-ttu-id="9d928-140">Répertorie les attributs utilisés pour contrôler la sérialisation encodée selon le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="9d928-140">Lists the attributes that are used to control SOAP-encoded serialization.</span></span>  
  
 [<span data-ttu-id="9d928-141">\<system.xml.serialization>, élément</span><span class="sxs-lookup"><span data-stu-id="9d928-141">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 <span data-ttu-id="9d928-142">Élément de configuration de niveau supérieur permettant de contrôler la sérialisation XML.</span><span class="sxs-lookup"><span data-stu-id="9d928-142">The top-level configuration element for controlling XML serialization.</span></span>  
  
 [<span data-ttu-id="9d928-143">\<dateTimeSerialization>, élément</span><span class="sxs-lookup"><span data-stu-id="9d928-143">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <span data-ttu-id="9d928-144">Contrôle le mode de sérialisation d'objets <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9d928-144">Controls the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 [<span data-ttu-id="9d928-145">\<schemaImporterExtensions>, élément</span><span class="sxs-lookup"><span data-stu-id="9d928-145">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <span data-ttu-id="9d928-146">Contient des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="9d928-146">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
 [<span data-ttu-id="9d928-147">\<add>, élément pour \<xmlSchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="9d928-147">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <span data-ttu-id="9d928-148">Ajoute des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="9d928-148">Adds types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9d928-149">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9d928-149">Related Sections</span></span>  
 [<span data-ttu-id="9d928-150">Technologies de développement avancées</span><span class="sxs-lookup"><span data-stu-id="9d928-150">Advanced Development Technologies</span></span>](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 <span data-ttu-id="9d928-151">Fournit des liens vers d'autres informations sur les tâches et les techniques de développement sophistiquées dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9d928-151">Provides links to more information on sophisticated development tasks and techniques in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="9d928-152">Création de services Web XML à l’aide de clients de service Web XML et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9d928-152">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 <span data-ttu-id="9d928-153">Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML à l'aide d'ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9d928-153">Provides topics that describe and explain how to program XML Web services using ASP.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d928-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d928-154">See Also</span></span>  
 [<span data-ttu-id="9d928-155">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="9d928-155">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
