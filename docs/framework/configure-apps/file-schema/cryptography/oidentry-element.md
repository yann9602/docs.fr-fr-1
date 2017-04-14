---
title: "&lt;oidEntry&gt;, &#233;l&#233;ment | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<oidEntry> (élément)"
  - "oidEntry (élément)"
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;oidEntry&gt;, &#233;l&#233;ment
Associe un OID \(Object IDentifier\) ASN.1 à un nom convivial.  
  
## Syntaxe  
  
```  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**OID**|Attribut requis.<br /><br /> Spécifie l'OID ASN.1 correspondant à l'algorithme implémenté par votre classe.|  
|**nom**|Attribut requis.<br /><br /> Spécifie la valeur de l'attribut **name** dans la balise [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`mscorlib`|Contient l'élément `cryptographySettings`.|  
|`oidMap`|Contient les mises en correspondance des OID \(Object IDentifier\) ASN.1 avec les classes.|  
  
## Notes  
 Les OID ASN.1 identifient les algorithmes dans certains formats de chiffrement.  Associez des OID aux noms conviviaux des algorithmes que vous souhaitez identifier.  Pour plus d'informations sur les OID, consultez MSDN Library.  
  
## Exemple  
 L'exemple montre comment utiliser l'élément **\<oidEntry\>** pour associer un OID pour l'algorithme de hachage RIPEMD\-160 à une implémentation de cet algorithme de hachage.  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## Voir aussi  
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Schéma des paramètres de chiffrement](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [Services de chiffrement](../../../../../docs/standard/security/cryptographic-services.md)   
 [Configuration de classes de chiffrement](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)   
 [Mappage d'identificateurs d'objet à des algorithmes de chiffrement](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)