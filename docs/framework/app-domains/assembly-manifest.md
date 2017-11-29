---
title: Manifeste d'assembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest
- dynamic assemblies, assembly manifest
- metadata, assembly manifest
- culture, assembly manifest
- assemblies [.NET Framework], metadata
ms.assetid: 8e40fab9-549d-4731-aec2-ffa47a382de0
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1df64129a0ae15b5bad387a62ca60bb4b1b92f7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-manifest"></a>Manifeste d'assembly
Chaque assembly, qu'il soit statique ou dynamique, comporte une collection de données qui décrit comment les éléments de l'assembly sont reliés les uns aux autres. Le manifeste d'assembly contient les métadonnées de l'assembly. Un manifeste d'assembly comprend toutes les métadonnées nécessaires pour spécifier la version requise et l'identité de sécurité de l'assembly, ainsi que toutes les métadonnées nécessaires pour définir la portée de l'assembly et résoudre les références aux ressources et aux classes. Le manifeste d'assembly peut être stocké soit dans un fichier exécutable portable (PE, portable executable) (.exe ou .dll) avec le code MILS (Microsoft Intermediate Language), soit dans un fichier PE autonome qui ne contient que des informations sur le manifeste de l'assembly.  
  
 L'illustration ci-dessous indique les différents modes de stockage du manifeste.  
  
 ![Assembly monofichier](../../../docs/framework/app-domains/media/assemblytypes.gif "assemblytypes")  
Types d'assemblys  
  
 Pour un assembly avec un fichier associé, le manifeste est incorporé au fichier PE pour former un assembly monofichier. Vous pouvez créer un assembly multifichier avec un fichier manifeste autonome ou avec le manifeste incorporé à l'un des fichiers PE de l'assembly.  
  
 Le manifeste de chaque assembly exécute les fonctions suivantes :  
  
-   Il énumère les fichiers qui composent l'assembly.  
  
-   Il détermine le mode de mappage des références aux types et aux ressources de l'assembly aux fichiers qui contiennent leurs déclarations et leurs implémentations.  
  
-   Il énumère les autres assemblys dont l'assembly dépend.  
  
-   Il fournit un niveau d'adressage indirect entre les consommateurs de l'assembly et les détails d'implémentation de l'assembly.  
  
-   Il rend l'assembly autodescriptif.  
  
## <a name="assembly-manifest-contents"></a>Contenu du manifeste d'assembly  
 Le tableau suivant indique les informations qui figurent dans le manifeste d'assembly. Les quatre premiers éléments (le nom de l'assembly, le numéro de version, la culture et les informations sur le nom fort) constituent l'identité de l'assembly.  
  
|Information|Description|  
|-----------------|-----------------|  
|Nom de l'assembly|Chaîne de texte spécifiant le nom de l'assembly.|  
|Numéro de version|Numéro de version principale et secondaire et numéro de révision et de build. Le Common Language Runtime utilise ces numéros pour appliquer la stratégie de version.|  
|Culture|Informations sur la culture ou le langage que l'assembly prend en charge. Ces informations ne doivent être utilisées que pour désigner un assembly en tant qu'assembly satellite contenant des informations spécifiques à la culture ou au langage. Un assembly possédant des informations sur la culture est automatiquement considéré comme étant un assembly satellite.|  
|Informations sur le nom fort|Clé publique de l'éditeur si un nom fort a été attribué à l'assembly.|  
|Liste de tous les fichiers figurant dans l'assembly|Hachage de chaque fichier figurant dans l'assembly et nom de fichier. Notez que tous les fichiers qui composent l'assembly doivent figurer dans le même répertoire que le fichier qui comporte le manifeste d'assembly.|  
|Informations sur les références de type|Informations utilisées par le runtime pour mapper une référence de type au fichier qui contient sa déclaration et son implémentation. Elles sont utilisées pour les types qui sont exportés à partir de l'assembly.|  
|Informations sur les assemblys référencés|Liste des autres assemblys statiquement référencés par l'assembly. Chaque référence inclut le nom de l'assembly dépendant, les métadonnées de l'assembly (version, culture, système d'exploitation...) et la clé publique, si l'assembly possède un nom fort.|  
  
 Vous pouvez ajouter ou modifier certaines informations dans le manifeste d'assembly en utilisant des attributs d'assembly dans votre code. Vous pouvez modifier les informations sur la version et les attributs d'informations, y compris la Marque, le Copyright, le Produit, la Société et la Version d'informations. Pour obtenir la liste complète des attributs d’assembly, consultez [Définition des attributs d’assembly](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contenu d’un assembly](../../../docs/framework/app-domains/assembly-contents.md)  
 [Contrôle de version des assemblys](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Création d’assemblys satellites](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)  
 [Assemblys avec nom fort](../../../docs/framework/app-domains/strong-named-assemblies.md)
