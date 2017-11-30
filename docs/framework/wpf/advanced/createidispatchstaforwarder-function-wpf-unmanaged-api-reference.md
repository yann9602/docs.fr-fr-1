---
title: "CreateIDispatchSTAForwarder (fonction) (référence des API non managées WPF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>CreateIDispatchSTAForwarder (fonction) (référence des API non managées WPF)
Cette API prend en charge l’infrastructure de Windows Presentation Foundation (WPF) et n’est pas destinée à être utilisée directement depuis votre code.  
  
 Utilisée par l’infrastructure de Windows Presentation Foundation (WPF) pour la gestion des threads et de windows.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a>Paramètres  
  
## <a name="property-valuereturn-value"></a>Valeur de propriété/valeur de retour  
 pDispatchDelegate  
 Un pointeur vers un `IDispatch` interface.  
  
 ppForwarder  
 Un pointeur vers l’adresse d’un `IDispatch` interface.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [configuration système requise du .NET Framework](../../../../docs/framework/get-started/system-requirements.md).  
  
 **DLL :**  
  
 Dans le .NET Framework 3.0 et 3.5 : PresentationHostDLL.dll  
  
 Dans le .NET Framework 4 et versions ultérieures : PresentationHost_v0400.dll  
  
 **Version du .NET framework :**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des API non managées WPF](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
