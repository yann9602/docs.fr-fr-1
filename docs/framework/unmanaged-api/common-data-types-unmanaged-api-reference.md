---
title: "Types de donn&#233;es communs (R&#233;f&#233;rence des API non manag&#233;es) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
ms.assetid: e4ab2c4c-9433-4eba-9e9a-096de406cafb
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# Types de donn&#233;es communs (R&#233;f&#233;rence des API non manag&#233;es)
Cette rubrique répertorie les types de données simples utilisés par les API non managées pour .NET Framework, qui sont définis par des instructions `typedef` en C\/C\+\+. Ces types de données sont généralement des alias pour des types de données primitifs C\/C\+\+. Les valeurs de ces types de données sont en général opaques, c'est\-à\-dire qu'elles sont retournées par une fonction ou une méthode particulière pour pouvoir être passées à d'autres fonctions ou méthodes sans modification.  
  
|Type de données|Définition|Défini dans|Description|  
|---------------------|----------------|-----------------|-----------------|  
|AppDomainID|`typedef UINT_PTR AppDomainID;`|corprof.h|L'identificateur d'un domaine d'application.|  
|AssemblyID|`typedef UINT_PTR AssemblyID;`|corprof.h|L'identificateur d'un assembly.|  
|ClassID|`typedef UINT_PTR ClassID;`|corprof.h|L'identificateur d'une classe managée.|  
|CONNID|`typedef DWORD CONNID;`|cordebug.h, mscoree.h|L'identificateur de connexion pour un thread qui est connecté à une instance de Microsoft SQL Server.|  
|ContextID|`typedef UINT_PTR ContextID;`|corprof.h|L'identificateur du contexte associé à un thread managé particulier.|  
|COR\_PRF\_ELT\_INFO|`typedef UINT_PTR COR_PRF_ELT_INFO;`|corprof.h|Un handle opaque qui représente des informations sur un frame de pile particulier.|  
|COR\_PRF\_FRAME\_INFO|`typedef UINT_PTR COR_PRF_FRAME_INFO;`|corprof.h|Un handle opaque qui pointe vers un frame de pile. Il est valide seulement pendant le rappel auquel il est passé.|  
|CORDB\_ADDRESS|`typedef ULONG64 CORDB_ADDRESS;`|cordebug.h|Une adresse en mémoire.|  
|CORDB\_CONTINUE\_STATUS|`typedef DWORD CORDB_CONTINUE_STATUS;`|cordebug.h|État de la continuation.|  
|CORDB\_REGISTER|`typedef ULONG64 CORDB_REGISTER;`|cordebug.h|La valeur d'un registre du processeur.|  
|FunctionID|`typedef UINT_PTR FunctionID;`|corprof.h|L'identificateur d'une fonction ou d'une méthode.|  
|GCHandleID|`typedef UINT_PTR GCHandleID;`|corprof.h|Un handle de récupération de mémoire.|  
|mdToken|`typedef UINT32 mdToken;`|corprof.h|Jeton de métadonnées \(une ligne dans une table de métadonnées\).|  
|ModuleID|`typedef UINT_PTR ModuleID;`|corprof.h|L'identificateur d'un module d'assembly.|  
|ObjectID|`typedef UINT_PTR ObjectID;`|corprof.h|L'identificateur d'un objet.|  
|ProcessID|`typedef UINT_PTR ProcessID;`|corprof.h|L'identificateur d'un processus managé.|  
|ReJITID|`typedef UINT_PTR ReJITID;`|corprof.h|Identificateur d'une fonction traitée juste\-à\-temps.|  
|TASKID|`typedef UINT64 TASKID;`|cordebug.h, mscoree.h|L'identificateur d'une instance de [ICLRTask](../../../ocs/framework/unmanaged-api/hosting/iclrtask-interface.md).|  
|ThreadID|`typedef UINT_PTR ThreadID;`|corprof.h|L'identificateur d'un thread managé.|  
  
## Voir aussi  
 [Référence des API non managées](../../../docs/framework/unmanaged-api/index.md)