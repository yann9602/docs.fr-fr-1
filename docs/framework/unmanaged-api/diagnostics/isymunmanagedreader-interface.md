---
title: ISymUnmanagedReader, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="ac157-102">ISymUnmanagedReader, interface</span><span class="sxs-lookup"><span data-stu-id="ac157-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="ac157-103">Représente un lecteur de symboles qui fournit l’accès aux documents, des méthodes et des variables dans un magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="ac157-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ac157-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ac157-104">Methods</span></span>  
  
|<span data-ttu-id="ac157-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-105">Method</span></span>|<span data-ttu-id="ac157-106">Description</span><span class="sxs-lookup"><span data-stu-id="ac157-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ac157-107">GetDocument, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="ac157-108">Recherche d’un document.</span><span class="sxs-lookup"><span data-stu-id="ac157-108">Finds a document.</span></span>|  
|[<span data-ttu-id="ac157-109">GetDocuments, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="ac157-110">Retourne un tableau de tous les documents définis dans le magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="ac157-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="ac157-111">GetDocumentVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="ac157-112">Obtient la version spécifiée du document spécifié.</span><span class="sxs-lookup"><span data-stu-id="ac157-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="ac157-113">GetGlobalVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="ac157-114">Retourne toutes les variables globales.</span><span class="sxs-lookup"><span data-stu-id="ac157-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="ac157-115">GetMethod, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="ac157-116">Obtient une méthode de lecteur de symboles, un jeton de méthode donné.</span><span class="sxs-lookup"><span data-stu-id="ac157-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="ac157-117">GetMethodByVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="ac157-118">Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et un numéro de version de la modifier et copier.</span><span class="sxs-lookup"><span data-stu-id="ac157-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="ac157-119">GetMethodFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="ac157-120">Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="ac157-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="ac157-121">GetMethodsFromDocumentPosition, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="ac157-122">Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.</span><span class="sxs-lookup"><span data-stu-id="ac157-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="ac157-123">GetMethodVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="ac157-124">Obtient la version de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ac157-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="ac157-125">GetNamespaces, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="ac157-126">Obtient les espaces de noms définis dans une portée globale dans ce magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="ac157-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="ac157-127">GetSymAttribute, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="ac157-128">Obtient un attribut personnalisé en fonction de son nom.</span><span class="sxs-lookup"><span data-stu-id="ac157-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="ac157-129">GetSymbolStoreFileName, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="ac157-130">Fournit le nom de fichier sur disque du magasin de symboles.</span><span class="sxs-lookup"><span data-stu-id="ac157-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="ac157-131">GetUserEntryPoint, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="ac157-132">Retourne la méthode qui a été spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="ac157-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="ac157-133">GetVariables, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="ac157-134">Retourne une variable non locale, son parent et le nom.</span><span class="sxs-lookup"><span data-stu-id="ac157-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="ac157-135">Initialize, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="ac157-136">Initialise le lecteur de symboles avec l’interface de métadonnées de l’importateur ce lecteur sera associé, ainsi que le nom de fichier du module.</span><span class="sxs-lookup"><span data-stu-id="ac157-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="ac157-137">ReplaceSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="ac157-138">Remplace le magasin de symboles existant par un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="ac157-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="ac157-139">UpdateSymbolStore, méthode</span><span class="sxs-lookup"><span data-stu-id="ac157-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="ac157-140">Met à jour le magasin de symboles existant avec un magasin de symboles delta.</span><span class="sxs-lookup"><span data-stu-id="ac157-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ac157-141">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ac157-141">Requirements</span></span>  
 <span data-ttu-id="ac157-142">**En-tête :** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ac157-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac157-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac157-143">See Also</span></span>  
 [<span data-ttu-id="ac157-144">Interfaces du magasin de symboles de diagnostics</span><span class="sxs-lookup"><span data-stu-id="ac157-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ac157-145">ISymUnmanagedReader2, interface</span><span class="sxs-lookup"><span data-stu-id="ac157-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
