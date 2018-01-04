---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a3afb9b8cfede60c773d146f4d1728d7fe02b75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="9f3b3-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9f3b3-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="9f3b3-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9f3b3-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f3b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f3b3-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9f3b3-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9f3b3-105">Methods</span></span>  
 <span data-ttu-id="9f3b3-106">La classe XmlDictionaryReaderQuotas ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9f3b3-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9f3b3-107">Properties</span></span>  
 <span data-ttu-id="9f3b3-108">La classe XmlDictionaryReaderQuotas a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="9f3b3-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="9f3b3-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="9f3b3-109">MaxArrayLength</span></span>  
 <span data-ttu-id="9f3b3-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="9f3b3-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f3b3-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="9f3b3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f3b3-112">La longueur de tableau maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="9f3b3-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="9f3b3-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="9f3b3-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="9f3b3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f3b3-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="9f3b3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f3b3-116">Le nombre maximal d'octets autorisés retournés pour chaque lecture.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="9f3b3-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="9f3b3-117">MaxDepth</span></span>  
 <span data-ttu-id="9f3b3-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="9f3b3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f3b3-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="9f3b3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f3b3-120">Profondeur maximale de nœud imbriqué par lecture.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="9f3b3-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="9f3b3-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="9f3b3-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="9f3b3-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f3b3-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="9f3b3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f3b3-124">Le nombre maximal de caractères autorisés dans un nom de table.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="9f3b3-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="9f3b3-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="9f3b3-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="9f3b3-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="9f3b3-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="9f3b3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9f3b3-128">Nombre maximal de caractères autorisés dans un contenu d'élément XML.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f3b3-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9f3b3-129">Requirements</span></span>  
  
|<span data-ttu-id="9f3b3-130">MOF</span><span class="sxs-lookup"><span data-stu-id="9f3b3-130">MOF</span></span>|<span data-ttu-id="9f3b3-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9f3b3-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9f3b3-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="9f3b3-132">Namespace</span></span>|<span data-ttu-id="9f3b3-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9f3b3-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f3b3-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f3b3-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
