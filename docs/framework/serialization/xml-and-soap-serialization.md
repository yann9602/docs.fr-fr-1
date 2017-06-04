---
title: "S&#233;rialisation&#160;XML et&#160;SOAP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "sérialisation"
  - "sérialisation, à propos de la sérialisation"
  - "sérialisation, SOAP"
  - "SOAP, sérialisation XML"
  - "sérialisation XML"
  - "sérialisation XML, SOAP"
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# S&#233;rialisation&#160;XML et&#160;SOAP
La sérialisation XML convertit \(sérialise\) les champs et les propriétés publics d'un objet ou les paramètres et valeurs de retour des méthodes, en un flux de données XML conforme à un document de langage XSD \(XML Schema Definition\) spécifique.La sérialisation XML permet d'obtenir des classes fortement typées avec des propriétés et des champs publics convertis au format série \(dans ce cas, XML\) pour le stockage ou le transport.  
  
 XML étant une norme ouverte, le flux de données XML peut être traité si nécessaire par toute application, quelle que soit la plateforme.Par exemple, les services Web XML créés à l'aide d'ASP.NET utilisent la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML qui passent des données entre des applications de services Web XML sur Internet ou des intranets.Inversement, la désérialisation utilise le flux de données XML et reconstruit l'objet.  
  
 La sérialisation XML peut également être utilisée pour sérialiser des objets en flux XML se conformant à la spécification SOAP.SOAP est un protocole basé sur XML, conçu spécifiquement pour transporter des appels de procédure à l'aide de XML.  
  
 Pour sérialiser ou désérialiser des objets, utilisez la classe <xref:System.Xml.Serialization.XmlSerializer>.Pour créer les classes à sérialiser, utilisez l'outil XML Schema Definition.  
  
## Dans cette section  
 [Introduction à la sérialisation XML](../../../docs/framework/serialization/introducing-xml-serialization.md)  
 Fournit une définition générale de la sérialisation, en particulier de la sérialisation XML.  
  
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)  
 Fournit des instructions pas à pas pour sérialiser un objet.  
  
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)  
 Fournit des instructions pas à pas pour désérialiser un objet.  
  
 [Exemples de sérialisation XML](../../../docs/framework/serialization/examples-of-xml-serialization.md)  
 Fournit des exemples qui illustrent les points essentiels de la sérialisation XML.  
  
 [Outil XML Schema Definition et sérialisation XML](../../../docs/framework/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 Décrit comment utiliser l'outil XML Schema Definition pour créer des classes qui respectent un schéma de langage XSD particulier ou pour générer un schéma XML à partir d'un fichier .dll.  
  
 [Contrôle de la sérialisation XML à l'aide d'attributs](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)  
 Décrit comment contrôler la sérialisation à l'aide d'attributs.  
  
 [Attributs qui contrôlent la sérialisation XML](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)  
 Répertorie les attributs utilisés pour contrôler la sérialisation XML.  
  
 [Comment : spécifier un nom d'élément différent pour un flux XML](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 Présente un scénario avancé illustrant comment générer plusieurs flux de données XML en substituant la sérialisation.  
  
 [Comment : contrôler la sérialisation de classes dérivées](../../../docs/framework/serialization/how-to-control-serialization-of-derived-classes.md)  
 Fournit un exemple de procédure de contrôle de la sérialisation de classes dérivées.  
  
 [Comment : qualifier des noms d'éléments XML et des noms d'attributs XML](../../../docs/framework/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 Décrit comment définir et contrôler la manière dont les espaces de noms XML sont utilisés dans le flux de données XML.  
  
 [Sérialisation XML avec les services Web XML](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)  
 Explique la manière dont la sérialisation XML est utilisée dans les services Web XML.  
  
 [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 Décrit comment utiliser la classe <xref:System.Xml.Serialization.XmlSerializer> pour créer des flux de données XML encodés selon le protocole SOAP et qui se conforment à la section 5 du document du World Wide Web Consortium \(www.w3.org\) intitulé « Simple Object Access Protocol \(SOAP\) 1.1 ».  
  
 [Comment : substituer la sérialisation XML encodée selon le protocole SOAP](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 Décrit le processus permettant de substituer la sérialisation XML d'objets sous forme de messages SOAP.  
  
 [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)  
 Répertorie les attributs utilisés pour contrôler la sérialisation encodée selon le protocole SOAP.  
  
 [Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)  
 Élément de configuration de niveau supérieur permettant de contrôler la sérialisation XML.  
  
 [Élément \<dateTimeSerialization\>](../../../docs/framework/serialization/datetimeserialization-element.md)  
 Contrôle le mode de sérialisation d'objets <xref:System.DateTime>.  
  
 [Élément \<schemaImporterExtensions\>](../../../docs/framework/serialization/schemaimporterextensions-element.md)  
 Contient des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
 [Élément \<add\> de \<xmlSchemaImporterExtensions\>](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)  
 Ajoute des types utilisés par la classe <xref:System.Xml.Serialization.XmlSchemaImporter>.  
  
## Rubriques connexes  
 [Advanced Development Technologies](http://msdn.microsoft.com/fr-fr/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 Fournit des liens vers d'autres informations sur les tâches et les techniques de développement sophistiquées dans le .NET Framework.  
  
 [XML Web Services Created Using ASP.NET and XML Web Service Clients](http://msdn.microsoft.com/fr-fr/1e64af78-d705-4384-b08d-591a45f4379c)  
 Fournit des rubriques qui décrivent et expliquent comment programmer des services Web XML à l'aide d'ASP.NET.  
  
## Voir aussi  
 [Sérialisation binaire](../../../docs/framework/serialization/binary-serialization.md)