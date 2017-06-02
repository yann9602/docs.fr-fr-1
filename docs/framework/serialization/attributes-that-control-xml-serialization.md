---
title: "Attributs qui contr&#244;lent la s&#233;rialisation&#160;XML | Microsoft Docs"
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
  - "classes, sérialiser"
  - "sérialisation, attributs"
  - "schéma XML, sérialiser"
  - "sérialisation XML, attributs"
  - "XmlSerializer (classe), sérialiser"
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Attributs qui contr&#244;lent la s&#233;rialisation&#160;XML
Vous pouvez appliquer les attributs du tableau suivant à des classes et des membres de classe pour contrôler la manière dont [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) sérialise ou désérialise une instance de la classe.Pour comprendre comment ces attributs contrôlent la sérialisation XML, consultez [Contrôle de la sérialisation XML à l'aide d'attributs](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md).  
  
 Ces attributs peuvent également être utilisés pour contrôler les messages SOAP de style littéral générés par un service Web XML.Pour plus d'informations sur l'application de ces attributs à une méthode de services Web XML, consultez [Sérialisation XML avec les services Web XML](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md).  
  
 Pour plus d'informations sur les attributs, consultez [Attributs](../../../docs/standard/attributes/index.md).  
  
|Attribut|S'applique à|Informations fournies|  
|--------------|------------------|---------------------------|  
|[XmlAnyAttributeAttribute](frlrfSystemXmlSerializationXmlAnyAttributeAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets [XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic).|Lors de la désérialisation, le tableau est rempli avec les objets [XmlAttribute](frlrfSystemXmlXmlAttributeClassTopic) qui représentent tous les attributs XML inconnus du schéma.|  
|[XmlAnyElementAttribute](frlrfSystemXmlSerializationXmlAnyElementAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets [XmlElement](frlrfSystemXmlXmlElementClassTopic).|Lors de la désérialisation, le tableau est rempli avec les objets [XmlElement](frlrfSystemXmlXmlElementClassTopic) qui représentent tous les éléments XML inconnus du schéma.|  
|[XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets complexes.|Les membres du tableau sont générés en tant que membres d'un tableau XML.|  
|[XmlArrayItemAttribute](frlrfSystemXmlSerializationXmlArrayItemAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour qui retourne un tableau d'objets complexes.|Types dérivés qui peuvent être insérés dans un tableau.S'applique habituellement avec [XmlArrayAttribute](frlrfSystemXmlSerializationXmlArrayAttributeClassTopic).|  
|[XmlAttributeAttribute](frlrfSystemXmlSerializationXmlAttributeAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour.|Le membre est sérialisé en tant qu'attribut XML.|  
|[XmlChoiceIdentifierAttribute](frlrfSystemXmlSerializationXmlChoiceIdentifierAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour.|L'ambiguïté du membre peut être levée à l'aide d'une énumération.|  
|[XmlElementAttribute](frlrfSystemXmlSerializationXmlElementAttributeClassTopic)|Champ public, propriété, paramètre ou valeur de retour.|Le champ ou la propriété est sérialisé en tant qu'élément XML.|  
|[XmlEnumAttribute](frlrfSystemXmlSerializationXmlEnumAttributeClassTopic)|Champ public qui est un identificateur d'énumération.|Nom d'élément d'un membre d'énumération.|  
|[XmlIgnoreAttribute](frlrfSystemXmlSerializationXmlIgnoreAttributeClassTopic)|Champs et propriétés publics.|La propriété ou le champ doit être ignoré lorsque la classe conteneur est sérialisée.|  
|[XmlIncludeAttribute](frlrfSystemXmlSerializationXmlIncludeAttributeClassTopic)|Déclarations de classe dérivée publiques et valeurs de retour de méthodes publiques pour les documents WSDL \(Web Services Description Language\).|La classe doit être incluse lors de la génération de schémas \(afin d'être reconnue en cas de sérialisation\).|  
|[XmlRootAttribute](frlrfSystemXmlSerializationXmlRootAttributeClassTopic)|Déclarations de classe publiques.|Contrôle la sérialisation XML de l'attribut cible en tant qu'élément racine XML.Utilisez l'attribut pour préciser l'espace de noms et le nom d'élément.|  
|[XmlTextAttribute](frlrfSystemXmlSerializationXmlTextAttributeClassTopic)|Champs et propriétés publics.|La propriété ou le champ doit être sérialisé en tant que texte XML.|  
|[XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic)|Déclarations de classe publiques.|Nom et espace de noms du type XML.|  
  
 En plus de ces attributs, qui se trouvent tous dans l'espace de noms [System.Xml.Serialization](frlrfSystemxmlserialization), vous pouvez également appliquer l'attribut [System.ComponentModel.DefaultValueAttribute](frlrfSystemComponentModelDefaultValueAttributeClassTopic) à un champ.**DefaultValueAttribute** définit la valeur qui sera assignée automatiquement au membre si aucune valeur n'est spécifiée.  
  
 Pour contrôler la sérialisation XML codée selon le protocole SOAP, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md).  
  
## Voir aussi  
 [Sérialisation XML et SOAP](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx)   
 [Contrôle de la sérialisation XML à l'aide d'attributs](../../../docs/framework/serialization/controlling-xml-serialization-using-attributes.md)   
 [Comment : spécifier un nom d'élément différent pour un flux XML](../../../docs/framework/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)   
 [Comment : sérialiser un objet](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [Comment : désérialiser un objet](../../../docs/framework/serialization/how-to-deserialize-an-object.md)