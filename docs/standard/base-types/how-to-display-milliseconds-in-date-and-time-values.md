---
title: "Comment : afficher les millisecondes dans les valeurs de date et d'heure"
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
- DateTime.ToString method
- displaying date and time data
- time [.NET Framework], milliseconds
- dates [.NET Framework], milliseconds
- milliseconds [.NET Framework]
ms.assetid: ae1a0610-90b9-4877-8eb6-4e30bc5e00cf
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 260d202eb0a218a6657bc719e36da6f39138e54e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-milliseconds-in-date-and-time-values"></a><span data-ttu-id="bc395-102">Comment : afficher les millisecondes dans les valeurs de date et d'heure</span><span class="sxs-lookup"><span data-stu-id="bc395-102">How to: Display Milliseconds in Date and Time Values</span></span>
<span data-ttu-id="bc395-103">La date par défaut et l’heure de mise en forme des méthodes, telles que <xref:System.DateTime.ToString?displayProperty=nameWithType>, incluent les heures, minutes et secondes d’une valeur d’heure, mais exclut les son composant « millisecondes ».</span><span class="sxs-lookup"><span data-stu-id="bc395-103">The default date and time formatting methods, such as <xref:System.DateTime.ToString?displayProperty=nameWithType>, include the hours, minutes, and seconds of a time value but exclude its milliseconds component.</span></span> <span data-ttu-id="bc395-104">Cette rubrique montre comment inclure le composant « millisecondes » d’une date et d’une heure dans des chaînes de date et d’heure mises en forme.</span><span class="sxs-lookup"><span data-stu-id="bc395-104">This topic shows how to include a date and time's millisecond component in formatted date and time strings.</span></span>  
  
### <a name="to-display-the-millisecond-component-of-a-datetime-value"></a><span data-ttu-id="bc395-105">Pour afficher le composant « millisecondes » d’une valeur DateTime</span><span class="sxs-lookup"><span data-stu-id="bc395-105">To display the millisecond component of a DateTime value</span></span>  
  
1.  <span data-ttu-id="bc395-106">Si la date est représentée sous forme de chaîne, convertissez-la en une valeur <xref:System.DateTime> ou <xref:System.DateTimeOffset> en utilisant la méthode <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> statique.</span><span class="sxs-lookup"><span data-stu-id="bc395-106">If you are working with the string representation of a date, convert it to a <xref:System.DateTime> or a <xref:System.DateTimeOffset> value by using the static <xref:System.DateTime.Parse%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.Parse%28System.String%29?displayProperty=nameWithType> method.</span></span>  
  
2.  <span data-ttu-id="bc395-107">Pour extraire la représentation sous forme de chaîne du composant « millisecondes » d’une heure, appelez la valeur date et d’heure <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> ou <xref:System.DateTimeOffset.ToString%2A> (méthode) et passez le `fff` ou `FFF` modèle de format personnalisé, seul ou avec d’autres format personnalisé les spécificateurs en tant que le `format` paramètre.</span><span class="sxs-lookup"><span data-stu-id="bc395-107">To extract the string representation of a time's millisecond component, call the date and time value's <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> or <xref:System.DateTimeOffset.ToString%2A> method, and pass the `fff` or `FFF` custom format pattern either alone or with other custom format specifiers as the `format` parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc395-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc395-108">Example</span></span>  
 <span data-ttu-id="bc395-109">L’exemple affiche le composant « millisecondes » d’une <xref:System.DateTime> et un <xref:System.DateTimeOffset> sur la console, seule et dans une chaîne de date et d’heure plus longue.</span><span class="sxs-lookup"><span data-stu-id="bc395-109">The example displays the millisecond component of a <xref:System.DateTime> and a <xref:System.DateTimeOffset> value to the console, both alone and included in a longer date and time string.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#1)]
 [!code-vb[Formatting.HowTo.Millisecond#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#1)]  
  
 <span data-ttu-id="bc395-110">Le modèle de format `fff` inclut les zéros de fin éventuels dans la valeur en millisecondes.</span><span class="sxs-lookup"><span data-stu-id="bc395-110">The `fff` format pattern includes any trailing zeros in the millisecond value.</span></span> <span data-ttu-id="bc395-111">Le modèle de format `FFF` les supprime.</span><span class="sxs-lookup"><span data-stu-id="bc395-111">The `FFF` format pattern suppresses them.</span></span> <span data-ttu-id="bc395-112">L’exemple suivant illustre cette différence.</span><span class="sxs-lookup"><span data-stu-id="bc395-112">The difference is illustrated in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#2)]
 [!code-vb[Formatting.HowTo.Millisecond#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#2)]  
  
 <span data-ttu-id="bc395-113">Quand vous définissez un spécificateur de format personnalisé complet qui inclut le composant « millisecondes » d’une date et d’une heure, vous pouvez être confronté au problème suivant : le format défini peut être un format codé en dur qui ne correspond pas à la disposition des éléments d’heure dans la culture actuelle de l’application.</span><span class="sxs-lookup"><span data-stu-id="bc395-113">A problem with defining a complete custom format specifier that includes the millisecond component of a date and time is that it defines a hard-coded format that may not correspond to the arrangement of time elements in the application's current culture.</span></span> <span data-ttu-id="bc395-114">Une meilleure solution consiste à récupérer une de la date et l’heure des modèles d’affichage définis par la culture actuelle <xref:System.Globalization.DateTimeFormatInfo> de l’objet et modifiez-le pour inclure les millisecondes.</span><span class="sxs-lookup"><span data-stu-id="bc395-114">A better alternative is to retrieve one of the date and time display patterns defined by the current culture's <xref:System.Globalization.DateTimeFormatInfo> object and modify it to include milliseconds.</span></span> <span data-ttu-id="bc395-115">L’exemple illustre également cette approche.</span><span class="sxs-lookup"><span data-stu-id="bc395-115">The example also illustrates this approach.</span></span> <span data-ttu-id="bc395-116">Il récupère de la culture actuelle complète modèle de date et heure à partir de la <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> propriété, puis insère le modèle personnalisé `.ffff` après son deuxième modèle.</span><span class="sxs-lookup"><span data-stu-id="bc395-116">It retrieves the current culture's full date and time pattern from the <xref:System.Globalization.DateTimeFormatInfo.FullDateTimePattern%2A?displayProperty=nameWithType> property, and then inserts the custom pattern `.ffff` after its seconds pattern.</span></span> <span data-ttu-id="bc395-117">Notez que l’exemple utilise une expression régulière pour effectuer cette opération dans un seul appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="bc395-117">Note that the example uses a regular expression to perform this operation in a single method call.</span></span>  
  
 <span data-ttu-id="bc395-118">Vous pouvez également utiliser un spécificateur de format personnalisé pour afficher une partie fractionnaire des secondes autre que les millisecondes.</span><span class="sxs-lookup"><span data-stu-id="bc395-118">You can also use a custom format specifier to display a fractional part of seconds other than milliseconds.</span></span> <span data-ttu-id="bc395-119">Par exemple, le spécificateur de format personnalisé `f` ou `F` affiche les dixièmes de seconde, le spécificateur de format personnalisé `ff` ou `FF` affiche les centièmes de seconde, tandis que le spécificateur de format personnalisé `ffff` ou `FFFF` affiche les dix millièmes de seconde.</span><span class="sxs-lookup"><span data-stu-id="bc395-119">For example, the `f` or `F` custom format specifier displays tenths of a second, the `ff` or `FF` custom format specifier displays hundredths of a second, and the `ffff` or `FFFF` custom format specifier displays ten thousandths of a second.</span></span> <span data-ttu-id="bc395-120">La partie fractionnaire d’une milliseconde est tronquée au lieu d’être arrondie dans la chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="bc395-120">Fractional parts of a millisecond are truncated instead of rounded in the returned string.</span></span> <span data-ttu-id="bc395-121">Ces spécificateurs de format sont utilisés dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="bc395-121">These format specifiers are used in the following example.</span></span>  
  
 [!code-csharp[Formatting.HowTo.Millisecond#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.Millisecond/cs/Millisecond.cs#3)]
 [!code-vb[Formatting.HowTo.Millisecond#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.Millisecond/vb/Millisecond.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="bc395-122">Il est possible d’afficher de très petites unités fractionnaires d’une seconde, telles que les dix millièmes de seconde ou les cent millièmes de seconde.</span><span class="sxs-lookup"><span data-stu-id="bc395-122">It is possible to display very small fractional units of a second, such as ten thousandths of a second or hundred-thousandths of a second.</span></span> <span data-ttu-id="bc395-123">Toutefois, ces valeurs peuvent ne pas être significatives.</span><span class="sxs-lookup"><span data-stu-id="bc395-123">However, these values may not be meaningful.</span></span> <span data-ttu-id="bc395-124">La précision des valeurs de date et d'heure dépend de la résolution de l'horloge système.</span><span class="sxs-lookup"><span data-stu-id="bc395-124">The precision of date and time values depends on the resolution of the system clock.</span></span> <span data-ttu-id="bc395-125">Sur Windows NT 3.5 et versions ultérieures, et [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] les systèmes d’exploitation, la résolution de l’horloge est environ 10-15 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="bc395-125">On Windows NT 3.5 and later, and [!INCLUDE[windowsver](../../../includes/windowsver-md.md)] operating systems, the clock's resolution is approximately 10-15 milliseconds.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc395-126">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="bc395-126">Compiling the Code</span></span>  
 <span data-ttu-id="bc395-127">Compiler le code à la ligne de commande à l’aide de csc.exe ou vb.exe.</span><span class="sxs-lookup"><span data-stu-id="bc395-127">Compile the code at the command line using csc.exe or vb.exe.</span></span> <span data-ttu-id="bc395-128">Pour compiler le code dans [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], placez-le dans un modèle de projet application console.</span><span class="sxs-lookup"><span data-stu-id="bc395-128">To compile the code in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], put it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc395-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc395-129">See Also</span></span>  
 <xref:System.Globalization.DateTimeFormatInfo>  
 [<span data-ttu-id="bc395-130">Custom Date and Time Format Strings</span><span class="sxs-lookup"><span data-stu-id="bc395-130">Custom Date and Time Format Strings</span></span>](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
