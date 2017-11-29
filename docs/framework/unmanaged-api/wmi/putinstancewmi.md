---
title: "PutInstanceWmi (fonction) (référence des API non managées)"
description: "La fonction PutInstanceWmi crée ou met à jour une instance d’une classe existante."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: PutInstanceWmi
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: PutInstanceWmi
helpviewer_keywords: PutInstanceWmi function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7a4ffce4789fb59d84778d02b41910c974216bd
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2017
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi (fonction)
Crée ou met à jour une instance d’une classe existante. L’instance est écrit dans le référentiel WMI. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
); 
```  

## <a name="parameters"></a>Paramètres

`pInst`    
[in] Pointeur vers l’instance à être écrits.

`lFlags`   
[in] Une combinaison d’indicateurs qui affectent le comportement de cette fonction. Les valeurs suivantes sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code : 

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0 x 20000 | Si la valeur, WMI ne stocke pas les qualificateurs avec la **modifié** flavor. </br> Si ce n’est pas ensemble, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont storedwith cette instance. |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | Créer l’instance si elle n’existe pas, ou remplacer si elle existe déjà. |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | Mettre à jour l’instance. L’instance doit exister pour l’appel réussisse. |
| `WBEM_FLAG_CREATE_ONLY` | 2 | Créer l’instance. L’appel échoue si l’instance existe déjà. |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0 x 10 | L’indicateur provoque un appel semi-synchrone. |

`pCtx`  
[in] En règle générale, cette valeur est `null`. Dans le cas contraire, il est un pointeur vers un [IWbemContext](https://msdn.microsoft.com/library/aa391465(v=vs.85).aspx) instance qui peut être utilisé par le fournisseur qui fournit les classes demandées. 

`ppCallResult`  
[out] Si `null`, ce paramètre est inutilisé. Si `lFlags` contient `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec `WBEM_S_NO_ERROR`. Le `ppCallResult` paramètre reçoit un pointeur vers un nouveau [IWbemCallResult](https://msdn.microsoft.com/library/aa391425(v=vs.85).aspx) objet.

## <a name="return-value"></a>Valeur de retour

Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :

|Constante  |Valeur  |Description  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0 x 80041003 | L’utilisateur n’a pas autorisé à mettre à jour une instance de la classe spécifiée. |
| `WBEM_E_FAILED` | 0 x 80041001 | Une erreur non spécifiée s’est produite. |
| `WBEM_E_INVALID_CLASS` | 0 x 80041010 | La classe de prise en charge de cette instance n’est pas valide. |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | un `null` a été spécifié pour une propriété qui ne peut pas être `null`, tel que celui qui est marquée par un **indexé** ou **Not_Null** qualificateur. |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | L’instance spécifiée n’est pas valide. (Par exemple, l’appel `PutInstanceWmi` avec une classe retourne cette valeur.) |
| `WBEM_E_INVALID_PARAMETER` | 0 x 80041008 | Un paramètre n’est pas valide. |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | Le `WBEM_FLAG_CREATE_ONLY` indicateur a été spécifié, mais l’instance existe déjà. |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY`a été spécifié dans `lFlags`, mais l’instance n’existe pas. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Pas assez de mémoire est disponible pour terminer l’opération. |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI s’est probablement arrêté, puis redémarrez. Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau. |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | Le lien de remote procedure call (RPC) entre les processus en cours et WMI a échoué. |
| `WBEM_S_NO_ERROR` | 0 | L’appel de fonction a réussi. |
  
## <a name="remarks"></a>Remarques

Cette fonction encapsule un appel à la [IWbemServices::PutInstance](https://msdn.microsoft.com/library/aa392115(v=vs.85).aspx) (méthode).

Le `PutInstanceWmi` fonction prend en charge la création d’instances et de mise à jour des instances de classes existantes uniquement.  Selon la façon dont le `pCtx` est affectée, certaines ou toutes les propriétés de l’instance sont mis à jour. 

Lorsque l’instance vers laquelle pointe `pInst` appartient à une sous-classe, gestion de Windows appelle tous les fournisseurs de responsables pour les classes à partir de laquelle dérive la sous-classe. Tous ces fournisseurs doivent réussir pour que l’original `PutInstanceWmi` demande réussisse. Le fournisseur de prise en charge de la classe au premier plan dans la hiérarchie est appelé en premier. L’ordre d’appel continue avec la sous-classe de la classe au premier plan et se poursuit à partir du haut vers le bas jusqu'à ce que Windows Management atteigne le fournisseur pour la classe propriétaire de l’instance vers laquelle pointé `pInst`.
Gestion de Windows n’appelle pas les fournisseurs pour toutes les classes enfants d’une instance. 

Lorsqu’une application doit mettre à jour une instance qui appartient à une hiérarchie de classes, les `pInst` paramètre doit pointer vers l’instance qui contient les propriétés à modifier. Autrement dit, considérez une instance cible qui appartienne à **classeB**. Le **classeB** instance dérive **ClassA**, et **ClassA** définit la propriété **PropA**. Si une application souhaite apporter une modification à la valeur de **PropA** dans les **classeB** instance, il doit définir `pInst` à cette instance, plutôt qu’à une instance de **ClassA** .

Appel de `PutInstanceWmi` sur une instance d’une classe abstraite n’est pas autorisée.

Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).

## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** WMINet_Utils.idl  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Voir aussi  
[WMI et les compteurs de Performance (référence des API non managées)](index.md)
