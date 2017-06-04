---
title: "Emplacement des assemblys | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<codeBase> (élément)"
  - "assemblys (.NET Framework), emplacement"
  - "assemblys (.NET Framework), positionnement"
  - "rechercher des assemblys"
ms.assetid: ff8d48bc-f606-484f-9fe1-d0af264269fb
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Emplacement des assemblys
Pour la plupart des applications .NET Framework, vous localisez les assemblys qui composent une application dans le répertoire de l'application, dans un sous\-répertoire de l'application ou dans le Global Assembly Cache \(si l'assembly est partagé\).  Vous pouvez substituer l'emplacement de recherche d'un assembly par le Common Language Runtime à l'aide de l'[\<codeBase\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) dans un fichier de configuration.  Si l'assembly ne possède pas de nom fort, l'emplacement spécifié à l'aide de l'[\<codeBase\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) est limité au répertoire ou à un sous\-répertoire de l'application.  Si l'assembly possède un nom fort, l'[\<codeBase\>, élément](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) peut spécifier un emplacement quelconque sur l'ordinateur ou sur un réseau.  
  
 Des règles similaires sont appliquées pour localiser des assemblys lors de l'utilisation d'applications de code non managé ou de COM Interop : si l'assembly est partagé par plusieurs applications, il doit alors être installé dans le Global Assembly Cache.  Les assemblys utilisés avec du code non managé doivent être exportés en tant que bibliothèque de types et être inscrits.  Les assemblys utilisés par COM Interop doivent être inscrits dans le catalogue, même si cette inscription s'effectue dans certains cas automatiquement.  
  
## Voir aussi  
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Configuration d'applications](../../../docs/framework/configure-apps/index.md)   
 [Advanced COM Interoperability](http://msdn.microsoft.com/fr-fr/3ada36e5-2390-4d70-b490-6ad8de92f2fb)   
 [Assemblys dans le Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)