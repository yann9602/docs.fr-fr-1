---
title: "&lt;nameEntry&gt;, &#233;l&#233;ment | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<nameEntry> (élément)"
  - "nameEntry (élément)"
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;nameEntry&gt;, &#233;l&#233;ment
Associe un nom de classe à un nom d'algorithme convivial, ce qui permet à une seule classe d'avoir plusieurs noms conviviaux.  
  
## Syntaxe  
  
```  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### Attributs  
  
|Attribut|Description|  
|--------------|-----------------|  
|**nom**|Attribut requis.<br /><br /> Spécifie le nom convivial de l'algorithme que la classe de chiffrement implémente.|  
|**class**|Attribut requis.<br /><br /> Spécifie la valeur de l'attribut **name** dans l'élément [\<cryptoClass\>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md).|  
  
### Éléments enfants  
 Aucun.  
  
### Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`system.web`|Spécifie l'élément racine de la section de configuration ASP.NET.|  
  
## Notes  
 L'attribut **name** peut être le nom de l'une des classes abstraites trouvées dans l'espace de noms <xref:System.Security.Cryptography>.  Lorsque vous appelez la méthode **Create** sur une classe de chiffrement abstraite, le nom de la classe abstraite est passé à la méthode [Security.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic).  **CreateFromName** retourne une instance du type indiqué par l'attribut **class**.  Si l'attribut **name** est un nom court, tel que RSA, vous pouvez utiliser ce nom lors de l'appel de la méthode **CreateFromName**.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation de l'élément **\<nameEntry\>** pour référencer une classe de chiffrement et configurer le runtime.  Vous pouvez ensuite passer la chaîne "RSA" à la méthode <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=fullName> et utiliser la méthode <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> pour retourner un objet `MyCryptoRSAClass`.  
  
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