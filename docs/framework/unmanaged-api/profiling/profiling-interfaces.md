---
title: Interfaces de profilage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
caps.latest.revision: "31"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c0423f9c8b01c1289e1107c0c16c59968a6e2a4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="profiling-interfaces"></a>Interfaces de profilage
Cette section décrit les interfaces non managées qui vous permettent de profiler un programme exécuté par le CLR (Common Language Runtime).  
  
## <a name="in-this-section"></a>Dans cette section  
 [ICLRProfiling (Interface)](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 Fournit la [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) (méthode), ce qui permet à un profileur de s’attacher à un processus en cours d’exécution.  
  
 [Icorprofilerassemblyreferenceprovider, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 Permet au profileur d’informer le CLR de références d’assembly que le profileur ajoutera dans le [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) rappel.  
  
 [Interface ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 Fournit des méthodes qui sont utilisées par le CLR pour envoyer des notifications à un profileur de code quand les événements auxquels le profileur s'est abonné se produisent.  
  
 [ICorProfilerCallback2, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 Étend l'interface `ICorProfilerCallback` avec des rappels pris en charge dans .NET Framework 2.0 et ultérieur.  
  
 [ICorProfilerCallback3 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 Fournit des méthodes de rappel que le CLR utilise pour communiquer au profileur des informations d'état d'attachement et de détachement.  
  
 [ICorProfilerCallback4 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 Fournit des méthodes de rappel que le CLR utilise pour communiquer des informations au profileur.  
  
 [ICorProfilerCallback5 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 Fournit une méthode qui identifie la fermeture transitive d’objets référencés par des racines de récupération de mémoire.  
  
 [Icorprofilercallback6, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 Fournit une méthode de rappel utilisée par le CLR pour envoyer une notification à un profileur quand un assembly est en cours de chargement.  
  
 [Interface ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 Fournit une méthode de rappel que le common language runtime utilise pour informer le profileur que le flux de symbole associé à un module en mémoire est mis à jour.  
  
 [ICorProfilerFunctionControl (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 Fournit des méthodes qui permettent à un profileur de code de communiquer avec le CLR (Common Language Runtime) pour contrôler comment le compilateur juste-à-temps doit générer du code lors de la recompilation d'une méthode spécifique.  
  
 [ICorProfilerFunctionEnum (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de fonctions dans le CLR.  
  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.  
  
 [ICorProfilerInfo2 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 Étend l'interface `ICorProfilerInfo` avec des méthodes prises en charge dans .NET Framework 2.0 et ultérieur.  
  
 [ICorProfilerInfo3 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 Étend l'interface `ICorProfilerInfo2` avec des méthodes prises en charge dans [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] et ultérieur.  
  
 [Icorprofilerinfo4, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.  
  
 [Icorprofilerinfo5, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 Fournit des méthodes utilisées par les profileurs de code pour communiquer avec le CLR pour contrôler la surveillance des événements.  
  
 [Interface de ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 Fournit un énumérateur pour toutes les méthodes qui appartiennent à un module NGen donné et qui sont incorporées dans le corps d’une méthode donnée.  
  
 [Interface de ICorProfilerInfo7](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 Fournit une méthode à appliquer qui vient d’être défini des métadonnées à un module et qui fournit l’accès à un flux de symbole de mémoire.  
  
 [ICorProfilerModuleEnum (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de modules chargés par l’application ou par le profileur.  
  
 [ICorProfilerObjectEnum (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 Fournit des méthodes pour itérer séquentiellement une collection d’objets figés qui sont générés par [Ngen.exe (Native Image Generator)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
 [ICorProfilerThreadEnum (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 Fournit des méthodes pour boucler séquentiellement dans une collection de threads dans le CLR.  
  
 [IMethodMalloc (Interface)](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 Fournit la [Alloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md) méthode pour allouer de la mémoire pour un nouveau corps de fonction MSIL (intermediate language).  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Fonctions statiques globales du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
