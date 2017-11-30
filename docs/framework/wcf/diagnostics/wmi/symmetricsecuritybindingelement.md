---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="5ecb9-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5ecb9-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="5ecb9-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5ecb9-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ecb9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ecb9-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5ecb9-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5ecb9-105">Methods</span></span>  
 <span data-ttu-id="5ecb9-106">La classe SymmetricSecurityBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="5ecb9-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5ecb9-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5ecb9-107">Properties</span></span>  
 <span data-ttu-id="5ecb9-108">La classe SymmetricSecurityBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="5ecb9-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="5ecb9-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="5ecb9-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="5ecb9-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="5ecb9-110">Data type: string</span></span>  
  
 <span data-ttu-id="5ecb9-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5ecb9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5ecb9-112">Ordre de chiffrement et de signature des messages de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="5ecb9-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="5ecb9-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="5ecb9-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="5ecb9-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="5ecb9-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5ecb9-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="5ecb9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5ecb9-116">Si la liaison requiert la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="5ecb9-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ecb9-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5ecb9-117">Requirements</span></span>  
  
|<span data-ttu-id="5ecb9-118">MOF</span><span class="sxs-lookup"><span data-stu-id="5ecb9-118">MOF</span></span>|<span data-ttu-id="5ecb9-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5ecb9-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5ecb9-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="5ecb9-120">Namespace</span></span>|<span data-ttu-id="5ecb9-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5ecb9-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ecb9-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ecb9-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
