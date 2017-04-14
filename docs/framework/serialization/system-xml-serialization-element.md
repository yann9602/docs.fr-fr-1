---
title: "&#201;l&#233;ment &lt;system.xml.serialization&gt; | Microsoft Docs"
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
  - "élément <system.xml.serialization>"
  - "system.xml.serialization (élément)"
  - "sérialisation XML, configuration"
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &#201;l&#233;ment &lt;system.xml.serialization&gt;
Élément de niveau supérieur permettant de contrôler la sérialisation XML.  Pour plus d'informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## Syntaxe  
  
```  
  
<system.xml.serialization>  
</system.xml.serialization>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[Élément \<dateTimeSerialization\>](../../../docs/framework/serialization/datetimeserialization-element.md)|Détermine le mode de sérialisation des objets <xref:System.DateTime>.|  
|[Élément \<schemaImporterExtensions\>](../../../docs/framework/serialization/schemaimporterextensions-element.md)|Contient des types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<configuration\>, élément](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Élément racine dans chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Exemple  
 L'exemple de code suivant illustre comment spécifier le mode de sérialisation d'un objet <xref:System.DateTime> et l'ajout de types utilisés par le <xref:System.Xml.Serialization.XmlSchemaImporter> lors du mappage de types XSD en types .NET Framework.  
  
```  
<system.xml.serialization>  
    <xmlSerializer checkDeserializeAdvances="false" />  
    <dateTimeSerialization mode = "Local" />  
    <schemaImporterExtensions>  
        <add   
        name = "MobileCapabilities"   
        type = "System.Web.Mobile.MobileCapabilities,   
        System.Web.Mobile, Version - 2.0.0.0, Culture = neuutral,   
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.sxml.serialization>  
```  
  
## Voir aussi  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)   
 [Élément \<dateTimeSerialization\>](../../../docs/framework/serialization/datetimeserialization-element.md)   
 [Élément \<schemaImporterExtensions\>](../../../docs/framework/serialization/schemaimporterextensions-element.md)   
 [Élément \<add\> de \<xmlSchemaImporterExtensions\>](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)