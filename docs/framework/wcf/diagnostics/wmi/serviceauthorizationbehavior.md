---
title: ServiceAuthorizationBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77dad8e8-fea4-4d1c-b366-2f01a2a87f78
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 62f3e32e886f49ac8dde6af5c37a4e57373c9576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="serviceauthorizationbehavior"></a><span data-ttu-id="4aa95-102">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="4aa95-102">ServiceAuthorizationBehavior</span></span>
<span data-ttu-id="4aa95-103">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="4aa95-103">ServiceAuthorizationBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aa95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4aa95-104">Syntax</span></span>  
  
```  
class ServiceAuthorizationBehavior : Behavior  
{  
  boolean ImpersonateCallerForAllOperations;  
  string PrincipalPermissionMode;  
  string RoleProvider;  
  string ServiceAuthorizationManager;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4aa95-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="4aa95-105">Methods</span></span>  
 <span data-ttu-id="4aa95-106">La classe ServiceAuthorizationBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="4aa95-106">The ServiceAuthorizationBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4aa95-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="4aa95-107">Properties</span></span>  
 <span data-ttu-id="4aa95-108">La classe ServiceAuthorizationBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="4aa95-108">The ServiceAuthorizationBehavior class has the following properties:</span></span>  
  
### <a name="impersonatecallerforalloperations"></a><span data-ttu-id="4aa95-109">ImpersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="4aa95-109">ImpersonateCallerForAllOperations</span></span>  
 <span data-ttu-id="4aa95-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="4aa95-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="4aa95-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4aa95-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aa95-112">Valeur qui contrôle si le service essaie d'emprunter l'identité à l'aide des informations d'identification fournies par le message entrant.</span><span class="sxs-lookup"><span data-stu-id="4aa95-112">A value that controls whether the service attempts to impersonate using the credentials provided by the incoming message.</span></span>  
  
### <a name="principalpermissionmode"></a><span data-ttu-id="4aa95-113">PrincipalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="4aa95-113">PrincipalPermissionMode</span></span>  
 <span data-ttu-id="4aa95-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4aa95-114">Data type: string</span></span>  
  
 <span data-ttu-id="4aa95-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4aa95-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aa95-116">Principal de sécurité utilisée pour effectuer les opérations sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="4aa95-116">The principal used to carry out operations on the server.</span></span>  
  
### <a name="roleprovider"></a><span data-ttu-id="4aa95-117">RoleProvider</span><span class="sxs-lookup"><span data-stu-id="4aa95-117">RoleProvider</span></span>  
 <span data-ttu-id="4aa95-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4aa95-118">Data type: string</span></span>  
  
 <span data-ttu-id="4aa95-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4aa95-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aa95-120">Nom du fournisseur de rôles ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4aa95-120">The name of the ASP.NET role provider.</span></span>  
  
### <a name="serviceauthorizationmanager"></a><span data-ttu-id="4aa95-121">ServiceAuthorizationManager</span><span class="sxs-lookup"><span data-stu-id="4aa95-121">ServiceAuthorizationManager</span></span>  
 <span data-ttu-id="4aa95-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="4aa95-122">Data type: string</span></span>  
  
 <span data-ttu-id="4aa95-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="4aa95-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4aa95-124">Gestionnaire d'autorisations utilisé pour l'autorisation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4aa95-124">The authorization manager used for custom authorization.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4aa95-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4aa95-125">Requirements</span></span>  
  
|<span data-ttu-id="4aa95-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4aa95-126">MOF</span></span>|<span data-ttu-id="4aa95-127">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4aa95-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4aa95-128">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="4aa95-128">Namespace</span></span>|<span data-ttu-id="4aa95-129">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4aa95-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4aa95-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4aa95-130">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
