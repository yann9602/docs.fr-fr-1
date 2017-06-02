---
title: "Exposing COM Components to the .NET Framework | Microsoft Docs"
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
  - "exposing COM components to .NET Framework"
  - "interoperation with unmanaged code, exposing COM components"
  - "COM interop, exposing COM components"
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Exposing COM Components to the .NET Framework
Cette section récapitule la procédure à suivre pour exposer un composant COM existant à du code managé.  Pour plus d'informations sur l'écriture de serveurs COM s'intégrant parfaitement au .NET Framework, consultez [Considérations de design pour l'interopérabilité](http://msdn.microsoft.com/fr-fr/b59637f6-fe35-40d6-ae72-901e7a707689).  
  
 Les composants COM existants constituent de précieuses ressources dans le code managé en tant qu'applications de gestion de couche intermédiaire ou en tant que fonctionnalités isolées.  Un composant idéal possède un assembly PIA \(Primary Interop Assembly\) et se conforme scrupuleusement aux normes de programmation imposées par COM.  
  
#### Pour exposer des composants COM au .NET Framework  
  
1.  [Importez une bibliothèque de types sous la forme d'un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md).  
  
     Le Common Language Runtime nécessite des métadonnées pour tous les types, y compris les types COM.  Un assembly contenant des types COM importés sous la forme de métadonnées peut être obtenu de différentes manières.  
  
2.  [Créez des types COM dans du code managé](http://msdn.microsoft.com/fr-fr/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).  
  
     Vous pouvez inspecter des types COM, activer des instances et appeler des méthodes sur l'objet COM de la même manière que vous le faites pour un type managé.  
  
3.  [Compilez un projet d'interopérabilité](../../../docs/framework/interop/compiling-an-interop-project.md).  
  
     Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournit des compilateurs conformes à la spécification CLS, y compris [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C\# et C\+\+.  
  
4.  [Déployez une application d'interopérabilité](../../../docs/framework/interop/deploying-an-interop-application.md).  
  
     Les applications d'interopérabilité sont les mieux déployées sous la forme d'assemblys signés avec [nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md) dans le Global Assembly Cache.  
  
## Voir aussi  
 [Interoperating with Unmanaged Code](../../../docs/framework/interop/index.md)   
 [Design Considerations for Interoperation](http://msdn.microsoft.com/fr-fr/b59637f6-fe35-40d6-ae72-901e7a707689)   
 [COM Interop Sample: .NET Client and COM Server](../../../docs/framework/interop/com-interop-sample-net-client-and-com-server.md)   
 [Indépendance du langage et composants indépendants du langage](../../../docs/standard/language-independence-and-language-independent-components.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)