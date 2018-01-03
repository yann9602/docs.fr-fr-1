---
title: "CorSymAddrKind, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSymAddrKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSymAddrKind
helpviewer_keywords: CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 300913f9ea89044e425f9f05856d13fa15cdc015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="corsymaddrkind-enumeration"></a><span data-ttu-id="4bc09-102">CorSymAddrKind, énumération</span><span class="sxs-lookup"><span data-stu-id="4bc09-102">CorSymAddrKind Enumeration</span></span>
<span data-ttu-id="4bc09-103">Indique le type d’adresse mémoire.</span><span class="sxs-lookup"><span data-stu-id="4bc09-103">Indicates the type of memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bc09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bc09-104">Syntax</span></span>  
  
```  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a><span data-ttu-id="4bc09-105">Membres</span><span class="sxs-lookup"><span data-stu-id="4bc09-105">Members</span></span>  
  
|<span data-ttu-id="4bc09-106">Membre</span><span class="sxs-lookup"><span data-stu-id="4bc09-106">Member</span></span>|<span data-ttu-id="4bc09-107">Description</span><span class="sxs-lookup"><span data-stu-id="4bc09-107">Description</span></span>|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|<span data-ttu-id="4bc09-108">Indique un index Microsoft intermediate language (MSIL) local variable ou un paramètre.</span><span class="sxs-lookup"><span data-stu-id="4bc09-108">Indicates a Microsoft intermediate language (MSIL) local variable or parameter index.</span></span>|  
|`ADDR_NATIVE_RVA`|<span data-ttu-id="4bc09-109">Indique une adresse virtuelle relative dans un module.</span><span class="sxs-lookup"><span data-stu-id="4bc09-109">Indicates a relative virtual address into a module.</span></span>|  
|`ADDR_NATIVE_REGISTER`|<span data-ttu-id="4bc09-110">Indique un Registre du processeur.</span><span class="sxs-lookup"><span data-stu-id="4bc09-110">Indicates a CPU register.</span></span>|  
|`ADDR_NATIVE_REGREL`|<span data-ttu-id="4bc09-111">Indique que la première adresse est un Registre et la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="4bc09-111">Indicates that the first address is a register and the second address is an offset.</span></span>|  
|`ADDR_NATIVE_OFFSET`|<span data-ttu-id="4bc09-112">Indique un décalage à partir d’une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="4bc09-112">Indicates an offset from a base address.</span></span>|  
|`ADDR_NATIVE_REGREG`|<span data-ttu-id="4bc09-113">Indique que la première adresse est la partie basse d’un Registre, et la deuxième adresse est la partie haute.</span><span class="sxs-lookup"><span data-stu-id="4bc09-113">Indicates that the first address is the low portion of a register, and the second address is the high portion.</span></span>|  
|`ADDR_NATIVE_REGSTK`|<span data-ttu-id="4bc09-114">Indique que la première adresse est la partie basse d’un Registre et la seconde est la partie haute, et le troisième est un décalage.</span><span class="sxs-lookup"><span data-stu-id="4bc09-114">Indicates that the first address is the low portion of a register, the second is the high portion, and the third is an offset.</span></span>|  
|`ADDR_NATIVE_STKREG`|<span data-ttu-id="4bc09-115">Indique que la première adresse est un Registre et le second est un décalage, et le troisième est la partie haute du Registre.</span><span class="sxs-lookup"><span data-stu-id="4bc09-115">Indicates that the first address is a register, the second is an offset, and the third is the high portion of the register.</span></span>|  
|`ADDR_BITFIELD`|<span data-ttu-id="4bc09-116">Indique que la première adresse est le début d’un champ et la deuxième adresse est la longueur de champ.</span><span class="sxs-lookup"><span data-stu-id="4bc09-116">Indicates that the first address is the start of a field and the second address is the field length.</span></span>|  
|`ADDR_NATIVE_ISECTOFFSET`|<span data-ttu-id="4bc09-117">Indique que la première adresse est la section et la deuxième adresse est un décalage.</span><span class="sxs-lookup"><span data-stu-id="4bc09-117">Indicates that the first address is the section and the second address is an offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bc09-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4bc09-118">Requirements</span></span>  
 <span data-ttu-id="4bc09-119">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4bc09-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc09-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bc09-120">See Also</span></span>  
 [<span data-ttu-id="4bc09-121">Énumérations du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="4bc09-121">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
