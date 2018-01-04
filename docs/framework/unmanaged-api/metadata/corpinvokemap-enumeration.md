---
title: "CorPinvokeMap, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e0771ce54e7e2973525bfcf4aba4c1f7ddf0a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap, énumération
Spécifie les options pour un appel PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pmNoMangle`|Utiliser chaque nom de membre spécifié.|  
|`pmCharSetMask`|Réservé.|  
|`pmCharSetNotSpec`|Réservé.|  
|`pmCharSetAnsi`|Marshaler des chaînes en tant que chaînes de caractères de plusieurs octets.|  
|`pmCharSetUnicode`|Marshaler des chaînes en tant que caractères Unicode 2 octets.|  
|`pmCharSetAuto`|Marshaler des chaînes de manière appropriée pour le système d’exploitation cible automatiquement. La valeur par défaut est Unicode sur Windows NT, Windows 2000, Windows XP et la famille Windows Server 2003. la valeur par défaut est ANSI sur Windows 98 et Windows Me.|  
|`pmBestFitUseAssem`|Réservé.|  
|`pmBestFitEnabled`|Effectuer le mappage ajusté des caractères Unicode qui ne disposent pas d’une correspondance exacte dans le jeu de caractères ANSI.|  
|`pmBestFitDisabled`|N’effectuez pas de mappage ajusté des caractères Unicode. Dans ce cas, tous les caractères non mappables seront remplacés par un ' ?'.|  
|`pmBestFitMask`|Réservé.|  
|`pmThrowOnUnmappableCharUseAssem`|Réservé.|  
|`pmThrowOnUnmappableCharEnabled`|Lève une exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.|  
|`pmThrowOnUnmappableCharDisabled`|Ne levez pas d’exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.|  
|`pmThrowOnUnmappableCharMask`|Réservée|  
|`pmSupportsLastError`|Permet à l’appelé d’appeler Win32 `SetLastError` fonction avant le retour de la méthode avec attributs.|  
|`pmCallConvMask`|Réservée|  
|`pmCallConvWinapi`|Utilisez la convention d’appel de plateforme par défaut. Par exemple, sur Windows, la valeur par défaut est `StdCall` et sur Windows CE .NET, il est `Cdecl`.|  
|`pmCallConvCdecl`|Utilisez le `Cdecl` convention d’appel. Dans ce cas, l’appelant nettoie la pile. Cela permet d’appeler des fonctions avec `varargs` (autrement dit, les fonctions qui acceptent un nombre variable de paramètres).|  
|`pmCallConvStdcall`|Utilisez le `StdCall` convention d’appel. Dans ce cas, l’appelé nettoie la pile. Il s’agit de la convention par défaut pour appeler des fonctions non managées dans un appel d’appel.|  
|`pmCallConvThiscall`|Utilisez le `ThisCall` convention d’appel. Dans ce cas, le premier paramètre est le `this` pointeur et est stocké dans le Registre ECX. Autres paramètres sont insérés dans la pile. Le `ThisCall` convention d’appel est utilisée pour appeler des méthodes sur des classes exportées à partir d’une DLL non managée.|  
|`pmCallConvFastcall`|Réservé.|  
|`pmMaxValue`|Réservé.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
