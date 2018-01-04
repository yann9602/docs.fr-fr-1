---
title: "Interfaces de métadonnées"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e4043bdb7ea128e7ac34349dad8c51a0b247df71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="metadata-interfaces"></a>Interfaces de métadonnées
Cette section décrit les interfaces non managées qui donnent accès aux métadonnées exposées par les types, méthodes, champs, etc. du .NET Framework.  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICeeGen, interface](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 Fournit des méthodes pour la compilation de code dynamique.  
  
 [IHostFilter, interface](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)  
 Fournit une méthode permettant à l'hôte du runtime de marquer des jetons de métadonnées à traiter.  
  
 [IMapToken, interface](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md)  
 Fournit des fonctionnalités de mappage entre des signatures de métadonnées importées et émises.  
  
 [IMetaDataAssemblyEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 Fournit des méthodes qui prennent en charge le modèle d'autodescription utilisé par le Common Language Runtime (CLR) pour résoudre et consommer des ressources.  
  
 [IMetaDataAssemblyImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)  
 Fournit des méthodes pour accéder au contenu d'un manifeste d'assembly et l'examiner.  
  
 [IMetaDataConverter, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataconverter-interface.md)  
 Fournit des méthodes pour mapper des bibliothèques de types à leurs signatures de métadonnées et effectuer la conversion entre les deux.  
  
 [IMetaDataDispenser, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)  
 `IMetaDataDispenser` est obsolète. Utilisez plutôt `IMetaDataDispenserEx`.  
  
 [IMetaDataDispenserEx, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 Fournit des méthodes qui mappent des zones de mémoire pour créer ou modifier des métadonnées.  
  
 [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 Fournit des méthodes pour créer, modifier et stocker les métadonnées sur l'assembly dans la portée actuellement définie.  
  
 [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 Fournit des méthodes pour définir et modifier les signatures de métadonnées de méthodes et de constructeurs avec les paramètres de type <xref:System.Type?displayProperty=nameWithType>.  
  
 [IMetaDataError, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataerror-interface.md)  
 Fournit un mécanisme de rappel pour signaler les erreurs pendant la résolution de la signature de métadonnées d’un assembly.  
  
 [IMetaDataFilter, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)  
 Fournit des méthodes pour marquer et filtrer des jetons de métadonnées pour éviter de répéter des actions qui ont déjà été prises.  
  
 [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 Fournit des méthodes pour importer et manipuler des types provenant d'autres assemblys.  
  
 [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 Étend `IMetaDataImport` pour permettre d'utiliser des types génériques.  
  
 [IMetaDataInfo, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-interface.md)  
 Fournit une méthode qui obtient des informations sur le mappage de métadonnées à partir d'un fichier sur disque dans la mémoire.  
  
 [IMetaDataTables, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 Fournit des méthodes pour le stockage et la récupération d'informations de métadonnées dans des tables.  
  
 [IMetaDataTables2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)  
 Étend `IMetaDataTables` pour inclure des méthodes permettant d'utiliser des flux de métadonnées.  
  
 [IMetaDataValidate, interface](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)  
 Fournit des méthodes à utiliser pour la validation des signatures de métadonnées.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Fonctions statiques globales des métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)  
  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
  
 [Structures de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
  
 [Unions de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
