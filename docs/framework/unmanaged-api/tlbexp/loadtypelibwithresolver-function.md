---
title: LoadTypeLibWithResolver, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadTypeLibWithResolver
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: LoadTypeLibWithResolver
helpviewer_keywords: LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0241745396ab01a777eef6e3b88e4c12bdd8b429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver, fonction
Charge une bibliothèque de types et utilise l’élément [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) pour résoudre toutes les bibliothèques de types référencées en interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `szFile`  
 [in] Le chemin d’accès de la bibliothèque de types.  
  
 `regkind`  
 [in] A [énumération de regkind a](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) indicateur qui contrôle comment la bibliothèque de types est enregistrée. Les valeurs possibles sont :  
  
-   `REGKIND_DEFAULT`: Utilisez le comportement de l’inscription par défaut.  
  
-   `REGKIND_REGISTER`: Inscrivez cette bibliothèque de types.  
  
-   `REGKIND_NONE`: Ne pas enregistrer cette bibliothèque de types.  
  
 `pTlbResolver`  
 [in] Un pointeur vers l’implémentation de la [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Une référence à la bibliothèque de types est chargée.  
  
## <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT répertoriés dans le tableau suivant.  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`E_POINTER`|Un ou plusieurs des pointeurs ne sont pas valides.|  
|`E_INVALIDARG`|Un ou plusieurs arguments ne sont pas valides.|  
|`TYPE_E_IOERROR`|La fonction n’a pas pu écrire dans le fichier.|  
|`TYPE_E_REGISTRYACCESS`|La base de données d’inscription système n’a pas pu être ouvert.|  
|`TYPE_E_INVALIDSTATE`|La bibliothèque de types n’a pas pu être ouvert.|  
|`TYPE_E_CANTLOADLIBRARY`|La bibliothèque de types ou de la DLL n’a pas pu être chargé.|  
  
## <a name="remarks"></a>Remarques  
 Le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) appelle la `LoadTypeLibWithResolver` fonction pendant le processus de conversion de l’assembly de bibliothèque de types.  
  
 Cette fonction charge la bibliothèque de types spécifiée avec un accès minimal au Registre. La fonction examine ensuite la bibliothèque de types pour les bibliothèques de types référencées en interne, chacune d’elles doit être chargé et ajouté à la bibliothèque de type parent.  
  
 Avant de la bibliothèque de types référencée peut être chargée, son chemin d’accès du fichier de référence doit être résolue pour un chemin d’accès complet du fichier. Cela s’effectue via le [ResolveTypeLib, méthode](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) fournie par le [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), qui est transmis dans le `pTlbResolver` paramètre.  
  
 Lorsque le chemin d’accès de fichier complet de la bibliothèque de types référencée est connu, le `LoadTypeLibWithResolver` fonction charge et ajoute la bibliothèque de types référencée à la bibliothèque de type parent, création d’une bibliothèque de types principale combinée.  
  
 Une fois que la fonction résout et charge des bibliothèques de types référencées en interne, elle retourne une référence à la bibliothèque de types résolue principale dans le `pptlib` paramètre.  
  
 Le `LoadTypeLibWithResolver` est généralement appelée le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), qui fournit sa propre interne [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) mise en œuvre dans le `pTlbResolver` paramètre.  
  
 Si vous appelez `LoadTypeLibWithResolver` directement, vous devez fournir votre propre [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implémentation.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** TlbRef.h  
  
 **Bibliothèque :** TlbRef.lib  
  
 **Version du .NET framework :** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions d’assistance Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx de le dont (fonction)](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
