---
title: ISymUnmanagedMethod, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod
helpviewer_keywords: ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 030ea4b472f6a6aead307e0c5cc94dfb34c19992
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="d26c3-102">ISymUnmanagedMethod, interface</span><span class="sxs-lookup"><span data-stu-id="d26c3-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="d26c3-103">Représente une méthode dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="d26c3-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="d26c3-104">Cette interface fournit l’accès aux seuls les attributs liés aux symboles d’une méthode, au lieu des attributs de type.</span><span class="sxs-lookup"><span data-stu-id="d26c3-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d26c3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="d26c3-105">Methods</span></span>  
  
|<span data-ttu-id="d26c3-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="d26c3-106">Method</span></span>|<span data-ttu-id="d26c3-107">Description</span><span class="sxs-lookup"><span data-stu-id="d26c3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d26c3-108">GetNamespace (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="d26c3-109">Obtient l’espace de noms dans lequel cette méthode est définie.</span><span class="sxs-lookup"><span data-stu-id="d26c3-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="d26c3-110">GetOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="d26c3-111">Retourne l’offset dans cette méthode qui correspond à une position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="d26c3-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="d26c3-112">GetParameters (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="d26c3-113">Obtient les paramètres de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="d26c3-114">GetRanges (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="d26c3-115">Une position donnée dans un document, retourne un tableau de début et fin paires d’offsets qui correspondent aux plages de langage intermédiaire Microsoft (MSIL) qui traite de la position au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="d26c3-116">GetRootScope (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="d26c3-117">Obtient la portée lexicale racine dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="d26c3-118">Cette portée englobe la totalité de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="d26c3-119">GetScopeFromOffset (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="d26c3-120">Obtient la portée lexicale la plus englobante dans cette méthode qui englobe l’offset donné.</span><span class="sxs-lookup"><span data-stu-id="d26c3-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="d26c3-121">GetSequencePointCount (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="d26c3-122">Obtient le nombre de points de séquence au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="d26c3-123">GetSequencePoints (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="d26c3-124">Obtient tous les points de séquence au sein de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="d26c3-125">GetSourceStartEnd (méthode)</span><span class="sxs-lookup"><span data-stu-id="d26c3-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="d26c3-126">Obtient les positions de document de début et de fin de la source de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="d26c3-127">GetToken, méthode</span><span class="sxs-lookup"><span data-stu-id="d26c3-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="d26c3-128">Retourne le jeton de métadonnées pour cette méthode.</span><span class="sxs-lookup"><span data-stu-id="d26c3-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d26c3-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d26c3-129">Requirements</span></span>  
 <span data-ttu-id="d26c3-130">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d26c3-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26c3-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d26c3-131">See Also</span></span>  
 [<span data-ttu-id="d26c3-132">Interfaces du magasin de symboles de Diagnostics</span><span class="sxs-lookup"><span data-stu-id="d26c3-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
