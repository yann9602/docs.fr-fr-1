---
title: '&lt;add&gt; de &lt;allowAccounts&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09ab06bb94249e79743335da1a360f6b668b1d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a><span data-ttu-id="541df-102">&lt;add&gt; de &lt;allowAccounts&gt;</span><span class="sxs-lookup"><span data-stu-id="541df-102">&lt;add&gt; of &lt;allowAccounts&gt;</span></span>
<span data-ttu-id="541df-103">Indique un compte d'utilisateur correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="541df-103">Specifies a user account for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>  
  
 <span data-ttu-id="541df-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="541df-104">\<system.serviceModel.activation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541df-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="541df-105">Syntax</span></span>  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="541df-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="541df-106">Attributes and Elements</span></span>  
 <span data-ttu-id="541df-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="541df-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="541df-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="541df-108">Attributes</span></span>  
  
|<span data-ttu-id="541df-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="541df-109">Attribute</span></span>|<span data-ttu-id="541df-110">Description</span><span class="sxs-lookup"><span data-stu-id="541df-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="541df-111">securityIdentifier</span><span class="sxs-lookup"><span data-stu-id="541df-111">securityIdentifier</span></span>|<span data-ttu-id="541df-112">Chaîne indiquant un identificateur unique utilisée pour identifier un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="541df-112">A string that specifies a unique identifier used to identify a user account.</span></span> <span data-ttu-id="541df-113">Les valeurs par défaut sont LocalSystem, Administrateurs, NS, LS et IIS_USRS.</span><span class="sxs-lookup"><span data-stu-id="541df-113">The default values are LocalSystem, Administrators, NS, LS, and IIS_USRS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="541df-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="541df-114">Child Elements</span></span>  
 <span data-ttu-id="541df-115">Aucun.</span><span class="sxs-lookup"><span data-stu-id="541df-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="541df-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="541df-116">Parent Elements</span></span>  
  
|<span data-ttu-id="541df-117">Élément</span><span class="sxs-lookup"><span data-stu-id="541df-117">Element</span></span>|<span data-ttu-id="541df-118">Description</span><span class="sxs-lookup"><span data-stu-id="541df-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="541df-119">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="541df-119">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="541df-120">Collection d'éléments de configuration qui contiennent un attribut `securityIdentifier` permettant de spécifier les comptes d'utilisateurs correspondant aux processus qui hébergent des services [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] et qui disposent d'un accès de connexion au service de partage.</span><span class="sxs-lookup"><span data-stu-id="541df-120">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="541df-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="541df-121">Example</span></span>  
 <span data-ttu-id="541df-122">L’exemple de configuration suivant ajoute à cette collection les cinq identificateurs par défaut correspondant aux comptes d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="541df-122">The following configuration example adds the five default identifiers for user accounts to this collection.</span></span>  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a><span data-ttu-id="541df-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="541df-123">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
