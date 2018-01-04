---
title: ServiceSecurityAuditBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c5809e7-5364-44ce-bc71-848be4672e2a
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ea9c04c201ff022fcea54b81a998b7020fb2a836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="servicesecurityauditbehavior"></a><span data-ttu-id="30e63-102">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="30e63-102">ServiceSecurityAuditBehavior</span></span>
<span data-ttu-id="30e63-103">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="30e63-103">ServiceSecurityAuditBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30e63-104">Syntax</span></span>  
  
```  
class ServiceSecurityAuditBehavior : Behavior  
{  
  string AuditLogLocation;  
  string MessageAuthenticationAuditLevel;  
  string ServiceAuthorizationAuditLevel;  
  boolean SuppressAuditFailure;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="30e63-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="30e63-105">Methods</span></span>  
 <span data-ttu-id="30e63-106">La classe ServiceSecurityAuditBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="30e63-106">The ServiceSecurityAuditBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30e63-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="30e63-107">Properties</span></span>  
 <span data-ttu-id="30e63-108">La classe ServiceSecurityAuditBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30e63-108">The ServiceSecurityAuditBehavior class has the following properties:</span></span>  
  
### <a name="auditloglocation"></a><span data-ttu-id="30e63-109">AuditLogLocation</span><span class="sxs-lookup"><span data-stu-id="30e63-109">AuditLogLocation</span></span>  
 <span data-ttu-id="30e63-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="30e63-110">Data type: string</span></span>  
  
 <span data-ttu-id="30e63-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="30e63-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30e63-112">Emplacement du journal d'audit.</span><span class="sxs-lookup"><span data-stu-id="30e63-112">The location of the audit log.</span></span>  
  
### <a name="messageauthenticationauditlevel"></a><span data-ttu-id="30e63-113">MessageAuthenticationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="30e63-113">MessageAuthenticationAuditLevel</span></span>  
 <span data-ttu-id="30e63-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="30e63-114">Data type: string</span></span>  
  
 <span data-ttu-id="30e63-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="30e63-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30e63-116">Type de niveau d'authentification de message utilisé pour enregistrer des événements d'audit.</span><span class="sxs-lookup"><span data-stu-id="30e63-116">The type of message authentication level that is used to log audit events.</span></span>  
  
### <a name="serviceauthorizationauditlevel"></a><span data-ttu-id="30e63-117">ServiceAuthorizationAuditLevel</span><span class="sxs-lookup"><span data-stu-id="30e63-117">ServiceAuthorizationAuditLevel</span></span>  
 <span data-ttu-id="30e63-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="30e63-118">Data type: string</span></span>  
  
 <span data-ttu-id="30e63-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="30e63-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30e63-120">Types d'événement d'autorisation enregistrés dans le journal d'audit.</span><span class="sxs-lookup"><span data-stu-id="30e63-120">The types of authorization events that are recorded in the audit log.</span></span>  
  
### <a name="suppressauditfailure"></a><span data-ttu-id="30e63-121">SuppressAuditFailure</span><span class="sxs-lookup"><span data-stu-id="30e63-121">SuppressAuditFailure</span></span>  
 <span data-ttu-id="30e63-122">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="30e63-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="30e63-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="30e63-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30e63-124">Valeur booléenne qui spécifie le comportement permettant de supprimer les erreurs d'écriture dans le journal d'audit.</span><span class="sxs-lookup"><span data-stu-id="30e63-124">A boolean value that specifies the behavior for suppressing failures of writing to the audit log.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e63-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="30e63-125">Requirements</span></span>  
  
|<span data-ttu-id="30e63-126">MOF</span><span class="sxs-lookup"><span data-stu-id="30e63-126">MOF</span></span>|<span data-ttu-id="30e63-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="30e63-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30e63-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="30e63-128">Namespace</span></span>|<span data-ttu-id="30e63-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30e63-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30e63-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30e63-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
