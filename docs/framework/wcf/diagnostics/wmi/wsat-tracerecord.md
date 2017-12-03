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
ms.openlocfilehash: b4e701c2f0d669a04be7f7235c8ab1edb8ce1612
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="wsattracerecord"></a><span data-ttu-id="3f2d0-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3f2d0-102">WSAT_TraceRecord</span></span>
<span data-ttu-id="3f2d0-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3f2d0-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f2d0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f2d0-104">Syntax</span></span>  
  
```  
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3f2d0-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f2d0-105">Methods</span></span>  
 <span data-ttu-id="3f2d0-106">La classe WSAT_TraceRecord ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="3f2d0-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3f2d0-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3f2d0-107">Properties</span></span>  
 <span data-ttu-id="3f2d0-108">La classe WSAT_TraceRecord a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3f2d0-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="3f2d0-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="3f2d0-109">ActivityID</span></span>  
 <span data-ttu-id="3f2d0-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="3f2d0-110">Data type: object</span></span>  
<span data-ttu-id="3f2d0-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3f2d0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f2d0-112">ID d'activité de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f2d0-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="3f2d0-113">EventID</span><span class="sxs-lookup"><span data-stu-id="3f2d0-113">EventID</span></span>  
 <span data-ttu-id="3f2d0-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="3f2d0-114">Data type: sint32</span></span>  
<span data-ttu-id="3f2d0-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3f2d0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f2d0-116">ID d'événement de l'enregistrement de suivi.</span><span class="sxs-lookup"><span data-stu-id="3f2d0-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="3f2d0-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="3f2d0-117">TraceRecord</span></span>  
 <span data-ttu-id="3f2d0-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="3f2d0-118">Data type: string</span></span>  
<span data-ttu-id="3f2d0-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3f2d0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3f2d0-120">Enregistrement de suivi</span><span class="sxs-lookup"><span data-stu-id="3f2d0-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f2d0-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3f2d0-121">Requirements</span></span>  
  
|<span data-ttu-id="3f2d0-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3f2d0-122">MOF</span></span>|<span data-ttu-id="3f2d0-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3f2d0-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3f2d0-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3f2d0-124">Namespace</span></span>|<span data-ttu-id="3f2d0-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3f2d0-125">Defined in root\ServiceModel</span></span>|
