---
title: Emplacement de l'assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: 7
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3bc0fc4e099540a87832b225aa0a3c262c54e9c3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="assembly-location"></a>Emplacement de l'assembly
L’emplacement d’un assembly détermine si le common language runtime peut le localiser quand il est référencé, et il peut aussi déterminer si l’assembly peut être partagé avec d’autres assemblys. Vous pouvez déployer un assembly dans les emplacements suivants :  
  
-   Répertoire ou sous-répertoires de l’application.  
  
     Il s’agit de l’emplacement le plus courant pour déployer un assembly. Les sous-répertoires du répertoire racine d’une application peuvent être basés sur la langue ou la culture. Si un assembly a des informations de l’attribut de culture, il doit se trouver dans un sous-répertoire sous le répertoire de l’application avec le nom de cette culture.  
  
-   Le Global Assembly Cache.  
  
     Il s’agit d’un cache de code au niveau de la machine, qui est installé partout où le common language runtime est installé. Dans la plupart des cas, si vous prévoyez de partager un assembly entre plusieurs applications, vous devez le déployer dans le Global Assembly Cache.  
  
-   Sur un serveur HTTP.  
  
     Un assembly déployé sur un serveur HTTP doit avoir un nom fort ; vous pointez vers l’assembly dans la section codebase du fichier de configuration de l’application.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’assemblys](../../../docs/framework/app-domains/create-assemblies.md)   
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)   
 [Méthode de localisation des assemblys par le runtime](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [Programmation à l’aide d’assemblys](../../../docs/framework/app-domains/programming-with-assemblies.md)

