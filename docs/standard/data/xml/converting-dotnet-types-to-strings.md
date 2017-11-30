---
title: "Conversion de types .NET Framework en chaînes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c3abe140e62f112a15a1ad1b1b2a79c14364b26d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="e0b94-102">Conversion de types .NET Framework en chaînes</span><span class="sxs-lookup"><span data-stu-id="e0b94-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="e0b94-103">Si vous souhaitez convertir un type .NET Framework en chaîne, utilisez la **ToString** (méthode).</span><span class="sxs-lookup"><span data-stu-id="e0b94-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="e0b94-104">Le **ToString** méthode retourne une représentation sous forme de chaîne du type passé dans.</span><span class="sxs-lookup"><span data-stu-id="e0b94-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="e0b94-105">Le tableau suivant répertorie les types .NET Framework qui retournent une chaîne dans un format qui mappe aux spécifications de schéma XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="e0b94-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="e0b94-106">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0b94-106">.NET Framework type</span></span>|<span data-ttu-id="e0b94-107">Type de chaîne de retour</span><span class="sxs-lookup"><span data-stu-id="e0b94-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="e0b94-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0b94-108">Boolean</span></span>|<span data-ttu-id="e0b94-109">"true", "false"</span><span class="sxs-lookup"><span data-stu-id="e0b94-109">"true", "false"</span></span>|  
|<span data-ttu-id="e0b94-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="e0b94-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="e0b94-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="e0b94-111">"INF"</span></span>|  
|<span data-ttu-id="e0b94-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="e0b94-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="e0b94-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="e0b94-113">"-INF"</span></span>|  
|<span data-ttu-id="e0b94-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="e0b94-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="e0b94-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="e0b94-115">"INF"</span></span>|  
|<span data-ttu-id="e0b94-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="e0b94-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="e0b94-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="e0b94-117">"-INF"</span></span>|  
|<span data-ttu-id="e0b94-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0b94-118">DateTime</span></span>|<span data-ttu-id="e0b94-119">Le format est yyyy-MM-ddTHH:mm:sszzzzzz et ses sous-ensembles.</span><span class="sxs-lookup"><span data-stu-id="e0b94-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="e0b94-120">TimeSpan</span><span class="sxs-lookup"><span data-stu-id="e0b94-120">Timespan</span></span>|<span data-ttu-id="e0b94-121">Le format est PnYnMnTnHnMnS. Par exemple, `P2Y10M15DT10H30M20S` est la durée de 2 années, 10 mois, 15 jours, 10 heures, 30 minutes et 20 secondes.</span><span class="sxs-lookup"><span data-stu-id="e0b94-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0b94-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0b94-122">See Also</span></span>  
 [<span data-ttu-id="e0b94-123">Conversion de Types de données XML</span><span class="sxs-lookup"><span data-stu-id="e0b94-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="e0b94-124">Conversion de chaînes en Types de données .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0b94-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
