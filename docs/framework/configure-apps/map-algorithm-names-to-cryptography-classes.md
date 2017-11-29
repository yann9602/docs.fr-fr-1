---
title: "Mappage de noms d'algorithmes à des classes de chiffrement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping algorithm names
- cryptography, mapping algorithm names
- cryptographic algorithms
- names [.NET Framework], algorithm mapping
ms.assetid: 01327c69-c5e1-4ef6-b73f-0a58351f0492
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e59b2551545b8b70bcb54a5d43d041c44579b786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="mapping-algorithm-names-to-cryptography-classes"></a>Mappage de noms d'algorithmes à des classes de chiffrement
Il existe quatre méthodes, un développeur peut créer un objet de chiffrement à l’aide de la [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]:  
  
-   Créer un objet à l’aide de la **nouveau** opérateur.  
  
-   Créer un objet qui implémente un algorithme de chiffrement particulier en appelant le **créer** méthode sur la classe abstraite pour cet algorithme.  
  
-   Créer un objet qui implémente un algorithme de chiffrement particulier en appelant le <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> (méthode).  
  
-   Créer un objet qui implémente une classe d’algorithmes de chiffrement (par exemple, un chiffrement symétrique) en appelant le **créer** méthode sur la classe abstraite pour ce type d’algorithme (tel que <xref:System.Security.Cryptography.SymmetricAlgorithm>).  
  
 Par exemple, qu'un développeur souhaite calculer le hachage SHA1 d’un jeu d’octets. Le <xref:System.Security.Cryptography> espace de noms contient deux implémentations de l’algorithme SHA1, une implémentation managée de purement et une autre qui encapsule CryptoAPI. Le développeur peut choisir d’instancier une implémentation particulière de SHA1 (telles que la <xref:System.Security.Cryptography.SHA1Managed>) en appelant le **nouveau** opérateur. Toutefois, si elle n’a pas d’importance le common language runtime charge tant que la classe implémente l’algorithme de hachage SHA1, le développeur peut créer un objet en appelant le <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> (méthode). Cette méthode appelle **System.Security.Cryptography.CryptoConfig.CreateFromName("System.Security.Cryptography.SHA1")**, qui doit retourner une implémentation de l’algorithme de hachage SHA1.  
  
 Le développeur peut également appeler **System.Security.Cryptography.CryptoConfig.CreateFromName("SHA1")** car, par défaut, la configuration de chiffrement comprend des noms courts pour les algorithmes fournis dans le .NET Framework.  
  
 Si l’algorithme de hachage est utilisé n’a pas d’importance, le développeur peut appeler le <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> (méthode), qui retourne un objet qui implémente une transformation de hachage.  
  
## <a name="mapping-algorithm-names-in-configuration-files"></a>Mappage des noms d’algorithmes dans les fichiers de Configuration  
 Par défaut, le runtime retourne un <xref:System.Security.Cryptography.SHA1CryptoServiceProvider> objet pour les quatre scénarios. Toutefois, un administrateur d’ordinateur permettre modifier le type d’objet renvoyées par les méthodes dans les deux derniers scénarios. Pour ce faire, vous devez mapper un nom d’algorithme convivial à la classe que vous souhaitez utiliser dans le fichier de configuration de l’ordinateur (Machine.config).  
  
 L’exemple suivant montre comment configurer le runtime de sorte que **System.Security.Cryptography.SHA1.Create**, **System.Security.CryptoConfig.CreateFromName("SHA1")**, et  **System.Security.Cryptography.HashAlgorithm.Create** renvoyer un `MySHA1HashClass` objet.  
  
```xml  
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
  
 Vous pouvez spécifier le nom de l’attribut dans le [< cryptoClass\> élément](../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) (l’exemple précédent nomme l’attribut `MySHA1Hash`). La valeur de l’attribut dans le  **\<cryptoClass >** élément est une chaîne que le common language runtime utilise pour rechercher la classe. Vous pouvez utiliser n’importe quelle chaîne qui répond aux exigences spécifiées dans [en spécifiant des noms de types qualifiés complets](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).  
  
 Plusieurs noms d’algorithmes peuvent mapper à la même classe. Le [ \<nameEntry > élément](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) mappe une classe à un nom d’algorithme convivial. Le **nom** attribut peut être soit une chaîne qui est utilisée lors de l’appel du **System.Security.Cryptography.CryptoConfig.CreateFromName** méthode ou le nom d’une classe de chiffrement abstraite dans le <xref:System.Security.Cryptography> espace de noms. La valeur de la **classe** attribut est le nom de l’attribut dans le  **\<cryptoClass >** élément.  
  
> [!NOTE]
>  Vous pouvez obtenir un algorithme SHA1 en appelant le <xref:System.Security.Cryptography.SHA1.Create%2A?displayProperty=nameWithType> ou **Security.CryptoConfig.CreateFromName("SHA1")** (méthode). Chaque méthode garantit uniquement qu’il retourne un objet qui implémente l’algorithme SHA1. Vous n’avez pas à mapper chaque nom convivial d’un algorithme à la même classe dans le fichier de configuration.  
  
 Pour obtenir la liste de noms par défaut et les classes de mappage, consultez <xref:System.Security.Cryptography.CryptoConfig>.  
  
## <a name="see-also"></a>Voir aussi  
 [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)  
 [Configuration des classes de chiffrement](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
