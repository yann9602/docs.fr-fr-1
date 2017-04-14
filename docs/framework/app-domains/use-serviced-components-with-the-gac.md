---
title: "Utilisation de composants de service avec le Global Assembly Cache | Microsoft Docs"
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
  - "assemblys (.NET Framework), Global Assembly Cache"
  - "Global Assembly Cache (GAC), composants de service"
  - "Global Assembly Cache, composants de service"
  - "composants de service, Global Assembly Cache"
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# Utilisation de composants de service avec le Global Assembly Cache
Les composants pris en charge \(composants COM\+ de code managé\) doivent être placés dans le Global Assembly Cache.  Dans certains scénarios, le Common Language Runtime et les services COM\+ peuvent gérer des composants pris en charge qui ne figurent pas dans le Global Assembly Cache. Dans d'autres scénarios, ceci se révèle impossible.  Les scénarios suivants en sont un exemple :  
  
-   Pour les composants pris en charge d'une application serveur COM\+, l'assembly contenant les composants doit être dans le Global Assembly Cache, car Dllhost.exe ne s'exécute pas dans le même répertoire que celui qui contient les composants pris en charge.  
  
-   Pour les composants pris en charge d'une application bibliothèque COM\+, le runtime et les services COM\+ peuvent résoudre la référence à l'assembly contenant les composants en effectuant une recherche dans le répertoire actif.  Dans ce cas, il n'est pas nécessaire que l'assembly soit dans le Global Assembly Cache.  
  
-   Pour les composants pris en charge d'une application ASP.NET, la situation est différente.  Si vous placez l'assembly contenant les composants pris en charge dans le répertoire bin de la base de l'application et si vous utilisez l'inscription à la demande, une copie fantôme de l'assembly sera placée dans le cache de téléchargement, car ASP.NET tire parti des fonctionnalités d'occultation du runtime.  
  
## Voir aussi  
 [How to: Create a Serviced Component](http://msdn.microsoft.com/fr-fr/7ec0b488-e5fc-46f2-a48d-1278ea4e301d)   
 [Utilisation d'assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [Assembly Cache Viewer \(Shfusion.dll\)](http://msdn.microsoft.com/fr-fr/0d9464cf-ddba-4ca9-bbec-f678fb58f380)