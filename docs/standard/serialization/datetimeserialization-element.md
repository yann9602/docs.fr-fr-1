---
title: "Élément &lt;dateTimeSerialization&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd6dda1f26e44c4864d5afea1427b2580ac1ed10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdatetimeserializationgt-element"></a>Élément &lt;dateTimeSerialization&gt;
Détermine le mode de sérialisation des objets <xref:System.DateTime>.  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attributs|Description|  
|----------------|-----------------|  
|`mode`|Facultatif. Spécifie le mode de sérialisation. Affectez-le à l'une des valeurs <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>. La valeur par défaut est **RoundTrip**.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|system.xml.serialization|Élément de niveau supérieur permettant de contrôler la sérialisation XML.|  
  
## <a name="remarks"></a>Remarques  
 Dans les versions 1.0, 1.1, 2.0 et ultérieures du .NET Framework, quand cette propriété a la valeur **Local**, les objets <xref:System.DateTime> sont toujours mis en forme avec l’heure locale. Autrement dit, les informations du fuseau horaire local sont toujours incluses avec les données sérialisées. Affectez la valeur **Local** à cette propriété pour garantir la compatibilité avec les versions antérieures du .NET Framework.  
  
 Dans les versions 2.0 et ultérieures du .NET Framework dont la propriété a la valeur **Roundtrip**, les objets <xref:System.DateTime> sont examinés pour déterminer s’ils se trouvent dans le fuseau horaire local ou UTC, ou encore dans un fuseau horaire non spécifié. Les objets <xref:System.DateTime> sont ensuite sérialisés de manière à ce que ces informations soient conservées. Il s'agit du comportement par défaut, recommandé pour toutes les nouvelles applications qui ne communiquent pas avec les versions antérieures du .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<schemaImporterExtensions>, élément](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [\<add>, élément pour \<xmlSchemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [\<system.xml.serialization>, élément](../../../docs/standard/serialization/system-xml-serialization-element.md)
