---
title: ICorProfilerInfo2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2
helpviewer_keywords: ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cbc0b4ad46c6a49313a42c4c232873988e7f4e99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2, interface
Fournit des méthodes que les profileurs de code utilisent pour communiquer avec le common language runtime (CLR) pour contrôler la surveillance des événements et les informations de demande. Le `ICorProfilerInfo2` interface est une extension de la [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface. Autrement dit, il fournit les nouvelles méthodes prises en charge dans le .NET Framework version 2.0 et versions ultérieures.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[DoStackSnapshot (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|Parcourt la pile du thread spécifié pour signaler les frames d’appels managés au profileur.|  
|[EnumModuleFrozenObjects (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|Obtient un énumérateur qui permet l’itération sur les objets figés dans le module spécifié.|  
|[GetAppDomainStaticAddress (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|Obtient l’adresse du champ statique de domaine application spécifiée dans la portée du domaine d’application spécifié.|  
|[GetArrayObjectInfo (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|Obtient des informations détaillées sur un objet tableau.|  
|[GetBoxClassLayout (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|Obtient des informations sur la disposition de classe pour un type valeur boxed.|  
|[GetClassFromTokenAndTypeArgs, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et le `ClassID` valeurs des arguments de type.|  
|[GetClassIDInfo2 (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|Obtient le module parent de la classe générique spécifiée, le jeton de métadonnées pour la classe, le `ClassID` de sa classe parente et le `ClassID` pour chaque argument de type, le cas échéant, de la classe.|  
|[GetClassLayout, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|Obtient des informations sur la disposition, dans la mémoire, des champs définis par la classe spécifiée. Autrement dit, cette méthode obtient les offsets des champs de la classe.|  
|[GetCodeInfo2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|Obtient l'étendue de code natif associée au `FunctionID` spécifié.|  
|[GetContextStaticAddress (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|Obtient l’adresse du champ statique de contexte spécifié qui est dans la portée du contexte spécifié.|  
|[GetFunctionFromTokenAndTypeArgs (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|Obtient le `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié contenant la classe, et `ClassID` valeurs des arguments de type.|  
|[GetFunctionInfo2 (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|Obtient la classe parente, le jeton de métadonnées et le `ClassID` de chaque argument de type, le cas échéant, d'une fonction.|  
|[GetGenerationBounds (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|Obtient les régions de mémoire (les segments du tas) qui composent les générations du tas de garbage collection.|  
|[GetNotifiedExceptionClauseInfo, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|Obtient les informations d’adresse et d’image natives pour la clause d’exception (`catch`/`finally`/`filter`) qui doit être exécutée ou vient d’être exécutée.|  
|[GetObjectGeneration, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|Obtient le segment du segment de mémoire qui contient l’objet spécifié.|  
|[GetRVAStaticAddress (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|Obtient l’adresse de l’adresse virtuelle relative (RVA) spécifié-champ statique.|  
|[GetStaticFieldInfo (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|Obtient la portée dans laquelle le champ spécifié est statique.|  
|[GetStringLayout (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|Obtient des informations sur la disposition d'un objet string.|  
|[GetThreadAppDomain (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|Obtient l’ID du domaine d’application dans lequel le thread spécifié est en cours d’exécution code.|  
|[GetThreadStaticAddress (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|Obtient l’adresse du champ statique de thread spécifié qui est dans la portée du thread spécifié.|  
|[SetEnterLeaveFunctionHooks2 (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|Spécifie les fonctions implémentées par le profileur à être appelée sur « entrer », « quitter » et « tailcall » de fonctions managées.|  
  
## <a name="remarks"></a>Remarques  
 Un profileur appelle une méthode dans le `ICorProfilerInfo2` interface pour communiquer avec le CLR pour contrôler la surveillance des événements et demander des informations.  
  
 Les méthodes de la `ICorProfilerInfo2` interface sont implémentées par le CLR à l’aide du modèle libre de threads. Chaque méthode retourne un HRESULT pour indiquer la réussite ou l'échec. Pour obtenir la liste des codes de retour possibles, consultez le fichier CorError.h.  
  
 Le CLR passe une `ICorProfilerInfo2` interface à chaque profileur de code pendant l’initialisation, à l’aide de l’implémentation du profileur de [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Un profileur de code peut ensuite appeler méthodes de la `ICorProfilerInfo2` interface pour obtenir des informations sur le code managé en cours d’exécution sous le contrôle du CLR.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
