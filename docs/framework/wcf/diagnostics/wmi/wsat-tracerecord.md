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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3966311bc10b5ad2ee401ef9e3e13c8f36e14505
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="43650-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="43650-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="43650-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="43650-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43650-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43650-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="43650-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="43650-105">Methods</span></span>  
 <span data-ttu-id="43650-106">La classe WSAT_TraceRecord ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="43650-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43650-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="43650-107">Properties</span></span>  
 <span data-ttu-id="43650-108">La classe WSAT_TraceRecord a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="43650-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="43650-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="43650-109">ActivityID</span></span>  
 <span data-ttu-id="43650-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="43650-110">Data type: object</span></span>  
<span data-ttu-id="43650-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="43650-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43650-112">ID d'activité de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="43650-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="43650-113">EventID</span><span class="sxs-lookup"><span data-stu-id="43650-113">EventID</span></span>  
 <span data-ttu-id="43650-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="43650-114">Data type: sint32</span></span>  
<span data-ttu-id="43650-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="43650-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43650-116">ID d'événement de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="43650-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="43650-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="43650-117">TraceRecord</span></span>  
 <span data-ttu-id="43650-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="43650-118">Data type: string</span></span>  
<span data-ttu-id="43650-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="43650-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43650-120">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="43650-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43650-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="43650-121">Requirements</span></span>  
  
|<span data-ttu-id="43650-122">MOF</span><span class="sxs-lookup"><span data-stu-id="43650-122">MOF</span></span>|<span data-ttu-id="43650-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="43650-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="43650-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="43650-124">Namespace</span></span>|<span data-ttu-id="43650-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="43650-125">Defined in root\ServiceModel</span></span>|
