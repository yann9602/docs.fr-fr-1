---
title: "CorSerializationType, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorSerializationType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorSerializationType
helpviewer_keywords: CorSerializationType enumeration [.NET Framework metadata]
ms.assetid: 6b1fcd11-c7fb-4be2-8910-abc862d4caf4
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f6650298364f7deb60d553ee21f5028f5cbe7400
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="corserializationtype-enumeration"></a><span data-ttu-id="150a7-102">CorSerializationType, énumération</span><span class="sxs-lookup"><span data-stu-id="150a7-102">CorSerializationType Enumeration</span></span>
<span data-ttu-id="150a7-103">Spécifie la façon dont un objet est sérialisé par le common language runtime.</span><span class="sxs-lookup"><span data-stu-id="150a7-103">Specifies how an object is serialized by the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="150a7-104">Syntax</span></span>  
  
```  
typedef enum CorSerializationType {  
  
    SERIALIZATION_TYPE_UNDEFINED     = 0,  
    SERIALIZATION_TYPE_BOOLEAN       = ELEMENT_TYPE_BOOLEAN,  
    SERIALIZATION_TYPE_CHAR          = ELEMENT_TYPE_CHAR,  
    SERIALIZATION_TYPE_I1            = ELEMENT_TYPE_I1,  
    SERIALIZATION_TYPE_U1            = ELEMENT_TYPE_U1,  
    SERIALIZATION_TYPE_I2            = ELEMENT_TYPE_I2,  
    SERIALIZATION_TYPE_U2            = ELEMENT_TYPE_U2,  
    SERIALIZATION_TYPE_I4            = ELEMENT_TYPE_I4,  
    SERIALIZATION_TYPE_U4            = ELEMENT_TYPE_U4,  
    SERIALIZATION_TYPE_I8            = ELEMENT_TYPE_I8,  
    SERIALIZATION_TYPE_U8            = ELEMENT_TYPE_U8,  
    SERIALIZATION_TYPE_R4            = ELEMENT_TYPE_R4,  
    SERIALIZATION_TYPE_R8            = ELEMENT_TYPE_R8,  
    SERIALIZATION_TYPE_STRING        = ELEMENT_TYPE_STRING,  
    SERIALIZATION_TYPE_SZARRAY       = ELEMENT_TYPE_SZARRAY,  
    SERIALIZATION_TYPE_TYPE          = 0x50,  
    SERIALIZATION_TYPE_TAGGED_OBJECT = 0x51,  
    SERIALIZATION_TYPE_FIELD         = 0x53,  
    SERIALIZATION_TYPE_PROPERTY      = 0x54,  
    SERIALIZATION_TYPE_ENUM          = 0x55  
  
} CorSerializationType;  
```  
  
## <a name="members"></a><span data-ttu-id="150a7-105">Membres</span><span class="sxs-lookup"><span data-stu-id="150a7-105">Members</span></span>  
  
|<span data-ttu-id="150a7-106">Membre</span><span class="sxs-lookup"><span data-stu-id="150a7-106">Member</span></span>|<span data-ttu-id="150a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="150a7-107">Description</span></span>|  
|------------|-----------------|  
|`SERIALIZATION_TYPE_UNDEFINED`|<span data-ttu-id="150a7-108">Sérialisation de l’objet n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="150a7-108">Serialization of the object is undefined.</span></span>|  
|`SERIALIZATION_TYPE_BOOLEAN`|<span data-ttu-id="150a7-109">L’objet est sérialisé comme un type Boolean</span><span class="sxs-lookup"><span data-stu-id="150a7-109">Object is serialized as a Boolean type</span></span>|  
|`SERIALIZATION_TYPE_CHAR`|<span data-ttu-id="150a7-110">Objet est sérialisé comme un type de caractère.</span><span class="sxs-lookup"><span data-stu-id="150a7-110">Object is serialized as a character type.</span></span>|  
|`SERIALIZATION_TYPE_I1`|<span data-ttu-id="150a7-111">Objet est sérialisé comme un entier signé de 1 octet.</span><span class="sxs-lookup"><span data-stu-id="150a7-111">Object is serialized as a signed 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U1`|<span data-ttu-id="150a7-112">Objet est sérialisé en tant qu’entier non signé sur 1 octet.</span><span class="sxs-lookup"><span data-stu-id="150a7-112">Object is serialized as an unsigned 1-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I2`|<span data-ttu-id="150a7-113">Objet est sérialisé comme un entier signé de 2 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-113">Object is serialized as a signed 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U2`|<span data-ttu-id="150a7-114">Objet est sérialisé en tant qu’entier non signé de 2 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-114">Object is serialized as an unsigned 2-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I4`|<span data-ttu-id="150a7-115">Objet est sérialisé comme un entier signé de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-115">Object is serialized as a signed 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U4`|<span data-ttu-id="150a7-116">Objet est sérialisé en tant qu’entier non signé de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-116">Object is serialized as an unsigned 4-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_I8`|<span data-ttu-id="150a7-117">Objet est sérialisé comme un entier signé de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-117">Object is serialized as a signed 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_U8`|<span data-ttu-id="150a7-118">Objet est sérialisé en tant qu’entier non signé de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-118">Object is serialized as an unsigned 8-byte integer.</span></span>|  
|`SERIALIZATION_TYPE_R4`|<span data-ttu-id="150a7-119">Objet est sérialisé en tant qu’un virgule flottante de 4 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-119">Object is serialized as a 4-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_R8`|<span data-ttu-id="150a7-120">Objet est sérialisé en tant qu’une virgule flottante de 8 octets.</span><span class="sxs-lookup"><span data-stu-id="150a7-120">Object is serialized as an 8-byte floating point.</span></span>|  
|`SERIALIZATION_TYPE_STRING`|<span data-ttu-id="150a7-121">Objet est sérialisé en tant que type System.String.</span><span class="sxs-lookup"><span data-stu-id="150a7-121">Object is serialized as a System.String type.</span></span>|  
|`SERIALIZATION_TYPE_SZARRAY`|<span data-ttu-id="150a7-122">L’objet est sérialisé en tant qu’une seule dimension, un tableau de limite inférieure à zéro.</span><span class="sxs-lookup"><span data-stu-id="150a7-122">Object is serialized as a single-dimensional, zero lower-bound array.</span></span>|  
|`SERIALIZATION_TYPE_TYPE`|<span data-ttu-id="150a7-123">Objet est sérialisé comme un type générique.</span><span class="sxs-lookup"><span data-stu-id="150a7-123">Object is serialized as a generic type.</span></span>|  
|`SERIALIZATION_TYPE_TAGGED_OBJECT`|<span data-ttu-id="150a7-124">Objet est sérialisé en tant qu’objet avec balises.</span><span class="sxs-lookup"><span data-stu-id="150a7-124">Object is serialized as a tagged object.</span></span>|  
|`SERIALIZATION_TYPE_FIELD`|<span data-ttu-id="150a7-125">L’objet est sérialisé en tant que champ.</span><span class="sxs-lookup"><span data-stu-id="150a7-125">Object is serialized as a field.</span></span>|  
|`SERIALIZATION_TYPE_PROPERTY`|<span data-ttu-id="150a7-126">L’objet est sérialisé en tant que propriété.</span><span class="sxs-lookup"><span data-stu-id="150a7-126">Object is serialized as a property.</span></span>|  
|`SERIALIZATION_TYPE_ENUM`|<span data-ttu-id="150a7-127">L’objet est sérialisé en tant qu’énumération.</span><span class="sxs-lookup"><span data-stu-id="150a7-127">Object is serialized as an enumeration.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="150a7-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="150a7-128">Requirements</span></span>  
 <span data-ttu-id="150a7-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="150a7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="150a7-130">**En-tête :** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="150a7-130">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="150a7-131">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="150a7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="150a7-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="150a7-132">See Also</span></span>  
 [<span data-ttu-id="150a7-133">Énumérations de métadonnées</span><span class="sxs-lookup"><span data-stu-id="150a7-133">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
