---
title: "&#201;l&#233;ment &lt;dateTimeSerialization&gt; | Microsoft Docs"
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
  - "élément <dateTimeSerialization>"
  - "élément dateTimeSerialization"
  - "sérialisation XML, configuration"
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# &#201;l&#233;ment &lt;dateTimeSerialization&gt;
Détermine le mode de sérialisation des objets <xref:System.DateTime>.  
  
## Syntaxe  
  
```  
  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attributs|Description|  
|---------------|-----------------|  
|`mode`|Facultatif.  Spécifie le mode de sérialisation.  Affectez\-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>.  La valeur par défaut est **RoundTrip**.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|system.xml.serialization|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## Notes  
 Dans les versions 1.0, 1.1, 2.0 et ultérieures du .NET Framework, lorsque cette propriété a la valeur **Local**, les objets <xref:System.DateTime> sont toujours mis en forme avec l'heure locale.  Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées.  Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.  
  
 Dans les versions 2.0 et ultérieures du .NET Framework dont la propriété a la valeur **Roundtrip**, les objets <xref:System.DateTime> sont examinés pour déterminer s'ils se trouvent dans le fuseau horaire local ou UTC, ou encore dans un fuseau horaire non spécifié.  Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées.  Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.  
  
## Voir aussi  
 <xref:System.DateTime>   
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>   
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)   
 [Élément \<schemaImporterExtensions\>](../../../docs/framework/serialization/schemaimporterextensions-element.md)   
 [Élément \<add\> de \<xmlSchemaImporterExtensions\>](../../../docs/framework/serialization/add-element-for-xmlschemaimporterextensions.md)   
 [Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)