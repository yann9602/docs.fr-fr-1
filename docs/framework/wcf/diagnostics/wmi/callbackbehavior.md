---
title: CallbackBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9df9629e280a2aec6acf93773e09384e763280ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="callbackbehavior"></a><span data-ttu-id="7f02f-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="7f02f-102">CallbackBehavior</span></span>
<span data-ttu-id="7f02f-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="7f02f-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f02f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f02f-104">Syntax</span></span>  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7f02f-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7f02f-105">Methods</span></span>  
 <span data-ttu-id="7f02f-106">La classe CallbackBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="7f02f-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7f02f-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="7f02f-107">Properties</span></span>  
 <span data-ttu-id="7f02f-108">La classe CallbackBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="7f02f-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="7f02f-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="7f02f-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="7f02f-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-112">Lorsque sa valeur est « true », la session est fermée automatiquement lorsqu'un service ferme une session duplex.</span><span class="sxs-lookup"><span data-stu-id="7f02f-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="7f02f-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="7f02f-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="7f02f-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="7f02f-114">Data type: string</span></span>  
<span data-ttu-id="7f02f-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-116">Spécifie si le service prend en charge un thread, plusieurs threads ou les appels réentrants.</span><span class="sxs-lookup"><span data-stu-id="7f02f-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="7f02f-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7f02f-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="7f02f-118">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-120">Valeur qui spécifie s'il faut envoyer des données de sérialisation inconnues sur le câble.</span><span class="sxs-lookup"><span data-stu-id="7f02f-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="7f02f-121">IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="7f02f-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="7f02f-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-124">En cas d'activation, des détails au sujet des exceptions levées sur le rappel sont joints aux erreurs retournées au service.</span><span class="sxs-lookup"><span data-stu-id="7f02f-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="7f02f-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7f02f-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="7f02f-126">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-128">Nombre maximal d'éléments autorisés dans un objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="7f02f-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="7f02f-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="7f02f-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="7f02f-130">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-131">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-132">Spécifie s'il faut utiliser le contexte de synchronisation actuel pour choisir le thread d'exécution.</span><span class="sxs-lookup"><span data-stu-id="7f02f-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="7f02f-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="7f02f-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="7f02f-134">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="7f02f-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="7f02f-135">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="7f02f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f02f-136">Spécifie si le système ou l'application applique le traitement d'en-tête SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="7f02f-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f02f-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7f02f-137">Requirements</span></span>  
  
|<span data-ttu-id="7f02f-138">MOF</span><span class="sxs-lookup"><span data-stu-id="7f02f-138">MOF</span></span>|<span data-ttu-id="7f02f-139">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7f02f-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7f02f-140">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="7f02f-140">Namespace</span></span>|<span data-ttu-id="7f02f-141">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7f02f-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f02f-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f02f-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
