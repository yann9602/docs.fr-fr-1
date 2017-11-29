---
title: "Structures de débogage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged structures [.NET Framework], debugging
- debugging structures [.NET Framework]
- structures [.NET Framework debugging]
ms.assetid: 173ba2c2-ab34-49ae-b6a8-e5c49882bf05
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0293a20f5f735dd38b1d167ebc5057f645fa011a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="debugging-structures"></a>Structures de débogage
Cette section décrit les structures non managées utilisées par l'API de débogage.  
  
## <a name="in-this-section"></a>Dans cette section  
 [CLR_DEBUGGING_VERSION (Structure)](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-version-structure.md)  
 Définit la version du produit de CLR (Common Language Runtime) à des fins de débogage.  
  
 [CodeChunkInfo Structure1](../../../../docs/framework/unmanaged-api/debugging/codechunkinfo-structure.md)  
 Représente un bloc de code unique en mémoire.  
  
 [CorDebugBlockingObject (Structure)](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)  
 Définit un objet qui bloque un thread et la raison pour laquelle le thread est bloqué.  
  
 [Structure CorDebugEHClause](../../../../docs/framework/unmanaged-api/debugging/cordebugehclause-structure.md)  
 Représente une clause de gestion des exceptions pour un bloc spécifié de langage intermédiaire.  
  
 [CorDebugExceptionObjectStackFrame (Structure)](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Représente les informations de frame de pile provenant d'un objet Exception.  
  
 [CorDebugExceptionObjectStackFrame (Structure)](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md)  
 Mappe un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID correspondant [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md) objet.  
  
 COR_ACTIVE_FUNCTION  
 Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.  
  
 [Structure COR_ARRAY_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md)  
 Fournit des informations sur la disposition d'un objet Array en mémoire.  
  
 COR_DEBUG_IL_TO_NATIVE_MAP  
 Contient les décalages qui sont utilisés pour mapper du code MSIL (Microsoft Intermediate Language) à du code natif.  
  
 COR_DEBUG_STEP_RANGE  
 Contient les informations de décalage pour une plage de code.  
  
 [COR_FIELD (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)  
 Fournit des informations sur un champ dans un objet.  
  
 [COR_GC_REFERENCE (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)  
 Contient des informations sur un objet qui doit faire l'objet d'une récupération de mémoire.  
  
 [COR_HEAPINFO (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)  
 Fournit des informations générales sur le tas du récupérateur de mémoire, y compris s’il est ou non énumérable.  
  
 [Cor_heapobject, Structure](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)  
 Fournit des informations à propos d’un objet sur le tas managé.  
  
 COR_IL_MAP  
 Spécifie des modifications dans le décalage relatif d'une fonction.  
  
 [COR_SEGMENT (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-segment-structure.md)  
 Contient des informations sur une région de la mémoire dans le tas managé.  
  
 [COR_TYPEID (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)  
 Contient un identificateur de type.  
  
 [COR_TYPE_LAYOUT (Structure)](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 Fournit des informations sur la disposition d'un objet en mémoire.  
  
 COR_VERSION  
 Stocke le numéro de version en quatre parties du CLR (Common Language Runtime).  
  
 [StackTrace_SimpleContext (Structure)](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)  
 Fournit un contexte simple qui peut être utilisé à la place d'une structure `CONTEXT` complète.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Débogage des Coclasses](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [Fonctions statiques globales de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [Énumérations de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
