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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 980a7eacd095dc1b601d63f5a807f2e287c09885
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="22739-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="22739-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="22739-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="22739-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22739-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22739-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="22739-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="22739-105">Methods</span></span>  
 <span data-ttu-id="22739-106">La classe XmlDictionaryReaderQuotas ne définit aucune méthode.</span><span class="sxs-lookup"><span data-stu-id="22739-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="22739-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="22739-107">Properties</span></span>  
 <span data-ttu-id="22739-108">La classe XmlDictionaryReaderQuotas a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="22739-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="22739-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="22739-109">MaxArrayLength</span></span>  
 <span data-ttu-id="22739-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="22739-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="22739-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="22739-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22739-112">La longueur de tableau maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="22739-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="22739-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="22739-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="22739-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="22739-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="22739-115">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="22739-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22739-116">Le nombre maximal d'octets autorisés retournés pour chaque lecture.</span><span class="sxs-lookup"><span data-stu-id="22739-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="22739-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="22739-117">MaxDepth</span></span>  
 <span data-ttu-id="22739-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="22739-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="22739-119">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="22739-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22739-120">Profondeur maximale de nœud imbriqué par lecture.</span><span class="sxs-lookup"><span data-stu-id="22739-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="22739-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="22739-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="22739-122">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="22739-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="22739-123">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="22739-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22739-124">Le nombre maximal de caractères autorisés dans un nom de table.</span><span class="sxs-lookup"><span data-stu-id="22739-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="22739-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="22739-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="22739-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="22739-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="22739-127">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="22739-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22739-128">Nombre maximal de caractères autorisés dans un contenu d'élément XML.</span><span class="sxs-lookup"><span data-stu-id="22739-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22739-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="22739-129">Requirements</span></span>  
  
|<span data-ttu-id="22739-130">MOF</span><span class="sxs-lookup"><span data-stu-id="22739-130">MOF</span></span>|<span data-ttu-id="22739-131">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="22739-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="22739-132">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="22739-132">Namespace</span></span>|<span data-ttu-id="22739-133">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="22739-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22739-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="22739-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>
