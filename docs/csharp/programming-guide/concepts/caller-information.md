---
title: "Informations relatives à l’appelant (C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8c514266b474f6d4cd3f02e6f9008bef053c407a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="caller-information-c"></a><span data-ttu-id="d475d-102">Informations relatives à l’appelant (C#)</span><span class="sxs-lookup"><span data-stu-id="d475d-102">Caller Information (C#)</span></span>
<span data-ttu-id="d475d-103">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="d475d-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="d475d-104">Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d475d-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="d475d-105">Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="d475d-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="d475d-106">Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="d475d-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="d475d-107">Le tableau suivant répertorie les attributs d'informations de l'appelant définis dans l'espace de noms <xref:System.Runtime.CompilerServices?displayProperty=fullName> :</span><span class="sxs-lookup"><span data-stu-id="d475d-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="d475d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d475d-108">Attribute</span></span>|<span data-ttu-id="d475d-109">Description</span><span class="sxs-lookup"><span data-stu-id="d475d-109">Description</span></span>|<span data-ttu-id="d475d-110">Type</span><span class="sxs-lookup"><span data-stu-id="d475d-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="d475d-111">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="d475d-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="d475d-112">C’est le chemin d’accès au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d475d-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="d475d-113">Numéro de ligne dans le fichier source dans lequel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="d475d-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="d475d-114">Méthode ou nom de la propriété de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d475d-114">Method or property name of the caller.</span></span> <span data-ttu-id="d475d-115">Consultez [Noms de membres](#MEMBERNAMES), plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="d475d-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="d475d-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d475d-116">Example</span></span>  
 <span data-ttu-id="d475d-117">L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d475d-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="d475d-118">À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.</span><span class="sxs-lookup"><span data-stu-id="d475d-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```csharp  
public void DoProcessing()  
{  
    TraceMessage("Something happened.");  
}  
  
public void TraceMessage(string message,  
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",  
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",  
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)  
{  
    System.Diagnostics.Trace.WriteLine("message: " + message);  
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);  
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);  
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);  
}  
  
// Sample Output:  
//  message: Something happened.  
//  member name: DoProcessing  
//  source file path: c:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoCS\CallerInfoCS\Form1.cs  
//  source line number: 31  
```  
  
## <a name="remarks"></a><span data-ttu-id="d475d-119">Remarques</span><span class="sxs-lookup"><span data-stu-id="d475d-119">Remarks</span></span>  
 <span data-ttu-id="d475d-120">Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="d475d-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="d475d-121">Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="d475d-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="d475d-122">Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="d475d-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="d475d-123">À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.</span><span class="sxs-lookup"><span data-stu-id="d475d-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="d475d-124">Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="d475d-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="d475d-125">Contrairement aux résultats de la propriété <xref:System.Exception.StackTrace%2A> pour les exceptions, les résultats ne sont pas affectés par l'obfuscation (protection de code).</span><span class="sxs-lookup"><span data-stu-id="d475d-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="d475d-126">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="d475d-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <span data-ttu-id="d475d-127"><a name="MEMBERNAMES"></a> Noms de membres</span><span class="sxs-lookup"><span data-stu-id="d475d-127"><a name="MEMBERNAMES"></a> Member Names</span></span>  
 <span data-ttu-id="d475d-128">Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="d475d-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="d475d-129">Vous évitez ainsi le problème que la **refactorisation de changement de nom** ne modifie pas les valeurs `String`.</span><span class="sxs-lookup"><span data-stu-id="d475d-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="d475d-130">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="d475d-130">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="d475d-131">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="d475d-131">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="d475d-132">Implémentation de l'interface <xref:System.ComponentModel.INotifyPropertyChanged> lors de la liaison de données.</span><span class="sxs-lookup"><span data-stu-id="d475d-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="d475d-133">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="d475d-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="d475d-134">Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.</span><span class="sxs-lookup"><span data-stu-id="d475d-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="d475d-135">Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="d475d-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="d475d-136">Les appels se produisent à l'intérieur</span><span class="sxs-lookup"><span data-stu-id="d475d-136">Calls occurs within</span></span>|<span data-ttu-id="d475d-137">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="d475d-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="d475d-138">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="d475d-138">Method, property, or event</span></span>|<span data-ttu-id="d475d-139">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="d475d-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="d475d-140">Constructeur</span><span class="sxs-lookup"><span data-stu-id="d475d-140">Constructor</span></span>|<span data-ttu-id="d475d-141">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="d475d-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="d475d-142">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="d475d-142">Static constructor</span></span>|<span data-ttu-id="d475d-143">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="d475d-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="d475d-144">Destructeur</span><span class="sxs-lookup"><span data-stu-id="d475d-144">Destructor</span></span>|<span data-ttu-id="d475d-145">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="d475d-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="d475d-146">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="d475d-146">User-defined operators or conversions</span></span>|<span data-ttu-id="d475d-147">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="d475d-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="d475d-148">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="d475d-148">Attribute constructor</span></span>|<span data-ttu-id="d475d-149">Le nom du membre auquel l'attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="d475d-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="d475d-150">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="d475d-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="d475d-151">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="d475d-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="d475d-152">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="d475d-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d475d-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d475d-153">See Also</span></span>  
 <span data-ttu-id="d475d-154">[Attributs (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="d475d-154">[Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/index.md) </span></span>  
 <span data-ttu-id="d475d-155">[Attributs courants (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="d475d-155">[Common Attributes (C#)](../../../csharp/programming-guide/concepts/attributes/common-attributes.md) </span></span>  
 <span data-ttu-id="d475d-156">[Arguments nommés et facultatifs](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="d475d-156">[Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md) </span></span>  
 [<span data-ttu-id="d475d-157">Concepts de programmation (C#)</span><span class="sxs-lookup"><span data-stu-id="d475d-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)

