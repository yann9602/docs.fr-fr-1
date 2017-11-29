---
title: "GetPublicKeyToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink2.GetPublicKeyToken
api_location: alink.dll
api_type: COM
f1_keywords: GetPublicKeyToken
helpviewer_keywords: GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f41c8088f095802cf35239afab279d6324adb55
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="3d0b6-102">GetPublicKeyToken, méthode</span><span class="sxs-lookup"><span data-stu-id="3d0b6-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="3d0b6-103">Récupère le jeton de clé publique pour un fichier ou un conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d0b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d0b6-104">Syntax</span></span>  
  
```  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d0b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d0b6-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="3d0b6-106">Nom de fichier de la clé.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="3d0b6-107">Nom du conteneur de clé.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="3d0b6-108">Adresse où le jeton de clé doit être stocké.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="3d0b6-109">Spécifie la taille, en octets, de la mémoire tampon indiqué par `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="3d0b6-110">Au retour, contient le nombre réel d’octets utilisés.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d0b6-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3d0b6-111">Return Value</span></span>  
 <span data-ttu-id="3d0b6-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d0b6-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3d0b6-113">Requirements</span></span>  
 <span data-ttu-id="3d0b6-114">Requiert alink.h.</span><span class="sxs-lookup"><span data-stu-id="3d0b6-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d0b6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d0b6-115">See Also</span></span>  
 [<span data-ttu-id="3d0b6-116">IALink2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="3d0b6-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="3d0b6-117">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="3d0b6-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="3d0b6-118">ALink (API)</span><span class="sxs-lookup"><span data-stu-id="3d0b6-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
