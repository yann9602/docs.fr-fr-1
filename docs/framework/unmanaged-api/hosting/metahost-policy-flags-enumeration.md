---
title: "METAHOST_POLICY_FLAGS, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8946fdcc7c23e11a3f3d78070532ac0bf72b33b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS, énumération
Fournit des stratégies de liaison qui sont communes à la plupart des hôtes de runtime. Cette énumération est utilisée par le [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Définit la stratégie haute compatibilité qui ne tient pas compte un common language runtime (CLR) qui est chargé dans le processus en cours. Au lieu de cela, il ne considère que les CLR installés et les préférences du composant, dérivé le fichier d’assembly, la version de génération déclarée ou le fichier de configuration.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Applique la stratégie de mise à niveau pour le résultat de la liaison version lorsqu’une correspondance exacte est introuvable, en fonction du contenu de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Cela a le même effet que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Liaison de résultats sont retournés comme si l’image fournie à l’appel a été lancée dans un nouveau processus. Actuellement, `GetRequestedRuntime` ignore le jeu de runtime chargeables et lie au jeu de runtime installés. Cet indicateur permet à un hôte déterminer à quelle exécution un EXE sera lié lorsqu’elle est lancée.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Une boîte de dialogue d’erreur s’affiche si `GetRequestedRuntime` ne peut pas trouver un runtime qui est compatible avec les paramètres d’entrée. Compter les [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], cette boîte de dialogue d’erreur peut prendre la forme d’une boîte de dialogue fonctionnalités Windows qui vous demande si l’utilisateur souhaite activer la fonctionnalité appropriée.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`utilise l’image de processus (et tout fichier de configuration correspondant) comme entrée supplémentaire au processus de liaison. Par défaut, `GetRequestedRuntime` ne tombe pas dans le chemin d’image de processus (en général, l’EXE qui a été utilisé pour lancer le processus) lors de la détermination du runtime à lier.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`doit vérifier si la référence appropriée est installée lorsque aucune information n’est disponible dans le fichier de configuration. Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut du .NET Framework. Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence appropriée est installée, sauf si l’attribut de référence (SKU) est spécifié dans le fichier de configuration `<supportedRuntime />` élément.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`doit vérifier si la référence appropriée est installée lorsque aucune information n’est disponible dans le fichier de configuration. Cela permet aux applications qui n’ont pas de fichiers de configuration d’échouer correctement sur des références plus petites que l’installation par défaut du .NET Framework. Par défaut, `GetRequestedRuntime` ne vérifie pas si la référence appropriée est installée, sauf si l’attribut de référence (SKU) est spécifié dans le fichier de configuration `<supportedRuntime />` élément.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`doit ignorer SEM_FAILCRITICALERRORS (qui est défini en appelant le [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) fonction) et afficher la boîte de dialogue d’erreur. Par défaut, SEM_FAILCRITICALERRORS supprime la boîte de dialogue d’erreur. Il peut avoir hérité à partir d’un autre processus et l’erreur en mode silencieux est peut-être pas souhaitable dans votre scénario.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Metahost.h  
  
 **Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Énumérations d’hébergement](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime (méthode)](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
