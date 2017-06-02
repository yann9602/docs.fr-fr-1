---
title: "Compiling an Interop Project | Microsoft Docs"
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
  - "interoperation with unmanaged code, compiling"
  - "COM interop, compiling"
  - "exposing COM components to .NET Framework"
  - "compiling interop projects"
  - "interoperation with unmanaged code, exposing COM components"
  - "COM interop, exposing COM components"
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: 16
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 16
---
# Compiling an Interop Project
Les projets de COM Interop qui référencent un ou plusieurs assemblys contenant des types COM importés sont compilés comme tout autre projet managé.  Vous pouvez référencer des assemblys d'interopérabilité dans un environnement de développement tel que Visual Studio, ou vous pouvez les référencer lorsque vous utilisez un compilateur de ligne de commande.  Dans les deux cas, l'assembly d'interopérabilité doit figurer dans le même répertoire que les autres fichiers projet pour que la compilation réussisse.  
  
 Il existe deux façons de référencer des assemblys d'interopérabilité :  
  
-   Types d'interopérabilité incorporés : à compter du [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] et de [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], vous pouvez instruire le compilateur pour incorporer les informations de type d'un assembly d'interopérabilité dans votre fichier exécutable.  Il s'agit de la technique recommandée.  
  
-   En déployant des assemblys d'interopérabilité : vous pouvez créer une référence standard à un assembly d'interopérabilité.  Dans ce cas, l'assembly d'interopérabilité doit être déployé avec votre application.  
  
 Les différences entre ces deux techniques sont abordées de manière plus détaillée dans [Using COM Types in Managed Code](http://msdn.microsoft.com/fr-fr/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
 L'incorporation des types d'interopérabilité avec Visual Studio est illustrée dans [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md) et [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
 Pour référencer un assembly d'interopérabilité avec un compilateur de ligne de commande et pour incorporer des informations de type dans vos fichiers exécutables, utilisez le commutateur de compilation [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md) ou [\/link](../Topic/-link%20\(Visual%20Basic\).md) et spécifiez le nom de l'assembly d'interopérabilité.  
  
> [!NOTE]
>  Les applications Visual C\+\+ ne peuvent pas incorporer d'informations de type, mais elles peuvent interagir avec des applications ou des compléments qui le font.  
  
 Pour compiler une application qui inclut un assembly PIA lorsqu'elle est déployée, utilisez le commutateur de compilation **\/reference** et spécifiez le nom de l'assembly d'interopérabilité.  
  
## Voir aussi  
 [Exposing COM Components to the .NET Framework](../../../docs/framework/interop/exposing-com-components.md)   
 [Indépendance du langage et composants indépendants du langage](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/fr-fr/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [Procédure pas à pas : incorporation d’informations de type provenant d’assemblys Microsoft Office](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Procédure pas à pas : incorporation de types provenant d’assemblys managés](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [Importing a Type Library as an Assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)