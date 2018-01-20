---
title: "Comment : créer une stratégie d'éditeur"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4ccd490f6d31ad1d20128497e5115147eddb3df4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-publisher-policy"></a>Comment : créer une stratégie d'éditeur
Les fournisseurs d’assemblys peuvent indiquer que les applications doivent utiliser une version plus récente d’un assembly en incluant un fichier de stratégie de serveur de publication avec l’assembly mis à niveau. Le fichier de stratégie d’éditeur spécifie la redirection d’assembly et les paramètres de base de code et utilise le même format comme un fichier de configuration. Le fichier de stratégie d’éditeur est compilé dans un assembly et placé dans le global assembly cache.  
  
 Il existe trois étapes impliquées dans la création d’une stratégie d’éditeur :  
  
1.  Créez un fichier de stratégie du serveur de publication.  
  
2.  Créer un assembly de stratégie d’éditeur.  
  
3.  Ajoutez l’assembly de stratégie du serveur de publication dans le global assembly cache.  
  
 Le schéma de la stratégie d’éditeur est décrit dans [redirection des Versions d’Assembly](../../../docs/framework/configure-apps/redirect-assembly-versions.md). L’exemple suivant montre un éditeur de fichier de stratégie qui redirige une version de `myAssembly` à un autre.  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 Pour savoir comment spécifier une base de code, consultez [spécifiant l’emplacement d’un Assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## <a name="creating-the-publisher-policy-assembly"></a>Création de l’Assembly de stratégie d’éditeur  
 Utilisez le [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer l’assembly de stratégie du serveur de publication.  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>Pour créer un assembly de stratégie d’éditeur  
  
1.  Tapez la commande suivante à l’invite de commandes :  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     Dans cette commande :  
  
    -   Le *publisherPolicyFile* argument est le nom du fichier de stratégie de serveur de publication.  
  
    -   Le *publisherPolicyAssemblyFile* argument est le nom de l’assembly de stratégie d’éditeur qui résulte de cette commande. Le nom de fichier d’assembly doit suivre le format :  
  
         **stratégie.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   Le *keyPairFile* argument est le nom du fichier contenant la paire de clés. Vous devez signer l’assembly et l’assembly de stratégie d’éditeur avec la même paire de clés.  
  
    -   Le *processorArchitecture* argument identifie la plateforme ciblée par un assembly spécifique au processeur.  
  
        > [!NOTE]
        >  La possibilité de cibler une architecture de processeur spécifique est nouvelle dans .NET Framework version 2.0.  
  
     La commande suivante crée un assembly de stratégie d’éditeur appelé `policy.1.0.myAssembly` à partir d’un fichier de stratégie d’éditeur appelé `pub.config`, assigne un nom fort à l’assembly à l’aide de la paire de clés dans le `sgKey.snk` de fichiers et spécifie que l’assembly cible la x86 architecture de processeur.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     L’assembly de stratégie du serveur de publication doit correspondre à l’architecture de processeur de l’assembly auquel il s’applique. Par conséquent, si votre assembly a un <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> valeur <xref:System.Reflection.ProcessorArchitecture.MSIL>, l’assembly de stratégie d’éditeur pour cet assembly doit être créé avec `/platform:anycpu`. Vous devez fournir un distinct assembly de stratégie d’éditeur pour chaque assembly spécifique au processeur.  
  
     Une conséquence de cette règle est que pour modifier l’architecture de processeur pour un assembly, vous devez modifier le composant majeure ou mineure du numéro de version, afin que vous pouvez fournir un nouvel assembly de stratégie de serveur de publication avec l’architecture de processeur correcte. L’ancien assembly de stratégie d’éditeur ne peut pas traiter votre assembly une fois que votre assembly possède une architecture de processeur différente.  
  
     Une autre conséquence est que l’éditeur de liens version 2.0 ne peut pas être utilisé pour créer un assembly de stratégie d’éditeur pour un assembly compilé à l’aide de versions antérieures du .NET Framework, car elle spécifie toujours architecture de processeur.  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Ajout de l’Assembly de stratégie de serveur de publication dans le Global Assembly Cache  
 Utilisez le [l’outil Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour ajouter l’assembly de stratégie de serveur de publication dans le global assembly cache.  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>Pour ajouter l’assembly de stratégie de serveur de publication dans le global assembly cache  
  
1.  Tapez la commande suivante à l’invite de commandes :  
  
     **gacutil /i**  *publisherPolicyAssemblyFile*  
  
     La commande suivante ajoute `policy.1.0.myAssembly.dll` dans le global assembly cache.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  L’assembly de stratégie d’éditeur ne peut pas être ajouté dans le global assembly cache, sauf si le fichier de stratégie de serveur de publication d’origine se trouve dans le même répertoire que l’assembly.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Configuration d'applications](../../../docs/framework/configure-apps/index.md)  
 [Configuration des applications .NET Framework](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [Schéma des paramètres d’exécution](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)  
 [Redirection des versions d'assemblys](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
