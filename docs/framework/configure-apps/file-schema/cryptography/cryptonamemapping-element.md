---
title: "&lt;cryptoNameMapping&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<cryptoNameMapping> (élément)"
  - "cryptoNameMapping (élément)"
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
caps.latest.revision: 12
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 12
---
# &lt;cryptoNameMapping&gt;, &#233;l&#233;ment
Contient les mises en correspondance des classes avec les noms conviviaux.  
  
## Syntaxe  
  
```  
  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
 Aucun.  
  
### Éléments enfants  
  
|Élément|Description|  
|-------------|-----------------|  
|`cryptoClasses`|Contient une liste des classes de chiffrement associées à un nom convivial figurant dans l'élément **\<nameEntry\>**.|  
|`nameEntry`|Associe un nom de classe à un nom d'algorithme convivial, ce qui permet à une seule classe d'avoir plusieurs noms conviviaux.|  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`cryptographySettings`|Contient des paramètres de chiffrement.|  
|`cryptoNameMapping`|Contient les mises en correspondance des classes avec les noms conviviaux.|  
|`mscorlib`|Contient l'élément \<cryptographySettings\> .|  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'élément **\<cryptoNameMapping\>** pour référencer une classe de chiffrement et configurer le runtime.  Vous pouvez ensuite passer la chaîne "RSA" à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.  
  
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