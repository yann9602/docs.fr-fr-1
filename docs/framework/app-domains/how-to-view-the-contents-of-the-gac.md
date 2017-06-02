---
title: "Comment&#160;: visualiser le contenu du Global Assembly Cache | Microsoft Docs"
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
  - "Global Assembly Cache (GAC), afficher le contenu"
  - "Gacutil.exe"
  - "Global Assembly Cache (outil)"
  - "Global Assembly Cache, afficher le contenu"
  - "liste des assemblys du Global Assembly Cache"
  - "assemblys avec nom fort, Global Assembly Cache"
  - "afficher des assemblys dans le Global Assembly Cache"
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# Comment&#160;: visualiser le contenu du Global Assembly Cache
Utilisez l'[outil Global Assembly Cache Tool \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pour visualiser le contenu du Global Assembly Cache.  
  
### Pour visualiser une liste des assemblys dans le Global Assembly Cache  
  
1.  À l'[invite de commandes Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), tapez la commande suivante :  
  
     **gacutil \-l**   
     ou               
     **gacutil \/l**  
  
 Dans les versions antérieures du .NET Framework, l'extension du shell Windows [Shfusion.dll](http://msdn.microsoft.com/fr-fr/0d9464cf-ddba-4ca9-bbec-f678fb58f380) vous permettait d'afficher le Global Assembly Cache dans l'Explorateur de fichiers.  À partir de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Shfusion.dll est obsolète.  
  
## Voir aussi  
 [Utilisation d'assemblys et du Global Assembly Cache](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe \(Global Assembly Cache Tool\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)