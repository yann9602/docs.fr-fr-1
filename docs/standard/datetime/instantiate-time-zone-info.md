---
title: "Comment : instancier un objet TimeZoneInfo"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
ms.assetid: 8cb620e5-c6a6-4267-a52e-beeb73cd1a34
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: defc8c9981b8476660c9c99d20bc50142ee9dfad
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="a2c61-102">Comment : instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="a2c61-102">How to: Instantiate a TimeZoneInfo object</span></span>

<span data-ttu-id="a2c61-103">La façon la plus courante pour instancier un objet <xref:System.TimeZoneInfo> consiste à récupérer les informations le concernant à partir du registre.</span><span class="sxs-lookup"><span data-stu-id="a2c61-103">The most common way to instantiate a <xref:System.TimeZoneInfo> object is to retrieve information about it from the registry.</span></span> <span data-ttu-id="a2c61-104">Cette rubrique explique comment instancier un objet <xref:System.TimeZoneInfo> à partir du registre système local.</span><span class="sxs-lookup"><span data-stu-id="a2c61-104">This topic discusses how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

### <a name="to-instantiate-a-timezoneinfo-object"></a><span data-ttu-id="a2c61-105">Pour instancier un objet TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="a2c61-105">To instantiate a TimeZoneInfo object</span></span>

1. <span data-ttu-id="a2c61-106">Déclarez un objet <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="a2c61-106">Declare a <xref:System.TimeZoneInfo> object.</span></span>

2. <span data-ttu-id="a2c61-107">Appelez le `static` (`Shared` en Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="a2c61-107">Call the `static` (`Shared` in Visual Basic) <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method.</span></span>

3. <span data-ttu-id="a2c61-108">Gérez toutes les exceptions levées par la méthode, en particulier l’exception <xref:System.TimeZoneNotFoundException> qui est levée si le fuseau horaire n’est pas défini dans le registre.</span><span class="sxs-lookup"><span data-stu-id="a2c61-108">Handle any exceptions thrown by the method, particularly the <xref:System.TimeZoneNotFoundException> that is thrown if the time zone is not defined in the registry.</span></span>

## <a name="example"></a><span data-ttu-id="a2c61-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2c61-109">Example</span></span>

<span data-ttu-id="a2c61-110">Le code suivant récupère un objet <xref:System.TimeZoneInfo> qui représente le fuseau horaire EST et affiche l’heure EST qui correspond à l’heure locale.</span><span class="sxs-lookup"><span data-stu-id="a2c61-110">The following code retrieves a <xref:System.TimeZoneInfo> object that represents the Eastern Standard Time zone and displays the Eastern Standard time that corresponds to the local time.</span></span>

[!code-csharp[System.TimeZone2.Concepts#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#5)]
[!code-vb[System.TimeZone2.Concepts#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#5)]

<span data-ttu-id="a2c61-111">Le <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> paramètre unique de la méthode est l’identificateur du fuseau horaire que vous souhaitez récupérer, qui correspond à l’objet <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="a2c61-111">The <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A?displayProperty=nameWithType> method's single parameter is the identifier of the time zone that you want to retrieve, which corresponds to the object's <xref:System.TimeZoneInfo.Id%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a2c61-112">L'identificateur de fuseau horaire est un champ clé qui identifie le fuseau horaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="a2c61-112">The time zone identifier is a key field that uniquely identifies the time zone.</span></span> <span data-ttu-id="a2c61-113">Alors que la plupart des clés sont relativement courtes, l'identificateur de fuseau horaire est long.</span><span class="sxs-lookup"><span data-stu-id="a2c61-113">While most keys are relatively short, the time zone identifier is comparatively long.</span></span> <span data-ttu-id="a2c61-114">Dans la plupart des cas, sa valeur correspond à la propriété <xref:System.TimeZoneInfo.StandardName%2A> d’un objet <xref:System.TimeZoneInfo> , qui est utilisée pour fournir le nom de l’heure standard du fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="a2c61-114">In most cases, its value corresponds to the <xref:System.TimeZoneInfo.StandardName%2A> property of a <xref:System.TimeZoneInfo> object, which is used to provide the name of the time zone's standard time.</span></span> <span data-ttu-id="a2c61-115">Toutefois, il existe des exceptions.</span><span class="sxs-lookup"><span data-stu-id="a2c61-115">However, there are exceptions.</span></span> <span data-ttu-id="a2c61-116">Pour vous assurer que l’identificateur fourni est valide, il est recommandé d’énumérer les fuseaux horaires disponibles sur votre système et de noter les identificateurs associés.</span><span class="sxs-lookup"><span data-stu-id="a2c61-116">The best way to make sure that you supply a valid identifier is to enumerate the time zones available on your system and note the identifiers of the time zones present on them.</span></span> <span data-ttu-id="a2c61-117">Pour voir un exemple, consultez [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span><span class="sxs-lookup"><span data-stu-id="a2c61-117">For an illustration, see [How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md).</span></span> <span data-ttu-id="a2c61-118">La rubrique [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) contient également une liste d’identificateurs de fuseau horaire sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="a2c61-118">The [Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) topic also contains a list of selected time zone identifiers.</span></span>

<span data-ttu-id="a2c61-119">Si le fuseau horaire est trouvé, la méthode renvoie son objet <xref:System.TimeZoneInfo> .</span><span class="sxs-lookup"><span data-stu-id="a2c61-119">If the time zone is found, the method returns its <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="a2c61-120">Si le fuseau horaire n’est pas trouvé, la méthode lève une exception <xref:System.TimeZoneNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="a2c61-120">If the time zone is not found, the method throws a <xref:System.TimeZoneNotFoundException>.</span></span> <span data-ttu-id="a2c61-121">Si le fuseau horaire est trouvé, mais que ses données sont endommagées ou incomplètes, la méthode lève une exception <xref:System.InvalidTimeZoneException>.</span><span class="sxs-lookup"><span data-stu-id="a2c61-121">If the time zone is found but its data is corrupted or incomplete, the method throws an <xref:System.InvalidTimeZoneException>.</span></span>

<span data-ttu-id="a2c61-122">Si votre application repose sur un fuseau horaire qui doit être présent, vous devez d’abord appeler la méthode <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> pour récupérer les informations de fuseau horaire à partir du registre.</span><span class="sxs-lookup"><span data-stu-id="a2c61-122">If your application relies on a time zone that must be present, you should first call the <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> method to retrieve the time zone information from the registry.</span></span> <span data-ttu-id="a2c61-123">Si l’appel de méthode échoue, votre gestionnaire d’exceptions doit alors créer une nouvelle instance du fuseau horaire ou le recréer en désérialisant un objet <xref:System.TimeZoneInfo> sérialisé.</span><span class="sxs-lookup"><span data-stu-id="a2c61-123">If the method call fails, your exception handler should then either create a new instance of the time zone or re-create it by deserializing a serialized <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="a2c61-124">Consultez [Comment : restaurer des fuseaux horaires dans une ressource incorporée](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) pour obtenir un exemple.</span><span class="sxs-lookup"><span data-stu-id="a2c61-124">See [How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) for an example.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2c61-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c61-125">See also</span></span>

<span data-ttu-id="a2c61-126">[Dates, heures et fuseaux horaires](../../../docs/standard/datetime/index.md)
[recherche des fuseaux horaires définis sur un système local](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[Comment : accéder aux objets de zone prédéfinis UTC et l’heure locale](../../../docs/standard/datetime/access-utc-and-local.md)</span><span class="sxs-lookup"><span data-stu-id="a2c61-126">[Dates, times, and time zones](../../../docs/standard/datetime/index.md)
[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md)</span></span>
