---
title: "Exécution de changements de casse indépendants de la culture"
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
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c500b882c335572b8b458ba515b282e9f5362b85
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="023af-102">Exécution de changements de casse indépendants de la culture</span><span class="sxs-lookup"><span data-stu-id="023af-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="023af-103">Le <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, et <xref:System.Char.ToLower%2A?displayProperty=nameWithType> méthodes fournissent des surcharges qui n’acceptent pas de paramètres.</span><span class="sxs-lookup"><span data-stu-id="023af-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="023af-104">Par défaut, ces surcharges sans paramètre effectuent des changements de casse basés sur la valeur de la <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="023af-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="023af-105">Cela produit des résultats de la casse peuvent varier selon la culture.</span><span class="sxs-lookup"><span data-stu-id="023af-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="023af-106">Pour indiquer clairement que vous souhaitez être dépendante ou indépendante de la culture des changements de casse, vous devez utiliser les surcharges de ces méthodes, vous devez spécifier explicitement un `culture` paramètre.</span><span class="sxs-lookup"><span data-stu-id="023af-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="023af-107">Pour les changements de casse dépendante de la culture, spécifiez `CultureInfo.CurrentCulture` pour la `culture` paramètre.</span><span class="sxs-lookup"><span data-stu-id="023af-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="023af-108">Pour les changements de casse indépendants de la culture, spécifiez `CultureInfo.InvariantCulture` pour la `culture` paramètre.</span><span class="sxs-lookup"><span data-stu-id="023af-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="023af-109">Souvent, les chaînes sont converties en une casse standard pour faciliter les recherches plus tard.</span><span class="sxs-lookup"><span data-stu-id="023af-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="023af-110">Lorsque les chaînes sont utilisées de cette manière, vous devez spécifier `CultureInfo.InvariantCulture` pour le `culture` paramètre, car la valeur de <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> peut changer entre le moment où la casse est modifiée et l’heure à laquelle la recherche est effectuée.</span><span class="sxs-lookup"><span data-stu-id="023af-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="023af-111">Si une décision de sécurité est basée sur une opération de changement de casse, l’opération doit être indépendante de la culture pour garantir que le résultat n’est pas affecté par la valeur de `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="023af-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="023af-112">Consultez la section « Chaîne comparaisons qui utiliser la Culture en cours » de la [meilleures pratiques pour l’utilisation de chaînes](../../../docs/standard/base-types/best-practices-strings.md) article pour obtenir un exemple qui montre comment des opérations de chaîne peut produire des résultats incohérents.</span><span class="sxs-lookup"><span data-stu-id="023af-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="023af-113">À l’aide de la String.ToUpper et String.ToLower</span><span class="sxs-lookup"><span data-stu-id="023af-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="023af-114">Pour la clarté du code, il est recommandé de toujours utiliser des surcharges de la `String.ToUpper` et `String.ToLower` méthodes qui vous permettent de spécifier un `culture` paramètre explicitement.</span><span class="sxs-lookup"><span data-stu-id="023af-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="023af-115">Par exemple, le code suivant effectue une recherche d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="023af-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="023af-116">Le `key.ToLower` opération est dépendante de la culture par défaut, mais ce comportement n’est pas clair à partir de la lecture du code.</span><span class="sxs-lookup"><span data-stu-id="023af-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="023af-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="023af-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="023af-118">Si vous souhaitez que le `key.ToLower` opération soit indépendante de la culture, vous devez modifier l’exemple précédent comme suit pour utiliser explicitement le `CultureInfo.InvariantCulture` lors de la modification de la casse.</span><span class="sxs-lookup"><span data-stu-id="023af-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="023af-119">À l’aide de la méthodes Char.ToUpper et Char.ToLower</span><span class="sxs-lookup"><span data-stu-id="023af-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="023af-120">Bien que le `Char.ToUpper` et `Char.ToLower` méthodes ont les mêmes caractéristiques que le `String.ToUpper` et `String.ToLower` méthodes, les seules cultures affectées sont le turc (Turquie) et Azérie (Latin, Azerbaïdjan).</span><span class="sxs-lookup"><span data-stu-id="023af-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="023af-121">Il s’agit uniquement deux cultures avec des différences de casse de caractère unique.</span><span class="sxs-lookup"><span data-stu-id="023af-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="023af-122">Pour plus d’informations sur ce mappage de casse unique, consultez la section « Casse » dans la <xref:System.String> rubrique de la classe.</span><span class="sxs-lookup"><span data-stu-id="023af-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="023af-123">Pour la clarté du code et pour garantir des résultats cohérents, il est recommandé de toujours utiliser les surcharges de ces méthodes qui vous permettent de spécifier explicitement un `culture` paramètre.</span><span class="sxs-lookup"><span data-stu-id="023af-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023af-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="023af-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="023af-125">Exécution d'opérations de chaînes indépendantes de la culture</span><span class="sxs-lookup"><span data-stu-id="023af-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
