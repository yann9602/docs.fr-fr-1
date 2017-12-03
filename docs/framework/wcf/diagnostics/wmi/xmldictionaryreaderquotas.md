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
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="907f2-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="907f2-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="907f2-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="907f2-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="907f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="907f2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="907f2-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="907f2-105">Methods</span></span>  
 <span data-ttu-id="907f2-106">La classe XmlDictionaryReaderQuotas ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="907f2-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="907f2-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="907f2-107">Properties</span></span>  
 <span data-ttu-id="907f2-108">La classe XmlDictionaryReaderQuotas a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="907f2-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="907f2-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="907f2-109">MaxArrayLength</span></span>  
 <span data-ttu-id="907f2-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="907f2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="907f2-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="907f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="907f2-112">La longueur de tableau maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="907f2-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="907f2-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="907f2-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="907f2-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="907f2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="907f2-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="907f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="907f2-116">Le nombre maximal d'octets autorisés retournés pour chaque lecture.</span><span class="sxs-lookup"><span data-stu-id="907f2-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="907f2-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="907f2-117">MaxDepth</span></span>  
 <span data-ttu-id="907f2-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="907f2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="907f2-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="907f2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="907f2-120">Profondeur maximale de nœud imbriqué par lecture.</span><span class="sxs-lookup"><span data-stu-id="907f2-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="907f2-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="907f2-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="907f2-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="907f2-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="907f2-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="907f2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="907f2-124">Le nombre maximal de caractères autorisés dans un nom de table.</span><span class="sxs-lookup"><span data-stu-id="907f2-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="907f2-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="907f2-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="907f2-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="907f2-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="907f2-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="907f2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="907f2-128">Nombre maximal de caractères autorisés dans un contenu d'élément XML.</span><span class="sxs-lookup"><span data-stu-id="907f2-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="907f2-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="907f2-129">Requirements</span></span>  
  
|<span data-ttu-id="907f2-130">MOF</span><span class="sxs-lookup"><span data-stu-id="907f2-130">MOF</span></span>|<span data-ttu-id="907f2-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="907f2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="907f2-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="907f2-132">Namespace</span></span>|<span data-ttu-id="907f2-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="907f2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="907f2-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="907f2-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
