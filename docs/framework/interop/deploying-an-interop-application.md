---
title: "Déploiement d'une application d'interopérabilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0682fd149134531781346d21245a0b1fd3fc4d43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="deploying-an-interop-application"></a>Déploiement d'une application d'interopérabilité
Une application d’interopérabilité comporte généralement un assembly client .NET, un ou plusieurs assemblys d’interopérabilité représentant des bibliothèques de types COM distinctes, et un ou plusieurs composants COM inscrits. Visual Studio et le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournissent des outils pour importer et convertir une bibliothèque de types vers un assembly d’interopérabilité, comme décrit dans [Importation d’une bibliothèque de types sous la forme d’un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md). Il existe deux façons de déployer une application d’interopérabilité :  
  
-   En utilisant des types d’interopérabilité : à compter de [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], vous pouvez indiquer au compilateur d’incorporer les informations de type d’un assembly d’interopérabilité dans votre exécutable. Le compilateur incorpore uniquement les informations de type que votre application utilise. Vous n’avez pas à déployer l’assembly d’interopérabilité avec votre application. Il s'agit de la technique recommandée.  
  
-   En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité. Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application. Si vous utilisez cette technique et que vous n’utilisez pas un composant COM privé, référencez toujours l’assembly PIA (Primary Interop Assembly) publié par l’auteur du composant COM que vous prévoyez d’incorporer dans votre code managé. Pour plus d’informations sur la production et l’utilisation d’assemblys PIA, consultez [Assemblys PIA (Primary Interop Assembly)](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
 Si vous utilisez des types interop incorporés, le déploiement est simple et direct. Vous n’avez rien de spécial à faire. Le reste de cet article décrit les scénarios de déploiement des assemblys d’interopérabilité avec votre application.  
  
## <a name="deploying-interop-assemblies"></a>Déploiement des assemblys d’interopérabilité  
 Les assemblys peuvent avoir des noms forts. Un assembly avec nom fort inclut la clé publique de l’éditeur, qui fournit une identité unique. Les assemblys qui sont produits par l’[importateur de bibliothèques de types (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) peuvent être signés par l’éditeur à l’aide de l’option **/keyfile**. Vous pouvez installer des assemblys signés dans le Global Assembly Cache. Les assemblys non signés doivent être installés sur la machine de l’utilisateur en tant qu’assemblys privés.  
  
### <a name="private-assemblies"></a>Assemblys privés  
 Pour installer un assembly destiné à une utilisation privée, vous devez installer l’exécutable de l’application et l’assembly d’interopérabilité qui contient les types COM importés dans la même structure de répertoires. L’illustration suivante montre un assembly d’interopérabilité non signé destiné à une utilisation privée par Client1.exe et Client2.exe, qui se trouvent dans des répertoires distincts de l’application. L’assembly d’interopérabilité, appelé LOANLib.dll dans cet exemple, est installé deux fois.  
  
 ![Structure de répertoires et Registre Windows](../../../docs/framework/interop/media/comdeployprivate.gif "comdeployprivate")  
Structure de répertoires et entrées du Registre pour un déploiement privé  
  
 Tous les composants COM associés à l’application doivent être installés dans le Registre Windows. Si les fichiers Client1.exe et Client2.exe de l’illustration sont installés sur des ordinateurs différents, vous devez inscrire les composants COM sur les deux ordinateurs.  
  
### <a name="shared-assemblies"></a>Assemblys partagés  
 Les assemblys qui sont partagés par plusieurs applications doivent être installés dans un référentiel centralisé appelé le Global Assembly Cache. Les clients .NET peuvent accéder à la même copie de l’assembly d’interopérabilité, qui est signé et installé dans le Global Assembly Cache. Pour plus d’informations sur la production et l’utilisation d’assemblys PIA, consultez [Assemblys PIA (Primary Interop Assembly)](http://msdn.microsoft.com/en-us/b977a8be-59a0-40a0-a806-b11ffba5c080).  
  
## <a name="see-also"></a>Voir aussi  
 [Exposition de composants COM au .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Importation d'une bibliothèque de types sous la forme d'un assembly](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)  
 [Utilisation de Types COM en Code managé](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [Compilation d'un projet d'interopérabilité](../../../docs/framework/interop/compiling-an-interop-project.md)
