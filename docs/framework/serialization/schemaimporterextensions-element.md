---
title: "&#201;l&#233;ment &lt;schemaImporterExtensions&gt; | Microsoft Docs"
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
  - "élément <schemaImporterExtensions>"
  - "schemaImporterExtensions (élément)"
  - "sérialisation XML, configuration"
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &#201;l&#233;ment &lt;schemaImporterExtensions&gt;
Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.  Pour plus d'informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## Syntaxe  
  
```  
  
<schemaImporterExtensions>  
    <!-- Add types -->  
</SchemaImporterExtension>  
```  
  
## Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément \<add\> de \<xmlSchemaImporterExtensions\>](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)|Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour créer des mappages.|  
  
## Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## Exemple  
 L'exemple de code suivant illustre comment ajouter des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.  
  
```  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =   
        "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
/system.sxml.serializaiton>  
```  
  
## Voir aussi  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)   
 [Élément \<dateTimeSerialization\>](../../../docs/framework/serialization/datetimeserialization-element.md)   
 [Élément \<add\> de \<xmlSchemaImporterExtensions\>](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)