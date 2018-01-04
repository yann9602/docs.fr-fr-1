---
title: Fonctions statiques globales du profilage
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66f22557dd6020ff5040d5aaf76cb12e9ae9965c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="profiling-global-static-functions"></a>Fonctions statiques globales du profilage
Cette section décrit les fonctions d’API non managées que l’API de profilage utilise.  
  
## <a name="in-this-section"></a>Dans cette section  
  
## <a name="net-framework-version-1-profiling-functions"></a>Fonctions de profilage du .NET framework version 1  
 [FunctionEnter, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction. Déconseillé dans .NET Framework 2.0.  
  
 [FunctionLeave, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifie le profileur qu’une fonction est sur le point de retourner à l’appelant. Déconseillé dans .NET Framework 2.0.  
  
 [FunctionTailcall, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction. Déconseillé dans .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>Fonctions de profilage du .NET framework version 2  
 [FunctionIDMapper, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé vers un autre ID à utiliser dans le [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), et [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) rappels pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction  
  
 [FunctionEnter2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit des informations sur la pile des arguments de fonction et de frame. Déconseillées dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionLeave2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifie le profileur qu’une fonction doit retourner à l’appelant et fournit des informations sur la valeur de retour pile fonction et de frame. Déconseillées dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [FunctionTailcall2, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction et fournit des informations sur le frame de pile. Déconseillées dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StackSnapshotCallback, fonction](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Fournit au profileur des informations sur chaque frame managé et chaque exécution de frames non managés sur la pile pendant un parcours de pile, qui est initié par le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) (méthode).  
  
## <a name="net-framework-version-4-profiling-functions"></a>Fonctions de profilage du .NET framework version 4  
 [FunctionIDMapper2, fonction](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifie le profileur que l’identificateur donné d’une fonction peut être remappé vers un autre ID à utiliser dans le [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), et [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), ou[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), et [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) rappels pour cette fonction. Permet également au profileur d’indiquer s’il souhaite recevoir des rappels pour cette fonction.  
  
 `FunctionIDMapper2`étend la [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) fonctionne avec un `clientData` paramètre, qui les profileurs peuvent utiliser pour distinguer les différents runtimes.  
  
 [FunctionEnter3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction.  
  
 [FunctionEnter3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifie le profileur que le contrôle est passé à une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) pour récupérer les arguments de fonction et de frame de pile.  
  
 [FunctionLeave3, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction.  
  
 [FunctionLeave3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Notifie le profileur que le contrôle a été renvoyé à partir d’une fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) pour récupérer le frame de pile et la valeur de retour.  
  
 [FunctionTailcall3, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction.  
  
 [FunctionTailcall3WithInfo, fonction](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Notifie le profileur que la fonction en cours d’exécution est sur le point d’exécuter un appel tail à une autre fonction et fournit un handle qui peut être passé à [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) pour extraire le frame de pile.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Vue d’ensemble du profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [Énumérations de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [Structures de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
