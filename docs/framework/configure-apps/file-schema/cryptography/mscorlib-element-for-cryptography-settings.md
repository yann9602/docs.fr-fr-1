---
title: "&lt;mscorlib&gt;, &#233;l&#233;ment pour les param&#232;tres de chiffrement | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<mscorlib> (élément)"
  - "mscorlib (élément)"
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;mscorlib&gt;, &#233;l&#233;ment pour les param&#232;tres de chiffrement
Contient l'élément [\<cryptographySettings\>.](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).  
  
## Syntaxe  
  
```  
  
      <mscorlib>   
</mscorlib>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'élément **\<mscorlib\>** pour référencer une classe de chiffrement et configurer le runtime.  Vous pouvez ensuite passer la chaîne "RSA" à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.  
  
```  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## Voir aussi  
 <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>   
 <xref:System.Security.Cryptography>   
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Schéma des paramètres de chiffrement](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [Services de chiffrement](../../../../../docs/standard/security/cryptographic-services.md)   
 [Configuration de classes de chiffrement](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)