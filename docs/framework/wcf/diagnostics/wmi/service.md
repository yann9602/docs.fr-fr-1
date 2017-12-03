---
title: Service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 027366e7bf7abd285ef65da2040514b4b9908213
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="service"></a><span data-ttu-id="bff00-102">Service</span><span class="sxs-lookup"><span data-stu-id="bff00-102">Service</span></span>
<span data-ttu-id="bff00-103">Service</span><span class="sxs-lookup"><span data-stu-id="bff00-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bff00-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bff00-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bff00-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="bff00-105">Methods</span></span>  
 <span data-ttu-id="bff00-106">La classe Service ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="bff00-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bff00-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="bff00-107">Properties</span></span>  
 <span data-ttu-id="bff00-108">La classe Service a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="bff00-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="bff00-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="bff00-109">BaseAddresses</span></span>  
 <span data-ttu-id="bff00-110">Type de données : tableau de chaînes</span><span class="sxs-lookup"><span data-stu-id="bff00-110">Data type: string array</span></span>  
  
 <span data-ttu-id="bff00-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-112">Les adresses de base utilisées par le service.</span><span class="sxs-lookup"><span data-stu-id="bff00-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="bff00-113">Comportements</span><span class="sxs-lookup"><span data-stu-id="bff00-113">Behaviors</span></span>  
 <span data-ttu-id="bff00-114">Type de données : tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="bff00-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="bff00-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-116">Les comportements associés à ce service.</span><span class="sxs-lookup"><span data-stu-id="bff00-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="bff00-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="bff00-117">ConfigurationName</span></span>  
 <span data-ttu-id="bff00-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bff00-118">Data type: string</span></span>  
  
 <span data-ttu-id="bff00-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="bff00-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="bff00-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="bff00-121">CounterInstanceName</span></span>  
 <span data-ttu-id="bff00-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bff00-122">Data type: string</span></span>  
  
 <span data-ttu-id="bff00-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-124">Le nom d'instance de l'instance des compteurs de performances du service.</span><span class="sxs-lookup"><span data-stu-id="bff00-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="bff00-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="bff00-125">DistinguishedName</span></span>  
 <span data-ttu-id="bff00-126">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bff00-126">Data type: string</span></span>  
  
 <span data-ttu-id="bff00-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-128">Nom du service à cette adresse.</span><span class="sxs-lookup"><span data-stu-id="bff00-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="bff00-129">Extensions</span><span class="sxs-lookup"><span data-stu-id="bff00-129">Extensions</span></span>  
 <span data-ttu-id="bff00-130">Type de données : tableau de chaînes</span><span class="sxs-lookup"><span data-stu-id="bff00-130">Data type: string array</span></span>  
  
 <span data-ttu-id="bff00-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-132">Les contextes d'instance pour les extensions de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="bff00-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="bff00-133">Métadonnées</span><span class="sxs-lookup"><span data-stu-id="bff00-133">Metadata</span></span>  
 <span data-ttu-id="bff00-134">Type de données : tableau de chaînes</span><span class="sxs-lookup"><span data-stu-id="bff00-134">Data type: string array</span></span>  
  
 <span data-ttu-id="bff00-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-136">Les paramètres de métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="bff00-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="bff00-137">Nom</span><span class="sxs-lookup"><span data-stu-id="bff00-137">Name</span></span>  
 <span data-ttu-id="bff00-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bff00-138">Data type: string</span></span>  
  
 <span data-ttu-id="bff00-139">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-140">Le nom unique de ce service.</span><span class="sxs-lookup"><span data-stu-id="bff00-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="bff00-141">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="bff00-141">Namespace</span></span>  
 <span data-ttu-id="bff00-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="bff00-142">Data type: string</span></span>  
  
 <span data-ttu-id="bff00-143">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-144">L'espace de noms du service.</span><span class="sxs-lookup"><span data-stu-id="bff00-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="bff00-145">Opened</span><span class="sxs-lookup"><span data-stu-id="bff00-145">Opened</span></span>  
 <span data-ttu-id="bff00-146">Type de données : datetime</span><span class="sxs-lookup"><span data-stu-id="bff00-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="bff00-147">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-148">L'heure à laquelle le service a été ouvert.</span><span class="sxs-lookup"><span data-stu-id="bff00-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="bff00-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="bff00-149">OutgoingChannels</span></span>  
 <span data-ttu-id="bff00-150">Type de données : tableau de canaux</span><span class="sxs-lookup"><span data-stu-id="bff00-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="bff00-151">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-152">Les canaux qui sortent de l'instance de service.</span><span class="sxs-lookup"><span data-stu-id="bff00-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="bff00-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="bff00-153">ProcessId</span></span>  
 <span data-ttu-id="bff00-154">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="bff00-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="bff00-155">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="bff00-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bff00-156">L'ID de processus du processus qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="bff00-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bff00-157">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bff00-157">Requirements</span></span>  
  
|<span data-ttu-id="bff00-158">MOF</span><span class="sxs-lookup"><span data-stu-id="bff00-158">MOF</span></span>|<span data-ttu-id="bff00-159">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bff00-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bff00-160">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="bff00-160">Namespace</span></span>|<span data-ttu-id="bff00-161">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bff00-161">Defined in root\ServiceModel</span></span>|
