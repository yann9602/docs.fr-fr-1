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
ms.workload: dotnet
ms.openlocfilehash: 7960ae9972490f2363b0f6f9942e947677c7d299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="symmetricsecuritybindingelement"></a><span data-ttu-id="47e7d-102">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="47e7d-102">SymmetricSecurityBindingElement</span></span>
<span data-ttu-id="47e7d-103">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="47e7d-103">SymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47e7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47e7d-104">Syntax</span></span>  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="47e7d-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="47e7d-105">Methods</span></span>  
 <span data-ttu-id="47e7d-106">La classe SymmetricSecurityBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="47e7d-106">The SymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="47e7d-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="47e7d-107">Properties</span></span>  
 <span data-ttu-id="47e7d-108">La classe SymmetricSecurityBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e7d-108">The SymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="47e7d-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="47e7d-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="47e7d-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="47e7d-110">Data type: string</span></span>  
  
 <span data-ttu-id="47e7d-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="47e7d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e7d-112">Ordre de chiffrement et de signature des messages de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="47e7d-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="47e7d-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="47e7d-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="47e7d-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="47e7d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="47e7d-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="47e7d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="47e7d-116">Si la liaison requiert la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="47e7d-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47e7d-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="47e7d-117">Requirements</span></span>  
  
|<span data-ttu-id="47e7d-118">MOF</span><span class="sxs-lookup"><span data-stu-id="47e7d-118">MOF</span></span>|<span data-ttu-id="47e7d-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="47e7d-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="47e7d-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="47e7d-120">Namespace</span></span>|<span data-ttu-id="47e7d-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="47e7d-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="47e7d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e7d-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
