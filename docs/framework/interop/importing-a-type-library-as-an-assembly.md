---
title: "Importing a Type Library as an Assembly | Microsoft Docs"
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
  - "importing type library"
  - "type metadata"
  - "custom wrappers"
  - "metadata"
  - "exposing COM components to .NET Framework"
  - "Type Library Importer"
  - "interoperation with unmanaged code, importing type library"
  - "interoperation with unmanaged code, exposing COM components"
  - "type libraries"
  - "TypeLibConverter class, importing type library as assembly"
  - "COM interop, importing type library"
  - "COM interop, exposing COM components"
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Importing a Type Library as an Assembly
Les définitions des types COM résident généralement dans une bibliothèque de types.  Les compilateurs conformes CLS produisent quant à eux les métadonnées des types dans un assembly.  Ces deux sources d'informations sur les types sont assez différentes.  Cette rubrique décrit des techniques permettant de générer des métadonnées à partir d'une bibliothèque de types.  L'assembly résultant est appelé assembly d'interopérabilité, et les informations de type qu'il contient permettent aux applications .NET Framework d'utiliser des types COM.  
  
 Il existe deux façons de mettre ces informations de type à disposition pour votre application :  
  
-   En utilisant des assemblys d'interopérabilité au moment du design : en commençant par le [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez instruire le compilateur afin qu'il incorpore les informations de type à partir d'un assembly d'interopérabilité dans votre fichier exécutable.  Le compilateur incorpore uniquement les informations de type que votre application utilise.  Vous n'avez pas à déployer l'assembly d'interopérabilité avec votre application.  Il s'agit de la technique recommandée.  
  
-   En déployant des assemblys d'interopérabilité : vous pouvez créer une référence standard à l'assembly d'interopérabilité.  Dans ce cas, l'assembly d'interopérabilité doit être déployé avec votre application.  Si vous utilisez cette technique et que vous n'utilisez pas un composant COM privé, référencez toujours l'assembly PIA publié par l'auteur du composant COM que vous prévoyez d'incorporer dans votre code managé.  Pour plus d'informations sur la production et l'utilisation d'assemblys d'interopérabilité, consultez [Assemblys PIA \(Primary Interop Assembly\)](http://msdn.microsoft.com/fr-fr/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
 Lorsque vous utilisez des assemblys d'interopérabilité au moment du design, vous pouvez incorporer les informations de type de l'assembly PIA \(Primary Interop Assembly\) publié par l'auteur du composant COM.  Toutefois, vous n'avez pas à déployer l'assembly PIA avec votre application.  
  
 L'utilisation d'assemblys d'interopérabilité au moment du design réduit la taille de votre application, car la plupart des applications n'utilisent pas toutes les fonctionnalités d'un composant COM.  Le compilateur est très efficace lorsqu'il incorpore les informations de type ; si votre application utilise uniquement certaines des méthodes sur une interface COM, le compilateur n'incorpore pas les méthodes inutilisées.  Lorsqu'une application qui a incorporé les informations de type interagit avec une autre application du même type, ou interagit avec une application qui utilise un assembly PIA \(Primary Interop Assembly\), le Common Language Runtime utilise des règles d'équivalence du type pour déterminer si deux types avec le même nom représentent le même type COM.  Vous n'avez pas à savoir ces règles pour utiliser des objets COM.  Toutefois, si vous vous intéressez aux règles, consultez [Type Equivalence and Embedded Interop Types](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## Génération de métadonnées  
 Les bibliothèques de types COM peuvent être des fichiers autonomes qui ont une extension .tlb, telle que Loanlib.tlb.  Certaines bibliothèques de types sont incorporées dans la section de ressources d'un fichier .dll ou .exe.  D'autres sources d'informations de bibliothèque de types sont des fichiers .olb et .ocx.  
  
 Une fois que vous avez trouvé la bibliothèque de types qui contient l'implémentation de votre type COM cible, vous disposez des options suivantes pour générer un assembly d'interopérabilité contenant des métadonnées de type :  
  
-   Visual Studio  
  
     Visual Studio convertit automatiquement des types COM dans une bibliothèque de types en métadonnées dans un assembly.  Pour obtenir des instructions, consultez [Comment : ajouter des références aux bibliothèques de types](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md) et [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
-   [Type Library Importer \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Cet importateur fournit des options de ligne de commande pour ajuster les métadonnées dans le fichier d'interopérabilité résultant, importe des types d'une bibliothèque de types existante et génère un assembly et un espace de noms.  Pour obtenir des instructions, consultez [Comment faire : générer des assemblys d'interopérabilité à partir de bibliothèques de types](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   Classe <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=fullName>  
  
     Cette classe fournit des méthodes pour convertir des coclasses et des interfaces dans une bibliothèque de types en métadonnées dans un assembly.  Il produit la même sortie de métadonnées que Tlbimp.exe.  Toutefois, la classe <xref:System.Runtime.InteropServices.TypeLibConverter> peut convertir une bibliothèque de types en mémoire en métadonnées contrairement à Tlbimp.exe.  
  
-   Wrappers personnalisés  
  
     Lorsqu'une bibliothèque de types est indisponible ou incorrecte, vous pouvez opter pour la création d'une définition dupliquée de la classe ou de l'interface dans du code source managé.  Vous pouvez ensuite compiler le code source avec un compilateur qui cible le runtime pour produire des métadonnées dans un assembly.  
  
     Pour définir manuellement des types COM, vous devez avoir accès aux éléments suivants :  
  
    -   des descriptions précises des coclasses et des interfaces qui sont définies ;  
  
    -   un compilateur, tel que le compilateur C\#, pouvant générer les définitions des classes .NET Framework appropriées ;  
  
    -   une connaissance des règles de conversion de bibliothèque de types en assembly.  
  
     L'écriture dans un wrapper personnalisé est une technique avancée.  Pour obtenir des informations supplémentaires sur la manière de générer un wrapper personnalisé, consultez [Personnalisation de wrappers standard](http://msdn.microsoft.com/fr-fr/c40d089b-6a3c-41b5-a20d-d760c215e49d).  
  
 Pour plus d'informations sur le processus d'importation COM Interop, consultez [Résumé de la conversion d'une bibliothèque de types en assembly](http://msdn.microsoft.com/fr-fr/bf3f90c5-4770-4ab8-895c-3ba1055cc958).  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.TypeLibConverter>   
 [Exposing COM Components to the .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/fr-fr/bf3f90c5-4770-4ab8-895c-3ba1055cc958)   
 [Tlbimp.exe \(Type Library Importer\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)   
 [Customizing Standard Wrappers](http://msdn.microsoft.com/fr-fr/c40d089b-6a3c-41b5-a20d-d760c215e49d)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/fr-fr/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [Compiling an Interop Project](../../../docs/framework/interop/compiling-an-interop-project.md)   
 [Deploying an Interop Application](../../../docs/framework/interop/deploying-an-interop-application.md)   
 [How to: Add References to Type Libraries](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)   
 [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)