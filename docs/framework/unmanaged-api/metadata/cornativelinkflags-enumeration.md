---
title: "CorNativeLinkFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorNativeLinkFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: CorNativeLinkFlags
helpviewer_keywords: CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 09afda63959d974af71e0264ad116c20d3af1923
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="ebaa1-102">CorNativeLinkFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="ebaa1-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="ebaa1-103">Fournit des valeurs d'indicateur utilisées par l'éditeur de liens lors de la liaison du code natif.</span><span class="sxs-lookup"><span data-stu-id="ebaa1-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebaa1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ebaa1-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ebaa1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ebaa1-105">Members</span></span>  
  
|<span data-ttu-id="ebaa1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ebaa1-106">Member</span></span>|<span data-ttu-id="ebaa1-107">Description</span><span class="sxs-lookup"><span data-stu-id="ebaa1-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="ebaa1-108">Ne spécifie aucun indicateur.</span><span class="sxs-lookup"><span data-stu-id="ebaa1-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="ebaa1-109">Indique un `setLastError` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="ebaa1-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="ebaa1-110">Indique un `nomangle` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="ebaa1-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="ebaa1-111">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="ebaa1-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebaa1-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ebaa1-112">Requirements</span></span>  
 <span data-ttu-id="ebaa1-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebaa1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebaa1-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ebaa1-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ebaa1-115">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebaa1-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ebaa1-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebaa1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebaa1-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ebaa1-117">See Also</span></span>  
 [<span data-ttu-id="ebaa1-118">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="ebaa1-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
