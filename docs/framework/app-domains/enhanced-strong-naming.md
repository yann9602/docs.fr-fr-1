---
title: "Amélioration de l'utilisation de noms forts"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429a54340cef6d608692abd71311c012afe9a3d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="enhanced-strong-naming"></a>Amélioration de l'utilisation de noms forts
Une signature de nom fort est un mécanisme d’identité dans le .NET Framework permettant d’identifier des assemblys. Il s’agit d’une signature numérique de clé publique qui sert généralement à vérifier l’intégrité des données transmises d’un expéditeur (signataire) vers un destinataire (vérificateur). Cette signature est utilisée comme identité unique pour un assembly, et garantit que les références à l’assembly ne sont pas ambiguës. L’assembly est signé dans le cadre du processus de génération, puis vérifié quand il est chargé.  
  
 Les signatures de nom fort empêchent des parties malveillantes de falsifier un assembly et de le resigner avec la clé du signataire d’origine. Toutefois, les clés de nom fort ne contiennent pas d’informations fiables sur l’éditeur, ni de hiérarchie de certificats. Une signature de nom fort ne garantit pas la fiabilité de la personne qui a signé l’assembly, et ne garantit pas non plus que cette personne était un propriétaire légitime de la clé ; elle indique uniquement que le propriétaire de la clé a signé l’assembly. Par conséquent, nous déconseillons d’utiliser une signature de nom fort comme validateur de sécurité pour approuver du code tiers. Microsoft Authenticode est la méthode recommandée pour authentifier le code.  
  
## <a name="limitations-of-conventional-strong-names"></a>Limitations des noms forts classiques  
 La technologie d’affectation de noms forts utilisée dans les versions antérieures au [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a les inconvénients suivants :  
  
-   Les clés subissent constamment des attaques, et le matériel et les techniques améliorés facilitent la déduction d’une clé privée à partir d’une clé publique. Pour se protéger des attaques, de plus grandes clés sont nécessaires. Les versions du .Net Framework antérieures au [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] permettent de signer avec n’importe quelle taille de clé (la taille par défaut étant 1024 bits), mais signer un assembly avec une nouvelle clé brise tous les binaires qui référencent l’ancienne identité de l’assembly. Par conséquent, il est extrêmement difficile de mettre à niveau la taille d’une clé de signature si vous voulez assurer la compatibilité.  
  
-   La signature de nom fort prend en charge uniquement l’algorithme SHA-1. Il a été récemment observé que SHA-1 n’était pas adéquat pour les applications de hachage sécurisées. Par conséquent, un algorithme plus fort (SHA-256 ou supérieur) est nécessaire. Il est possible que SHA-1 perde sa position conforme FIPS, ce qui poserait des problèmes pour ceux qui choisissent d’utiliser uniquement des logiciels et des algorithmes conformes FIPS.  
  
## <a name="advantages-of-enhanced-strong-names"></a>Avantages des noms forts améliorés  
 Les principaux avantages des noms forts améliorés sont la compatibilité avec les noms forts préexistants et la capacité à revendiquer qu’une identité est équivalente à une autre :  
  
-   Les développeurs qui ont des assemblys signés pré-existants peuvent migrer leurs identités vers les algorithmes SHA-2 tout en conservant la compatibilité avec les assemblys qui référencent les anciennes identités.  
  
-   Les développeurs qui créent de nouveaux assemblys et ne sont pas concernés par les signatures de nom fort préexistantes peuvent utiliser les algorithmes SHA-2 plus sécurisés et signer les assemblys comme ils l’ont toujours fait.  
  
## <a name="using-enhanced-strong-names"></a>Utilisation de noms forts améliorés  
 Les clés de nom fort se composent d’une clé de signature et d’une clé d’identité. L’assembly est signé avec la clé de signature et est identifié par la clé d’identité. Avant le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ces deux clés étaient identiques. À partir du [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], la clé d’identité est la même que dans les versions antérieures du. Net Framework, mais la clé de signature est améliorée avec un algorithme de hachage plus fort. En outre, la clé de signature est signée avec la clé d’identité pour créer une contre-signature.  
  
 L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> permet aux métadonnées de l’assembly d’utiliser la clé publique préexistante pour l’identité d’assembly, ce qui permet aux anciennes références d’assembly de continuer à fonctionner.  L’attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> utilise la contre-signature pour garantir que le propriétaire de la nouvelle clé de signature est également le propriétaire de l’ancienne clé d’identité.  
  
### <a name="signing-with-sha-2-without-key-migration"></a>Signature avec SHA-2, sans migration de clé  
 Exécutez les commandes suivantes à partir d’une fenêtre d’invite de commandes pour signer un assembly sans migrer une signature de nom fort :  
  
1.  Générez la nouvelle clé d’identité (si nécessaire).  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  Extrayez la clé publique d’identité et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  Signez en différé l’assembly avec le fichier de clé publique d’identité.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  Resignez l’assembly avec la paire de clés d’identité complète.  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="signing-with-sha-2-with-key-migration"></a>Signature avec SHA-2, avec migration de clé  
 Exécutez les commandes suivantes à partir d’une fenêtre d’invite de commandes pour signer un assembly avec une signature de nom fort migrée.  
  
1.  Générez une paire de clés d’identité et de signature (si nécessaire).  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  Extrayez la clé publique de signature et indiquez qu’un algorithme SHA-2 doit être utilisé lors de la signature avec cette clé.  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  Extrayez la clé publique d’identité, qui détermine l’algorithme de hachage qui génère une contre-signature.  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  Générez les paramètres pour un attribut <xref:System.Reflection.AssemblySignatureKeyAttribute> et attachez l’attribut à l’assembly.  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  Signez en différé l’assembly avec la clé publique d’identité.  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6.  Signez complètement l’assembly avec la paire de clés de signature.  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Création et utilisation d’assemblys avec nom fort](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
