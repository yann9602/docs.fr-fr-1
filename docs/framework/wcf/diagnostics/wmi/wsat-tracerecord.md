---
title: WSAT_TraceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24f74d4086a5499d3bfd4ef6183d377528acc21
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="ce1d6-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce1d6-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="ce1d6-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce1d6-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce1d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce1d6-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ce1d6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ce1d6-105">Methods</span></span>  
 <span data-ttu-id="ce1d6-106">La classe WSAT_TraceRecord ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ce1d6-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ce1d6-107">Properties</span></span>  
 <span data-ttu-id="ce1d6-108">La classe WSAT_TraceRecord a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="ce1d6-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="ce1d6-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="ce1d6-109">ActivityID</span></span>  
 <span data-ttu-id="ce1d6-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="ce1d6-110">Data type: object</span></span>  
<span data-ttu-id="ce1d6-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce1d6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce1d6-112">ID d'activité de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="ce1d6-113">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="ce1d6-113">EventID</span></span>  
 <span data-ttu-id="ce1d6-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="ce1d6-114">Data type: sint32</span></span>  
<span data-ttu-id="ce1d6-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce1d6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce1d6-116">ID d'événement de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="ce1d6-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="ce1d6-117">TraceRecord</span></span>  
 <span data-ttu-id="ce1d6-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="ce1d6-118">Data type: string</span></span>  
<span data-ttu-id="ce1d6-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ce1d6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ce1d6-120">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="ce1d6-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce1d6-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ce1d6-121">Requirements</span></span>  
  
|<span data-ttu-id="ce1d6-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ce1d6-122">MOF</span></span>|<span data-ttu-id="ce1d6-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ce1d6-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ce1d6-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ce1d6-124">Namespace</span></span>|<span data-ttu-id="ce1d6-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ce1d6-125">Defined in root\ServiceModel</span></span>|
