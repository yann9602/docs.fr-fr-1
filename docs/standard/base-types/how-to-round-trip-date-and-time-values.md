---
title: 'Comment : effectuer un aller-retour de valeurs de date et d''heure'
ms.custom: 
ms.date: 03/30/2017
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
- round-trip date and time values
- dates [.NET Framework], round-trip values
- time zones [.NET Framework], round-trip date and time values
- time [.NET Framework], round-trip values
- formatting strings [.NET Framework], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 515a29e279cfa8fc100e0612fc19df7abc6a3b36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="3d048-102">Comment : effectuer un aller-retour de valeurs de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="3d048-102">How to: Round-trip Date and Time Values</span></span>
<span data-ttu-id="3d048-103">Dans de nombreuses applications, une valeur de date et d’heure est destinée à identifier clairement un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="3d048-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="3d048-104">Cette rubrique montre comment enregistrer et restaurer un <xref:System.DateTime> valeur, un <xref:System.DateTimeOffset> valeur et une valeur de date et d’heure avec le temps de zone d’informations afin que la valeur restaurée identifie le même temps que la valeur enregistrée.</span><span class="sxs-lookup"><span data-stu-id="3d048-104">This topic shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>  
  
### <a name="to-round-trip-a-datetime-value"></a><span data-ttu-id="3d048-105">Pour effectuer un aller-retour d’une valeur DateTime</span><span class="sxs-lookup"><span data-stu-id="3d048-105">To round-trip a DateTime value</span></span>  
  
1.  <span data-ttu-id="3d048-106">Convertir le <xref:System.DateTime> valeur à sa représentation sous forme de chaîne en appelant le <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> méthode avec le spécificateur de format « o ».</span><span class="sxs-lookup"><span data-stu-id="3d048-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="3d048-107">Enregistrer la représentation sous forme de chaîne de la <xref:System.DateTime> valeur dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3d048-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="3d048-108">Récupérer la chaîne qui représente le <xref:System.DateTime> valeur.</span><span class="sxs-lookup"><span data-stu-id="3d048-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>  
  
4.  <span data-ttu-id="3d048-109">Appelez le <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> (méthode) et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> comme valeur de le `styles` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3d048-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="3d048-110">L’exemple suivant montre comment effectuer un aller-retour d’une <xref:System.DateTime> valeur.</span><span class="sxs-lookup"><span data-stu-id="3d048-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
 [!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]  
  
 <span data-ttu-id="3d048-111">Lors de l’aller-retour un <xref:System.DateTime> valeur, cette technique conserve l’heure à tout moment locaux et universels.</span><span class="sxs-lookup"><span data-stu-id="3d048-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="3d048-112">Par exemple, si une variable locale <xref:System.DateTime> valeur est enregistrée sur un système aux États-Unis. Pacifique (États-Unis) et qu’elle est restaurée sur un système situé dans le fuseau horaire Centre (États-Unis), la date et l’heure restaurées ont deux heures de retard par rapport à l’heure d’origine, ce qui reflète le décalage horaire entre ces deux fuseaux horaires.</span><span class="sxs-lookup"><span data-stu-id="3d048-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="3d048-113">En revanche, cette technique n’est pas nécessairement exacte pour les heures non spécifiées.</span><span class="sxs-lookup"><span data-stu-id="3d048-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="3d048-114">Tous les <xref:System.DateTime> dont les valeurs <xref:System.DateTime.Kind%2A> propriété <xref:System.DateTimeKind.Unspecified> sont traités comme s’ils sont locales.</span><span class="sxs-lookup"><span data-stu-id="3d048-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="3d048-115">Si ce n’est pas le cas, le <xref:System.DateTime> identifiera pas le point correct dans le temps.</span><span class="sxs-lookup"><span data-stu-id="3d048-115">If this is not the case, the <xref:System.DateTime> will not successfully identify the correct point in time.</span></span> <span data-ttu-id="3d048-116">La solution pour contourner cette limitation consiste à associer étroitement une valeur de date et d’heure avec son fuseau horaire pour l’opération d’enregistrement et de restauration.</span><span class="sxs-lookup"><span data-stu-id="3d048-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>  
  
### <a name="to-round-trip-a-datetimeoffset-value"></a><span data-ttu-id="3d048-117">Pour effectuer un aller-retour d’une valeur DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="3d048-117">To round-trip a DateTimeOffset value</span></span>  
  
1.  <span data-ttu-id="3d048-118">Convertir le <xref:System.DateTimeOffset> valeur à sa représentation sous forme de chaîne en appelant le <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> méthode avec le spécificateur de format « o ».</span><span class="sxs-lookup"><span data-stu-id="3d048-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>  
  
2.  <span data-ttu-id="3d048-119">Enregistrer la représentation sous forme de chaîne de la <xref:System.DateTimeOffset> valeur dans un fichier ou passez-la dans un processus, un domaine d’application ou une limite d’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3d048-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>  
  
3.  <span data-ttu-id="3d048-120">Récupérer la chaîne qui représente le <xref:System.DateTimeOffset> valeur.</span><span class="sxs-lookup"><span data-stu-id="3d048-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>  
  
4.  <span data-ttu-id="3d048-121">Appelez le <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> (méthode) et passez <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> comme valeur de le `styles` paramètre.</span><span class="sxs-lookup"><span data-stu-id="3d048-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>  
  
 <span data-ttu-id="3d048-122">L’exemple suivant montre comment effectuer un aller-retour d’une <xref:System.DateTimeOffset> valeur.</span><span class="sxs-lookup"><span data-stu-id="3d048-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
 [!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]  
  
 <span data-ttu-id="3d048-123">Cette technique identifie toujours clairement un <xref:System.DateTimeOffset> valeur comme un point unique dans le temps.</span><span class="sxs-lookup"><span data-stu-id="3d048-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="3d048-124">La valeur peut ensuite être convertie en temps universel coordonné (UTC), en appelant le <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> (méthode), ou il peut être convertie en heure d’un fuseau horaire particulier en appelant le <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> ou <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3d048-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3d048-125">La limitation majeure de cette technique est que la date et l’heure arithmétiques, lorsqu’un <xref:System.DateTimeOffset> valeur qui représente l’heure dans un fuseau horaire particulier, peut ne pas produire des résultats précis pour ce fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3d048-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="3d048-126">C’est parce que lorsqu’un <xref:System.DateTimeOffset> valeur est instanciée, il est dissocié de son fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3d048-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="3d048-127">Ainsi, les règles d’ajustement de ce fuseau horaire ne sont plus applicables quand vous effectuez des calculs de date et d’heure.</span><span class="sxs-lookup"><span data-stu-id="3d048-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="3d048-128">Vous pouvez contourner ce problème en définissant un type personnalisé qui inclut à la fois une valeur de date et heure et son fuseau horaire correspondant.</span><span class="sxs-lookup"><span data-stu-id="3d048-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>  
  
### <a name="to-round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="3d048-129">Pour effectuer un aller-retour d’une valeur de date et d’heure avec son fuseau horaire</span><span class="sxs-lookup"><span data-stu-id="3d048-129">To round-trip a date and time value with its time zone</span></span>  
  
1.  <span data-ttu-id="3d048-130">Définissez une classe ou une structure avec deux champs.</span><span class="sxs-lookup"><span data-stu-id="3d048-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="3d048-131">Le premier champ est un <xref:System.DateTime> ou un <xref:System.DateTimeOffset> objet et le second est un <xref:System.TimeZoneInfo> objet.</span><span class="sxs-lookup"><span data-stu-id="3d048-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="3d048-132">L’exemple suivant est une version simple d’un tel type.</span><span class="sxs-lookup"><span data-stu-id="3d048-132">The following example is a simple version of such a type.</span></span>  
  
     [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
     [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]  
  
2.  <span data-ttu-id="3d048-133">Marquez la classe avec le <xref:System.SerializableAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="3d048-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="3d048-134">Sérialiser l’objet en utilisant la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3d048-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>  
  
4.  <span data-ttu-id="3d048-135">Restaurer l’objet en utilisant la <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="3d048-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>  
  
5.  <span data-ttu-id="3d048-136">Effectuez un cast (en c#) ou convertir (en Visual Basic) l’objet désérialisé en un objet du type approprié.</span><span class="sxs-lookup"><span data-stu-id="3d048-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>  
  
 <span data-ttu-id="3d048-137">L’exemple suivant illustre comment effectuer un aller-retour un objet qui stocke les informations de date et heure et fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3d048-137">The following example illustrates how to round-trip an object that stores both date and time and time zone information.</span></span>  
  
 [!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
 [!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]  
  
 <span data-ttu-id="3d048-138">Cette technique doit toujours refléter clairement le point correct d’exécution à la fois avant et après qu’il est enregistré et restauré, que l’implémentation de l’objet de fuseau horaire et l’heure et date combinée n’autorise pas la valeur de date devenir désynchronisés avec le valeur de fuseau horaire.</span><span class="sxs-lookup"><span data-stu-id="3d048-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d048-139">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3d048-139">Compiling the Code</span></span>  
 <span data-ttu-id="3d048-140">Ces exemples nécessitent :</span><span class="sxs-lookup"><span data-stu-id="3d048-140">These examples require:</span></span>  
  
-   <span data-ttu-id="3d048-141">Que les espaces de noms suivant importés avec c# `using` instructions ou [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` instructions :</span><span class="sxs-lookup"><span data-stu-id="3d048-141">That the following namespaces be imported with C# `using` statements or [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] `Imports` statements:</span></span>  
  
    -   <span data-ttu-id="3d048-142"><xref:System>(C# uniquement).</span><span class="sxs-lookup"><span data-stu-id="3d048-142"><xref:System> (C# only).</span></span>  
  
    -   <span data-ttu-id="3d048-143"><xref:System.Globalization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d048-143"><xref:System.Globalization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="3d048-144"><xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d048-144"><xref:System.IO?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="3d048-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d048-145"><xref:System.Runtime.Serialization?displayProperty=nameWithType>.</span></span>  
  
    -   <span data-ttu-id="3d048-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3d048-146"><xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="3d048-147">Une référence à System.Core.dll.</span><span class="sxs-lookup"><span data-stu-id="3d048-147">A reference to System.Core.dll.</span></span>  
  
-   <span data-ttu-id="3d048-148">Chaque exemple de code, autre que le `DateInTimeZone` (classe), doit être inclus dans une classe ou un module Visual Basic, encapsulé dans des méthodes et appelé à partir de la `Main` (méthode).</span><span class="sxs-lookup"><span data-stu-id="3d048-148">Each code example, other than the `DateInTimeZone` class, should be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d048-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d048-149">See Also</span></span>  
 [<span data-ttu-id="3d048-150">Exécution d’opérations de mise en forme</span><span class="sxs-lookup"><span data-stu-id="3d048-150">Performing Formatting Operations</span></span>](../../../docs/standard/base-types/performing-formatting-operations.md)  
 [<span data-ttu-id="3d048-151">Choisir entre DateTime, DateTimeOffset, TimeSpan et TimeZoneInfo</span><span class="sxs-lookup"><span data-stu-id="3d048-151">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../../../docs/standard/datetime/choosing-between-datetime.md)  
 [<span data-ttu-id="3d048-152">Standard Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="3d048-152">Standard Date and Time Format Strings</span></span>](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
