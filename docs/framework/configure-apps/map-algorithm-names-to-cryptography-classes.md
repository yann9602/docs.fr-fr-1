---
title: "Mappage de noms d&#39;algorithmes &#224; des classes de chiffrement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "algorithmes de chiffrement"
  - "chiffrement, mapper des noms d'algorithmes"
  - "mapper des noms d'algorithmes"
  - "noms (.NET Framework), mapper des algorithmes"
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# Mappage de noms d&#39;algorithmes &#224; des classes de chiffrement
Un développeur dispose de quatre possibilités pour créer un objet de chiffrement à l'aide du [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] :  
  
-   création d'un objet à l'aide de l'opérateur **new**;  
  
-   création d'un objet qui implémente un algorithme de chiffrement particulier en appelant la méthode **Create** sur la classe abstraite pour cet algorithme ;  
  
-   création d'un objet qui implémente un algorithme de chiffrement particulier en appelant la méthode [System.Security.Cryptography.CryptoConfig.CreateFromName](frlrfSystemSecurityCryptographyCryptoConfigClassCreateFromNameTopic);  
  
-   création d'un objet qui implémente une classe d'algorithmes de chiffrement \(un chiffrement de blocs symétrique, par exemple\) en appelant la méthode **Create** sur la classe abstraite pour ce type d'algorithme \(comme <xref:System.Security.Cryptography.SymmetricAlgorithm>\).  
  
 Supposons par exemple qu'un développeur souhaite calculer le hachage SHA1 d'un jeu d'octets.  L'espace de noms <xref:System.Security.Cryptography> contient deux implémentations de l'algorithme SHA1, une implémentation managée de façon pure et une autre qui encapsule CryptoAPI.  Le développeur peut instancier une implémentation particulière de SHA1 \(la [classe SHA1Managed](frlrfSystemSecurityCryptographySHA1ManagedClassTopic)par exemple\) en appelant l'opérateur **new**.  Cependant, si la classe chargée par le Common Language Runtime n'a pas d'importance aussi longtemps qu'elle implémente l'algorithme de hachage SHA1, le développeur peut créer un objet en appelant la méthode [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic).  Cette méthode appelle **System.Security.Cryptography.CryptoConfig.CreateFromName\("System.Security.Cryptography.SHA1"\)**, qui doit retourner une implémentation de l'algorithme de hachage SHA1.  
  
 Le développeur peut également appeler **System.Security.Cryptography.CryptoConfig.CreateFromName\("SHA1"\)** puisque, par défaut, la configuration de chiffrement comprend des noms courts pour les algorithmes fournis par le .NET Framework.  
  
 Si l'algorithme de hachage utilisé n'a pas d'importance, le développeur peut appeler la méthode [System.Security.Cryptography.HashAlgorithm.Create](frlrfSystemSecurityCryptographyHashAlgorithmClassCreateTopic), qui retourne un objet implémentant une transformation de hachage.  
  
## Mappage de noms d'algorithmes dans des fichiers de configuration  
 Par défaut, le runtime retourne un objet [classe System.Security.Cryptography.SHA1CryptoServiceProvider](frlrfSystemSecurityCryptographySHA1CryptoServiceProviderClassTopic) pour les quatre scénarios.  Néanmoins, un administrateur d'ordinateur peut modifier le type d'objet retourné par les méthodes dans les deux derniers scénarios.  Pour cela, il faut mapper un nom d'algorithme convivial à la classe à utiliser dans le fichier de configuration machine \(Machine.config\).  
  
 L'exemple suivant illustre la configuration du runtime pour que les méthodes **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName\("SHA1"\)** et **System.Security.Cryptography.HashAlgorithm.Create** retournent un objet `MySHA1HashClass`.  
  
```  
<configuration>  
   <!-- Other configuration settings. -->  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MySHA1Hash="MySHA1HashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="SHA1" class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.SHA1"  
                       class="MySHA1Hash"/>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MySHA1Hash"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 Vous pouvez spécifier le nom de l'attribut dans l'élément [\<cryptoClass\>:](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) \(l'exemple précédent nomme l'attribut `MySHA1Hash`\).  La valeur de l'attribut dans l'élément **\<cryptoClass\>** est une chaîne que le Common Language Runtime utilise pour rechercher la classe.  Vous pouvez employer n'importe quelle chaîne répondant aux critères requis spécifiés dans [Spécification des noms de types qualifiés complets](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Plusieurs noms d'algorithmes peuvent être mappés à la même classe.  L'élément [\<nameEntry\> .](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mappe une classe à un seul nom d'algorithme convivial.  L'attribut **name** peut être soit une chaîne utilisée lors de l'appel à la méthode **System.Security.Cryptography.CryptoConfig.CreateFromName**, soit le nom d'une classe de chiffrement abstraite de l'espace de noms <xref:System.Security.Cryptography>.  La valeur de l'attribut **class** est le nom de l'attribut dans l'élément **\<cryptoClass\>**.  
  
> [!NOTE]
>  Vous pouvez obtenir un algorithme SHA1 en appelant la méthode [System.Security.Cryptography.SHA1.Create](frlrfSystemSecurityCryptographySHA1ClassCreateTopic) ou **Security.CryptoConfig.CreateFromName\("SHA1"\)**.  Chacune de ces méthodes garantit uniquement qu'elle retourne un objet implémentant l'algorithme SHA1.  Il n'est pas obligatoire de mapper à la même classe chaque nom convivial d'un algorithme donné dans le fichier de configuration.  
  
 Pour obtenir la liste des noms par défaut et des classes auxquelles ils sont mappés, consultez [CryptoConfig, classe](frlrfSystemSecurityCryptographyCryptoConfigClassTopic).  
  
## Voir aussi  
 [Services de chiffrement](../../../docs/standard/security/cryptographic-services.md)   
 [Configuration de classes de chiffrement](../../../docs/framework/configure-apps/configure-cryptography-classes.md)