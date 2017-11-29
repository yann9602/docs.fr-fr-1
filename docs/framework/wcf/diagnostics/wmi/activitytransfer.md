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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="activitytransfer"></a><span data-ttu-id="82e58-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="82e58-102">ActivityTransfer</span></span>
<span data-ttu-id="82e58-103">Événement du transfert de l'activité</span><span class="sxs-lookup"><span data-stu-id="82e58-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e58-104">Syntax</span></span>  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="82e58-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="82e58-105">Methods</span></span>  
 <span data-ttu-id="82e58-106">La classe ActivityTransfer ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="82e58-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="82e58-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="82e58-107">Properties</span></span>  
 <span data-ttu-id="82e58-108">La classe ActivityTransfer a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="82e58-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="82e58-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="82e58-109">ActivityID</span></span>  
  
-   <span data-ttu-id="82e58-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="82e58-110">Data type: object</span></span>  
    <span data-ttu-id="82e58-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="82e58-111">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="82e58-112">ID d'activité</span><span class="sxs-lookup"><span data-stu-id="82e58-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="82e58-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="82e58-113">RelatedActivityID</span></span>  
  
-   <span data-ttu-id="82e58-114">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="82e58-114">Data type: object</span></span>  
    <span data-ttu-id="82e58-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="82e58-115">Access type: Read-only</span></span>  
  
-   <span data-ttu-id="82e58-116">ID d'activité connexe</span><span class="sxs-lookup"><span data-stu-id="82e58-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e58-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="82e58-117">Requirements</span></span>  
  
|<span data-ttu-id="82e58-118">MOF</span><span class="sxs-lookup"><span data-stu-id="82e58-118">MOF</span></span>|<span data-ttu-id="82e58-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="82e58-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="82e58-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="82e58-120">Namespace</span></span>|<span data-ttu-id="82e58-121">Défini dans root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="82e58-121">Defined in root\ServiceModel.</span></span>|
