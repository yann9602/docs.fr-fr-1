---
title: "Autorisation de sécurité pour la redirection de liaison d’assembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1bd25dd0444c428e000371abe494e62b258eaa63
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="14899-102">Autorisation de sécurité pour la redirection de liaison d’assembly</span><span class="sxs-lookup"><span data-stu-id="14899-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="14899-103">La redirection de liaison d’assembly explicite dans un fichier de configuration de l’application nécessite une autorisation de sécurité.</span><span class="sxs-lookup"><span data-stu-id="14899-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="14899-104">Cela s'applique à la redirection des assemblys .NET Framework et des assemblys tiers.</span><span class="sxs-lookup"><span data-stu-id="14899-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="14899-105">L’autorisation est accordée en définissant le <xref:System.Security.Permissions.SecurityPermissionFlag> indicateur sur le <xref:System.Security.Permissions.SecurityPermission>.</span><span class="sxs-lookup"><span data-stu-id="14899-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="14899-106">Les assemblys managés ne possèdent aucuns autorisations par défaut.</span><span class="sxs-lookup"><span data-stu-id="14899-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="14899-107">L’autorisation de sécurité est accordée aux applications en cours d’exécution dans la Zone de confiance (ordinateur local) et de la Zone Intranet.</span><span class="sxs-lookup"><span data-stu-id="14899-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="14899-108">Applications en cours d’exécution dans la Zone Internet sont strictement interdite d’effectuer la redirection de liaison d’assembly.</span><span class="sxs-lookup"><span data-stu-id="14899-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="14899-109">L’autorisation n’est pas nécessaire si la redirection d’assembly est exécutée dans un fichier de stratégie d’éditeur qui est contrôlé par l’éditeur de composant, ou dans le fichier de configuration d’ordinateur qui est contrôlé par l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="14899-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="14899-110">Toutefois, l’autorisation est nécessaire pour une application ignore explicitement la stratégie du serveur de publication à l’aide du [ \<publisherPolicy appliquer = « no » / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) élément dans le fichier de configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="14899-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="14899-111">Le tableau suivant présente la valeur par défaut des paramètres de sécurité pour le **BindingRedirects** indicateur.</span><span class="sxs-lookup"><span data-stu-id="14899-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="14899-112">Zone</span><span class="sxs-lookup"><span data-stu-id="14899-112">Zone</span></span>|<span data-ttu-id="14899-113">Paramètre d’indicateur BindingRedirects</span><span class="sxs-lookup"><span data-stu-id="14899-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="14899-114">Zone de confiance (ordinateur local)</span><span class="sxs-lookup"><span data-stu-id="14899-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="14899-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="14899-115">**ON**</span></span>|  
|<span data-ttu-id="14899-116">Zone intranet</span><span class="sxs-lookup"><span data-stu-id="14899-116">Intranet Zone</span></span>|<span data-ttu-id="14899-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="14899-117">**ON**</span></span>|  
|<span data-ttu-id="14899-118">Zone Internet</span><span class="sxs-lookup"><span data-stu-id="14899-118">Internet Zone</span></span>|<span data-ttu-id="14899-119">**DÉSACTIVÉ**</span><span class="sxs-lookup"><span data-stu-id="14899-119">**OFF**</span></span>|  
|<span data-ttu-id="14899-120">Zones non fiables</span><span class="sxs-lookup"><span data-stu-id="14899-120">Untrusted zones</span></span>|<span data-ttu-id="14899-121">**DÉSACTIVÉ**</span><span class="sxs-lookup"><span data-stu-id="14899-121">**OFF**</span></span>|  
  
 <span data-ttu-id="14899-122">Un administrateur peut modifier ces paramètres de sécurité pour prendre en charge ou restreindre des scénarios spécifiques sur un ordinateur donné.</span><span class="sxs-lookup"><span data-stu-id="14899-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="14899-123">Aucun outil permettant de modifier le **BindingRedirects** indicateur de définition à partir de la valeur par défaut ; un administrateur doit modifier manuellement le fichier Security.config sur l’ordinateur d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="14899-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14899-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14899-124">See Also</span></span>  
 [<span data-ttu-id="14899-125">Fichiers de stratégie d’éditeur et de l’exécution de côte à côte</span><span class="sxs-lookup"><span data-stu-id="14899-125">Publisher Policy Files and Side-by-Side Execution</span></span>](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [<span data-ttu-id="14899-126">Comment : activer et désactiver la redirection de liaison automatique</span><span class="sxs-lookup"><span data-stu-id="14899-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [<span data-ttu-id="14899-127">Exécution côte à côte</span><span class="sxs-lookup"><span data-stu-id="14899-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
