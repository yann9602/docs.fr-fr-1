---
title: ISymUnmanagedVariable, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable
helpviewer_keywords: ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: 704c69ba-77bc-40d7-8c0c-400061686321
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c32d5b66c575a21b4d390cff560b71f93aa31927
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedvariable-interface"></a><span data-ttu-id="59f1c-102">ISymUnmanagedVariable, interface</span><span class="sxs-lookup"><span data-stu-id="59f1c-102">ISymUnmanagedVariable Interface</span></span>
<span data-ttu-id="59f1c-103">Représente une variable, comme un paramètre, une variable locale ou un champ.</span><span class="sxs-lookup"><span data-stu-id="59f1c-103">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59f1c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="59f1c-104">Methods</span></span>  
  
|<span data-ttu-id="59f1c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="59f1c-105">Method</span></span>|<span data-ttu-id="59f1c-106">Description</span><span class="sxs-lookup"><span data-stu-id="59f1c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="59f1c-107">GetAddressField1 (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-107">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)|<span data-ttu-id="59f1c-108">Obtient le premier champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-108">Gets the first address field for this variable.</span></span> <span data-ttu-id="59f1c-109">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="59f1c-109">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59f1c-110">GetAddressField2 (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-110">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)|<span data-ttu-id="59f1c-111">Obtient le deuxième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-111">Gets the second address field for this variable.</span></span> <span data-ttu-id="59f1c-112">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="59f1c-112">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59f1c-113">GetAddressField3 (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-113">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)|<span data-ttu-id="59f1c-114">Obtient le troisième champ d’adresse pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-114">Gets the third address field for this variable.</span></span> <span data-ttu-id="59f1c-115">Sa signification dépend du type d’adresse.</span><span class="sxs-lookup"><span data-stu-id="59f1c-115">Its meaning depends on the kind of address.</span></span>|  
|[<span data-ttu-id="59f1c-116">GetAddressKind (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)|<span data-ttu-id="59f1c-117">Obtient le type d’adresse de cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-117">Gets the kind of address of this variable.</span></span>|  
|[<span data-ttu-id="59f1c-118">GetAttributes, méthode</span><span class="sxs-lookup"><span data-stu-id="59f1c-118">GetAttributes Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getattributes-method.md)|<span data-ttu-id="59f1c-119">Obtient les indicateurs d’attribut pour cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-119">Gets the attribute flags for this variable.</span></span>|  
|[<span data-ttu-id="59f1c-120">GetEndOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-120">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)|<span data-ttu-id="59f1c-121">Obtient l’offset de fin de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="59f1c-121">Gets the end offset of this variable within its parent.</span></span>|  
|[<span data-ttu-id="59f1c-122">GetName (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-122">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getname-method.md)|<span data-ttu-id="59f1c-123">Obtient le nom de cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-123">Gets the name of this variable.</span></span>|  
|[<span data-ttu-id="59f1c-124">GetSignature (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-124">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getsignature-method.md)|<span data-ttu-id="59f1c-125">Obtient la signature de cette variable.</span><span class="sxs-lookup"><span data-stu-id="59f1c-125">Gets the signature of this variable.</span></span>|  
|[<span data-ttu-id="59f1c-126">GetStartOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="59f1c-126">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)|<span data-ttu-id="59f1c-127">Obtient l’offset de début de cette variable dans son parent.</span><span class="sxs-lookup"><span data-stu-id="59f1c-127">Gets the start offset of this variable within its parent.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59f1c-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59f1c-128">Requirements</span></span>  
 <span data-ttu-id="59f1c-129">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="59f1c-129">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59f1c-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59f1c-130">See Also</span></span>  
 [<span data-ttu-id="59f1c-131">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="59f1c-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
