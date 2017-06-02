---
title: "Attributs qui contr&#244;lent la s&#233;rialisation encod&#233;e selon le protocole&#160;SOAP | Microsoft Docs"
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
  - "attributs (.NET Framework), sérialisation XML"
  - "sérialisation, attributs"
  - "SOAP, sérialisation XML"
  - "sérialisation XML, attributs"
  - "sérialisation XML, SOAP"
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Attributs qui contr&#244;lent la s&#233;rialisation encod&#233;e selon le protocole&#160;SOAP
Le document World Wide Web Consortium \(www.w3.org\) intitulé « Simple Object Access Protocol \(SOAP\) 1.1 » contient une section facultative \(section 5\) qui décrit la manière dont les paramètres SOAP peuvent être encodés.Pour se conformer à la section 5 de la spécification, vous devez utiliser un ensemble spécial d'attributs se trouvant dans l'espace de noms [System.Xml.Serialization](frlrfSystemXmlSerialization).Appliquez ces attributs en fonction des classes et membres de classes, puis utilisez [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) pour sérialiser les instances de la ou des classes.  
  
 Le tableau suivant affiche les attributs, leurs conditions d'application et l'action qu'ils entraînent.Pour plus d'informations sur l'utilisation de ces attributs pour contrôler la sérialisation XML, consultez [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md) et [Comment : substituer la sérialisation XML encodée selon le protocole SOAP](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md).  
  
 Pour plus d'informations sur les attributs, consultez [Attributs](../../../docs/standard/attributes/index.md).  
  
|Attribut|S'applique à|Informations fournies|  
|--------------|------------------|---------------------------|  
|[SoapAttributeAttribute](frlrfSystemXmlSerializationSoapAttributeAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour.|Le membre de classe est sérialisé en tant qu'attribut XML.|  
|[SoapElementAttribute](frlrfSystemXmlSerializationSoapElementAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour.|La classe est sérialisée en tant qu'élément XML.|  
|[SoapEnumAttribute](frlrfSystemXmlSerializationSoapEnumAttributeClassTopic)|Champ public qui est un identificateur d'énumération.|Nom d'élément d'un membre d'énumération.|  
|[SoapIgnoreAttribute](frlrfSystemXmlSerializationSoapIgnoreAttributeClassTopic)|Champs et propriétés publics.|La propriété ou le champ doit être ignoré lorsque la classe conteneur est sérialisée.|  
|[SoapIncludeAttribute](frlrfSystemXmlSerializationSoapIncludeAttributeClassTopic)|Déclarations de classe dérivée publiques et méthodes publiques pour les documents WSDL \(Web Services Description Language\).|Le type doit être inclus lors de la génération de schémas \(afin d'être reconnu en cas de sérialisation\).|  
|[SoapTypeAttribute](frlrfSystemXmlSerializationSoapTypeAttributeClassTopic)|Déclarations de classe publiques.|La classe doit être sérialisée en tant que type XML.|  
  
## Voir aussi  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [Comment : substituer la sérialisation XML encodée selon le protocole SOAP](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [Attributs](../../../docs/standard/attributes/index.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)