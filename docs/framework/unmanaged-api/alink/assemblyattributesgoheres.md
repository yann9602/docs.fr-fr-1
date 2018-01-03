---
title: AssemblyAttributesGoHereS
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyAttributesGoHereS
api_location: alink.dll
api_type: COM
f1_keywords: AssemblyAttributesGoHereS
helpviewer_keywords:
- AssemblyAttributesGoHereS type
- Alink API, AssemblyAttributesGoHereS type
ms.assetid: 4e817f35-a2bc-4403-9e6f-f731e6b9fe23
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac8f25632521f2e8abe5209608e42632293feb4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assemblyattributesgoheres"></a>AssemblyAttributesGoHereS
Utilisé par ALink en tant qu'espace réservé pour stocker des informations sur les attributs personnalisés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
AssemblyAttributesGoHereS  
```  
  
## <a name="remarks"></a>Notes  
 Les références à ce type peuvent être incorporées dans les netmodules dont les sources contiennent des attributs personnalisés d'assembly. Quand vous générez un manifeste d'assembly à partir d'un ou plusieurs netmodules qui contiennent des références à ces types, ALink utilise les informations associées à ces références pour émettre des attributs personnalisés réels. Par conséquent, ce type n'est jamais instancié et ses références sont utilisées uniquement dans le cadre du processus de génération et n'ont aucune utilité dans l'assembly final.  
  
 Les références à ce type indiquent des attributs personnalisés qui sont liés à la sécurité et ne peuvent pas être utilisés plusieurs fois.  
  
 Ces types sont marqués comme étant « internes » dans le .NET Framework et se trouvent dans <xref:System.Runtime.CompilerServices>.  
  
## <a name="requirements"></a>Configuration requise  
 mscorlib.dll  
  
## <a name="see-also"></a>Voir aussi  
 [AssemblyAttributesGoHere](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgohere.md)  
 [AssemblyAttributesGoHereM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoherem.md)  
 [AssemblyAttributesGoHereSM](../../../../docs/framework/unmanaged-api/alink/assemblyattributesgoheresm.md)
