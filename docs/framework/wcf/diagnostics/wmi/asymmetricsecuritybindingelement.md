---
title: AsymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bd3b6be-8f77-4927-93ae-6fa371893cca
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 104810fc24cfe7c4c6ddf7ee5ece9f16a345c80c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="asymmetricsecuritybindingelement"></a><span data-ttu-id="961cf-102">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="961cf-102">AsymmetricSecurityBindingElement</span></span>
<span data-ttu-id="961cf-103">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="961cf-103">AsymmetricSecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="961cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="961cf-104">Syntax</span></span>  
  
```  
class AsymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="961cf-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="961cf-105">Methods</span></span>  
 <span data-ttu-id="961cf-106">La classe AsymmetricSecurityBindingElement ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="961cf-106">The AsymmetricSecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="961cf-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="961cf-107">Properties</span></span>  
 <span data-ttu-id="961cf-108">La classe AsymmetricSecurityBindingElement a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="961cf-108">The AsymmetricSecurityBindingElement class has the following properties:</span></span>  
  
### <a name="messageprotectionorder"></a><span data-ttu-id="961cf-109">MessageProtectionOrder</span><span class="sxs-lookup"><span data-stu-id="961cf-109">MessageProtectionOrder</span></span>  
 <span data-ttu-id="961cf-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="961cf-110">Data type: string</span></span>  
  
 <span data-ttu-id="961cf-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="961cf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="961cf-112">Ordre de chiffrement et de signature des messages de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="961cf-112">The order of message encryption and signing for this binding.</span></span>  
  
### <a name="requiresignatureconfirmation"></a><span data-ttu-id="961cf-113">RequireSignatureConfirmation</span><span class="sxs-lookup"><span data-stu-id="961cf-113">RequireSignatureConfirmation</span></span>  
 <span data-ttu-id="961cf-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="961cf-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="961cf-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="961cf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="961cf-116">Si la liaison requiert la confirmation de signature.</span><span class="sxs-lookup"><span data-stu-id="961cf-116">Whether the binding requires signature confirmation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="961cf-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="961cf-117">Requirements</span></span>  
  
|<span data-ttu-id="961cf-118">MOF</span><span class="sxs-lookup"><span data-stu-id="961cf-118">MOF</span></span>|<span data-ttu-id="961cf-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="961cf-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="961cf-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="961cf-120">Namespace</span></span>|<span data-ttu-id="961cf-121">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="961cf-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="961cf-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="961cf-122">See Also</span></span>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
