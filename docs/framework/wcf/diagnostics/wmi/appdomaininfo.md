---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="3b4c6-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="3b4c6-102">AppDomainInfo</span></span>
<span data-ttu-id="3b4c6-103">Informations du domaine d'application</span><span class="sxs-lookup"><span data-stu-id="3b4c6-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b4c6-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3b4c6-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3b4c6-105">Methods</span></span>  
 <span data-ttu-id="3b4c6-106">La classe AppDomainInfo ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b4c6-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3b4c6-107">Properties</span></span>  
 <span data-ttu-id="3b4c6-108">La classe AppDomainInfo a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="3b4c6-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="3b4c6-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="3b4c6-109">AppDomainId</span></span>  
 <span data-ttu-id="3b4c6-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="3b4c6-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="3b4c6-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-112">ID de l'appdomain.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="3b4c6-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="3b4c6-113">IsDefault</span></span>  
 <span data-ttu-id="3b4c6-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="3b4c6-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b4c6-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-116">Indique si l'appdomain est l'appdomain par défaut.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="3b4c6-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="3b4c6-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="3b4c6-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="3b4c6-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b4c6-119">Type d'accès : lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="3b4c6-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="3b4c6-120">Valeur qui spécifie si les messages incorrects sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="3b4c6-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="3b4c6-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="3b4c6-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="3b4c6-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b4c6-123">Type d'accès : lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="3b4c6-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="3b4c6-124">Valeur qui spécifie si les messages sont suivis au niveau du service (avant les transformations associées au chiffrement et au transport).</span><span class="sxs-lookup"><span data-stu-id="3b4c6-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="3b4c6-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="3b4c6-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="3b4c6-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="3b4c6-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3b4c6-127">Type d'accès : lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="3b4c6-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="3b4c6-128">Valeur qui spécifie si les messages sont suivis au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="3b4c6-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="3b4c6-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="3b4c6-130">Type de données : tableau TraceListener</span><span class="sxs-lookup"><span data-stu-id="3b4c6-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="3b4c6-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-132">Écouteurs de suivi de la collection qui écoutent la source de suivi System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3b4c6-133">Name</span><span class="sxs-lookup"><span data-stu-id="3b4c6-133">Name</span></span>  
 <span data-ttu-id="3b4c6-134">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="3b4c6-134">Data type: string</span></span>  
  
 <span data-ttu-id="3b4c6-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-136">Nom de l'appdomain.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="3b4c6-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="3b4c6-137">PerformanceCounters</span></span>  
 <span data-ttu-id="3b4c6-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="3b4c6-138">Data type: string</span></span>  
  
 <span data-ttu-id="3b4c6-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-140">Portée de compteurs de performance actifs dans l'appdomain.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="3b4c6-141">ProcessId</span><span class="sxs-lookup"><span data-stu-id="3b4c6-141">ProcessId</span></span>  
 <span data-ttu-id="3b4c6-142">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="3b4c6-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="3b4c6-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-144">ID de processus.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="3b4c6-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="3b4c6-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="3b4c6-146">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="3b4c6-146">Data type: string</span></span>  
  
 <span data-ttu-id="3b4c6-147">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-148">Chemin d’accès à la configuration du service.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="3b4c6-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="3b4c6-149">TraceLevel</span></span>  
 <span data-ttu-id="3b4c6-150">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="3b4c6-150">Data type: string</span></span>  
  
 <span data-ttu-id="3b4c6-151">Type d'accès : lecture/écriture</span><span class="sxs-lookup"><span data-stu-id="3b4c6-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="3b4c6-152">Niveau de suivi de la source de suivi System.Wmi.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="3b4c6-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="3b4c6-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="3b4c6-154">Type de données : tableau TraceListener</span><span class="sxs-lookup"><span data-stu-id="3b4c6-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="3b4c6-155">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="3b4c6-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b4c6-156">Collection d’écouteurs de la source de suivi System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4c6-157">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3b4c6-157">Requirements</span></span>  
  
|<span data-ttu-id="3b4c6-158">MOF</span><span class="sxs-lookup"><span data-stu-id="3b4c6-158">MOF</span></span>|<span data-ttu-id="3b4c6-159">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3b4c6-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3b4c6-160">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="3b4c6-160">Namespace</span></span>|<span data-ttu-id="3b4c6-161">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3b4c6-161">Defined in root\ServiceModel</span></span>|
