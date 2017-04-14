---
title: "Comment&#160;: cr&#233;er une strat&#233;gie d&#39;&#233;diteur | Microsoft Docs"
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
  - "Global Assembly Cache (GAC), assembly de stratégie d'éditeur"
  - "Global Assembly Cache, assembly de stratégie d'éditeur"
  - "assembly de stratégie d'éditeur"
  - "fichiers de stratégie d'éditeur"
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# Comment&#160;: cr&#233;er une strat&#233;gie d&#39;&#233;diteur
Les fournisseurs d'assemblys peuvent établir que les applications utilisent une nouvelle version en incluant un fichier de stratégie d'éditeur contenant l'assembly mis à jour.  Le fichier de stratégie de l'éditeur spécifie la redirection de l'assembly et les paramètres de base de code et utilise le même format que le fichier de configuration d'une application.  Le fichier de stratégie de l'éditeur est compilé dans un assembly et placé dans le Global Assembly Cache.  
  
 La création d'une stratégie de l'éditeur comporte trois étapes :  
  
1.  Créez un fichier de stratégie de l'éditeur.  
  
2.  Créez un assembly de stratégie d'éditeur.  
  
3.  Ajoutez l'assembly de stratégie d'éditeur au Global Assembly Cache.  
  
 Le schéma d'une stratégie de l'éditeur est décrit dans [Redirection des versions d'assemblys](../../../docs/framework/configure-apps/redirect-assembly-versions.md).  L'exemple suivant illustre un fichier de stratégie de l'éditeur qui redirige une version de `myAssembly` vers une autre.  
  
```  
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
  
 Pour savoir comment spécifier une base de code, consultez [Spécification de l'emplacement de l'assembly](../../../docs/framework/configure-apps/specify-assembly-location.md).  
  
## Création de l'assembly de stratégie d'éditeur  
 Utilisez l'utilitaire [Assembly Linker \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) pour créer l'assembly de stratégie d'éditeur.  
  
#### Pour créer un assembly de stratégie d'éditeur  
  
1.  Tapez la commande suivante à l'invite de commande :  
  
     **al \/link:** *publisherPolicyFile* **\/out:** *publisherPolicyAssemblyFile* **\/keyfile:** *keyPairFile* **\/platform:** *processorArchitecture*  
  
     Dans cette commande :  
  
    -   L'argument *publisherPolicyFile* est le nom du fichier de stratégie de l'éditeur.  
  
    -   L'argument *publisherPolicyAssemblyFile* est le nom de l'assembly de stratégie d'éditeur qui résulte de cette commande.  Le nom de fichier de l'assembly doit suivre le format suivant :  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   L'argument *keyPairFile* est le nom du fichier contenant la paire de clés.  Vous devez signer l'assembly et l'assembly de stratégie d'éditeur avec la même paire de clés.  
  
    -   L'argument *processorArchitecture* identifie la plateforme ciblée par un assembly spécifique au processeur.  
  
        > [!NOTE]
        >  La possibilité de cibler une architecture de processeur spécifique est une nouveauté du .NET Framework version 2.0.  
  
     La commande suivante crée un assembly de stratégie d'éditeur appelé `policy.1.0.myAssembly` à partir d'un fichier de stratégie d'éditeur appelé `pub.config`, assigne un nom fort à l'assembly à l'aide de la paire de clés qui se trouve dans le fichier `sgKey.snk` et indique que l'assembly cible l'architecture de processeur x86.  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     L'assembly de stratégie d'éditeur doit correspondre à l'architecture de processeur de l'assembly auquel il s'applique.  Ainsi, si la valeur <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> de votre assembly est <xref:System.Reflection.ProcessorArchitecture>, l'assembly de stratégie d'éditeur de cet assembly doit être créé avec `/platform:anycpu`.  Vous devez fournir un assembly de stratégie d'éditeur distinct pour chaque assembly spécifique au processeur.  
  
     Du fait de cette règle, pour modifier l'architecture de processeur d'un assembly, vous devez modifier le composant majeur ou mineur du numéro de version afin de pouvoir fournir un nouvel assembly de stratégie d'éditeur avec l'architecture de processeur correcte.  L'ancien assembly de stratégie d'éditeur ne peut pas assurer la maintenance de votre assembly une fois que celui\-ci a une architecture de processeur différente.  
  
     Cela implique également que l'éditeur de liens version 2.0 ne peut pas être utilisé pour créer un assembly de stratégie d'éditeur pour un assembly compilé à l'aide de versions précédentes du .NET Framework, car l'architecture de processeur est toujours spécifiée.  
  
## Ajout de l'assembly de stratégie d'éditeur au Global Assembly Cache  
 Utilisez l'[outil Global Assembly Cache Tool \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour ajouter l'assembly de stratégie d'éditeur au Global Assembly Cache.  
  
#### Pour ajouter l'assembly de stratégie d'éditeur au Global Assembly Cache  
  
1.  Tapez la commande suivante à l'invite de commande :  
  
     **gacutil \/i**  *publisherPolicyAssemblyFile*  
  
     La commande suivante ajoute `policy.1.0.myAssembly.dll` au Global Assembly Cache.  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  L'assembly de stratégie d'éditeur ne peut pas être ajouté au Global Assembly Cache à moins que le fichier de stratégie d'éditeur d'origine se trouve dans le même répertoire que l'assembly.  
  
## Voir aussi  
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuration d'applications](../../../docs/framework/configure-apps/index.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/fr-fr/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)   
 [Schéma des paramètres d'exécution](../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [Schéma des fichiers de configuration](../../../docs/framework/configure-apps/file-schema/index.md)   
 [Redirection des versions d'assemblys](../../../docs/framework/configure-apps/redirect-assembly-versions.md)