---
title: "Sérialisation XML et SOAP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: 4
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 412468a03c15cedaa77a5e10be41793565039c4d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/21/2017

---
# <a name="xml-and-soap-serialization"></a>Sérialisation XML et SOAP
La sérialisation XML convertit (sérialise) les champs et les propriétés publics d'un objet ou les paramètres et valeurs de retour des méthodes, en un flux de données XML conforme à un document de langage XSD (XML Schema Definition) spécifique. La sérialisation XML permet d'obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format série (dans ce cas, XML) pour le stockage ou le transport.  
  
 XML étant une norme ouverte, le flux de données XML peut être traité si nécessaire par toute application, quelle que soit la plateforme. Par exemple, les services Web XML créés à l'aide d'ASP.NET utilisent la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML qui passent des données entre des applications de services Web XML sur Internet ou des intranets. Inversement, la désérialisation utilise le flux de données XML et reconstruit l'objet.  
  
 La sérialisation XML peut également être utilisée pour sérialiser des objets en flux XML se conformant à la spécification SOAP. SOAP est un protocole basé sur XML, conçu spécifiquement pour transporter des appels de procédure à l'aide de XML.  
  
 Pour sérialiser ou désérialiser des objets, utilisez la classe <xref:System.Xml.Serialization.XmlSerializer>. Pour créer les classes à sérialiser, utilisez l'outil XML Schema Definition.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 Fournit une définition générale de la sérialisation, en particulier de la sérialisation XML.  
  
 [Guide pratique pour sérialiser un objet](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 Fournit des instructions pas à pas pour sérialiser un objet.  
  
 [Guide pratique pour désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 Fournit des instructions pas à pas pour désérialiser un objet.  
  
 [Exemples de sérialisation XML](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 Fournit des exemples qui illustrent les points essentiels de la sérialisation XML.  
  
 [Outil XML Schema Definition et sérialisation XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 Décrit comment utiliser l'outil XML Schema Definition pour créer des classes qui respectent un schéma de langage XSD particulier ou pour générer un schéma XML à partir d'un fichier .dll.  
  
 [Contrôle de la sérialisation XML à l’aide d’attributs](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 Décrit comment contrôler la sérialisation à l'aide d'attributs.  
  
 [Attributs qui contrôlent la sérialisation XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 Répertorie les attributs utilisés pour contrôler la sérialisation XML.  
  
 [Guide pratique pour spécifier un nom d’élément différent pour un flux XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Présente un scénario avancé illustrant comment générer plusieurs flux de données XML en substituant la sérialisation.  
  
 [Guide pratique pour contrôler la sérialisation de classes dérivées](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 Fournit un exemple de procédure de contrôle de la sérialisation de classes dérivées.  
  
 [Guide pratique pour qualifier des noms d’éléments XML et des noms d’attributs XML](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Décrit comment définir et contrôler la manière dont les espaces de noms XML sont utilisés dans le flux de données XML.  
  
 [Sérialisation XML avec les services web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 Explique la manière dont la sérialisation XML est utilisée dans les services Web XML.  
  
 [Guide pratique pour sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Décrit comment utiliser la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML encodés selon le protocole SOAP et qui se conforment à la section 5 du document du World Wide Web Consortium (www.w3.org) intitulé « Simple Object Access Protocol (SOAP) 1.1 ».  
  
 [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Décrit le processus permettant de substituer la sérialisation XML d'objets sous forme de messages SOAP.  
  
 [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 Répertorie les attributs utilisés pour contrôler la sérialisation encodée selon le protocole SOAP.  
  
 [\<system.xml.serialization>, élément](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 Élément de configuration de niveau supérieur permettant de contrôler la sérialisation XML.  
  
 [\<dateTimeSerialization>, élément](../../../docs/standard/serialization/datetimeserialization-element.md)  
 Contrôle le mode de sérialisation d'objets <xref:System.DateTime>.  
  
 [\<schemaImporterExtensions>, élément](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 Contient des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
 [\<add>, élément pour \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Ajoute des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Technologies de développement avancées](http://msdn.microsoft.com/en-us/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Fournit des liens vers d'autres informations sur les tâches et les techniques de développement sophistiquées dans le .NET Framework.  
  
 [Création de services Web XML à l’aide de clients de service Web XML et ASP.NET](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML à l'aide d'ASP.NET.  
  
## <a name="see-also"></a>Voir aussi  
 [Sérialisation binaire](../../../docs/standard/serialization/binary-serialization.md)

