---
title: "&#201;l&#233;ment &lt;add&gt; de &lt;xmlSchemaImporterExtensions&gt; | Microsoft Docs"
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
  - "élément <add> de <xmlSchemaImporterExtensions>"
  - "sérialisation XML, configuration"
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &#201;l&#233;ment &lt;add&gt; de &lt;xmlSchemaImporterExtensions&gt;
Ajoute des types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter> pour mapper des types XSD en types .NET Framework.  Pour plus d'informations sur les fichiers de configuration, consultez [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<XmlSchemaImporterExtensions\>  
\<add\>  
  
## Syntaxe  
  
```  
  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**name**|Nom simple utilisé pour rechercher l'instance.|  
|**type**|Requis.  Spécifie la classe d'extension de schéma à ajouter.  La valeur d'attribut **type** doit figurer sur une ligne et inclure le nom de type qualifié complet.  Lorsque l'assembly est placé dans le Global Assembly Cache \(GAC\), il doit également inclure la version, la culture et le jeton de clé publique de l'assembly signé.|  
  
### Éléments enfants  
 Aucun  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|\<xmlSchemaImporterExtensions\>|Contient les types utilisés par <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## Exemple  
 L'exemple de code suivant ajoute un type d'extension que XmlSchemaImporter peut utiliser lors du mappage de types.  
  
```  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Xml.Serialization.XmlSchemaImporter>   
 [Élément \<system.xml.serialization\>](../../../docs/framework/serialization/system-xml-serialization-element.md)   
 [Élément \<schemaImporterExtensions\>](../../../docs/framework/serialization/schemaimporterextensions-element.md)