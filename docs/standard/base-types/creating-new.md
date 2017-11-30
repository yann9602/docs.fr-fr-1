---
title: "Création de nouvelles chaînes dans .NET"
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
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d000cd88fc9ee9fd48ef25e9bb4982688564a2a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="6b298-102">Création de nouvelles chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="6b298-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="6b298-103">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] permet des chaînes à l’aide d’une assignation simple et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide d’un nombre de paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="6b298-103">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="6b298-104">Le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] fournit également plusieurs méthodes dans la <xref:System.String?displayProperty=nameWithType> classe créer la nouvelle chaîne en combinant plusieurs chaînes, tableaux de chaînes, des objets ou des objets.</span><span class="sxs-lookup"><span data-stu-id="6b298-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="6b298-105">Création de chaînes à l’aide d’une affectation</span><span class="sxs-lookup"><span data-stu-id="6b298-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="6b298-106">Le moyen le plus simple pour créer un nouveau <xref:System.String> objet consiste à assigner un littéral de chaîne en un <xref:System.String> objet.</span><span class="sxs-lookup"><span data-stu-id="6b298-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="6b298-107">Création de chaînes à l’aide d’un constructeur de classe</span><span class="sxs-lookup"><span data-stu-id="6b298-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="6b298-108">Vous pouvez utiliser les surcharges de la <xref:System.String> constructeur de classe pour créer des chaînes à partir des tableaux de caractères.</span><span class="sxs-lookup"><span data-stu-id="6b298-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="6b298-109">Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.</span><span class="sxs-lookup"><span data-stu-id="6b298-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="6b298-110">Méthodes retournant des chaînes</span><span class="sxs-lookup"><span data-stu-id="6b298-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="6b298-111">Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.</span><span class="sxs-lookup"><span data-stu-id="6b298-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="6b298-112">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="6b298-112">Method name</span></span>|<span data-ttu-id="6b298-113">Utilisation</span><span class="sxs-lookup"><span data-stu-id="6b298-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="6b298-114">Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="6b298-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="6b298-115">Génère des chaînes à partir de deux ou de plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="6b298-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="6b298-116">Génère une nouvelle chaîne en combinant un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6b298-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="6b298-117">Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.</span><span class="sxs-lookup"><span data-stu-id="6b298-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="6b298-118">Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="6b298-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="6b298-119">Format</span><span class="sxs-lookup"><span data-stu-id="6b298-119">Format</span></span>  
 <span data-ttu-id="6b298-120">Vous pouvez utiliser la **String.Format** pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="6b298-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="6b298-121">Cette méthode convertit automatiquement tout objet passé en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="6b298-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="6b298-122">Par exemple, si votre application doit afficher une **Int32** valeur et un **DateTime** valeur à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la **Format**(méthode).</span><span class="sxs-lookup"><span data-stu-id="6b298-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="6b298-123">Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="6b298-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="6b298-124">L’exemple suivant utilise le **Format** méthode pour créer une chaîne qui utilise une variable de type entier.</span><span class="sxs-lookup"><span data-stu-id="6b298-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="6b298-125">Dans cet exemple,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> affiche la date et l’heure de la manière spécifiée par la culture associée au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="6b298-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="6b298-126">Concat</span><span class="sxs-lookup"><span data-stu-id="6b298-126">Concat</span></span>  
 <span data-ttu-id="6b298-127">Le **String.Concat** méthode peut être utilisée pour créer facilement un nouvel objet string à partir de deux ou plusieurs objets existants.</span><span class="sxs-lookup"><span data-stu-id="6b298-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="6b298-128">Elle offre un moyen de concaténer des chaînes indépendamment du langage.</span><span class="sxs-lookup"><span data-stu-id="6b298-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="6b298-129">Cette méthode accepte toute classe qui dérive de **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="6b298-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="6b298-130">L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="6b298-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="6b298-131">Join</span><span class="sxs-lookup"><span data-stu-id="6b298-131">Join</span></span>  
 <span data-ttu-id="6b298-132">Le **String.Join** méthode crée une nouvelle chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="6b298-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="6b298-133">Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.</span><span class="sxs-lookup"><span data-stu-id="6b298-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="6b298-134">L’exemple suivant utilise un espace pour lier un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="6b298-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="6b298-135">Insert</span><span class="sxs-lookup"><span data-stu-id="6b298-135">Insert</span></span>  
 <span data-ttu-id="6b298-136">Le **String.Insert** méthode crée une nouvelle chaîne en insérant une chaîne dans une position spécifiée dans une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="6b298-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="6b298-137">Cette méthode utilise un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="6b298-137">This method uses a zero-based index.</span></span> <span data-ttu-id="6b298-138">L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.</span><span class="sxs-lookup"><span data-stu-id="6b298-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="6b298-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="6b298-139">CopyTo</span></span>  
 <span data-ttu-id="6b298-140">Le **String.CopyTo** méthode copie d’une chaîne dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="6b298-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="6b298-141">Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="6b298-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="6b298-142">Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="6b298-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="6b298-143">Tous les index sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="6b298-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="6b298-144">L’exemple suivant utilise le **CopyTo** méthode pour copier les caractères du mot « Hello » à partir d’une chaîne de l’objet à la première position d’index d’un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="6b298-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="6b298-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b298-145">See Also</span></span>  
 [<span data-ttu-id="6b298-146">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="6b298-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 [<span data-ttu-id="6b298-147">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="6b298-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
