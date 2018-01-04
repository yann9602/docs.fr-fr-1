---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f3db50a32fabc117c79eef5ac086a7798f86ed3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="3a282-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="3a282-102">ActivityTransfer</span></span>
<span data-ttu-id="3a282-103">Événement du transfert de l'activité</span><span class="sxs-lookup"><span data-stu-id="3a282-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a282-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a282-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3a282-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3a282-105">Methods</span></span>  
 <span data-ttu-id="3a282-106">La classe ActivityTransfer ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="3a282-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a282-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3a282-107">Properties</span></span>  
 <span data-ttu-id="3a282-108">La classe ActivityTransfer a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a282-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="3a282-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="3a282-109">ActivityID</span></span>  
  
-   <span data-ttu-id="3a282-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="3a282-110">Data type: object</span></span>  
    <span data-ttu-id="3a282-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3a282-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="3a282-112">ID d'activité</span><span class="sxs-lookup"><span data-stu-id="3a282-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="3a282-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="3a282-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="3a282-114">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="3a282-114">Data type: object</span></span>  
    <span data-ttu-id="3a282-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3a282-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="3a282-116">ID d'activité connexe</span><span class="sxs-lookup"><span data-stu-id="3a282-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a282-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3a282-117">Requirements</span></span>  
  
|<span data-ttu-id="3a282-118">MOF</span><span class="sxs-lookup"><span data-stu-id="3a282-118">MOF</span></span>|<span data-ttu-id="3a282-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3a282-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3a282-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3a282-120">Namespace</span></span>|<span data-ttu-id="3a282-121">Défini dans root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3a282-121">Defined in root\ServiceModel.</span></span>|
