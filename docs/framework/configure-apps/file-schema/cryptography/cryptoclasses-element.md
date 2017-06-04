---
title: "&lt;cryptoClasses&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptoClasses> (élément)"
  - "cryptoClasses (élément)"
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
caps.latest.revision: 16
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# &lt;cryptoClasses&gt;, &#233;l&#233;ment
Contient une liste des classes de chiffrement associées à un nom convivial figurant dans l'élément [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).  
  
## Syntaxe  
  
```  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Contient une classe de chiffrement associée à un nom convivial figurant dans l'élément **\<nameEntry\>**.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`cryptoNameMapping`|Contient les mises en correspondance des classes avec les noms conviviaux.|  
|`mscorlib`|Contient l'élément `cryptographySettings`.|  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'élément **\<cryptoClass\>** pour référencer une classe de chiffrement et configurer le runtime.  Vous pouvez ensuite passer la chaîne "RSA" à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Security.Cryptography>   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Schéma des paramètres de chiffrement](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [Services de chiffrement](../../../../../docs/standard/security/cryptographic-services.md)   
 [System.Security.Cryptography.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic)   
 [Configuration de classes de chiffrement](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)