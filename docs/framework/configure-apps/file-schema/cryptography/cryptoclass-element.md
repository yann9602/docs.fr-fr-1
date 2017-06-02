---
title: "&lt;cryptoClass&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses/cryptoClass"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClass"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptoClass> (élément)"
  - "cryptoClass (élément)"
ms.assetid: 03db52ef-010e-44ea-b6fd-b9c900ecad50
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;cryptoClass&gt;, &#233;l&#233;ment
Contient une classe de chiffrement associée à un nom convivial figurant dans l'élément [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).  
  
## Syntaxe  
  
```  
<cryptoClass customClassName="fully qualified type name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|`customClassName`|Attribut requis.<br /><br /> Contient les informations pour la classe de chiffrement.  Utilisez cet attribut pour fournir un nom court pour votre classe.  Vous devez spécifier une chaîne conforme aux exigences spécifiées dans [Spécification des noms de types qualifiés complets](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptoClasses`|Contient une liste des classes de chiffrement associées à un nom convivial figurant dans l'élément [\<nameEntry\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md).|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`cryptoNameMapping`|Contient les mises en correspondance des classes avec les noms conviviaux.|  
|`mscorlib`|Contient l'élément [\<cryptographySettings\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md).|  
  
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
 [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Schéma des paramètres de chiffrement](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)   
 [Services de chiffrement](../../../../../docs/standard/security/cryptographic-services.md)   
 [Configuration de classes de chiffrement](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)