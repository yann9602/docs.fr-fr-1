---
title: "Emplacement de l&#39;assembly | Microsoft Docs"
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
  - "assemblys (.NET Framework), emplacement"
  - "rechercher des assemblys"
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# Emplacement de l&#39;assembly
L'emplacement d'un assembly détermine si le Common Language Runtime peut le trouver lorsqu'il est référencé. Il peut également déterminer si l'assembly peut être partagé avec d'autres assemblys.  Vous pouvez déployer un assembly aux emplacements suivants :  
  
-   Répertoire ou sous\-répertoires de l'application.  
  
     Il s'agit de l'emplacement le plus courant pour déployer un assembly.  Les sous\-répertoires du répertoire racine d'une application peuvent être basés sur la langue ou sur la culture.  Si un assembly possède des informations dans l'attribut de culture, il doit être placé dans un sous\-répertoire du répertoire de l'application avec le nom de cette culture.  
  
-   Global Assembly Cache.  
  
     Il s'agit d'un cache de code à l'échelle de l'ordinateur, installé au même emplacement que le Common Language Runtime.  Dans la plupart des cas, si vous comptez partager un assembly entre plusieurs applications, vous devez le déployer dans le Global Assembly Cache.  
  
-   Serveur HTTP.  
  
     Un assembly déployé sur un serveur HTTP doit avoir un nom fort. Pointez sur l'assembly dans la section du code base du fichier de configuration de l'application.  
  
## Voir aussi  
 [Création d'assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Programmation à l'aide d'assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)