---
title: "Informations sur l’appelant (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d9a028474a3bb7ae020f466d4dfe51608c43ab07
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="56ad0-102">Informations sur l’appelant (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56ad0-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="56ad0-103">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="56ad0-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="56ad0-104">Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="56ad0-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="56ad0-105">Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="56ad0-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="56ad0-106">Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="56ad0-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="56ad0-107">Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définies dans le <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms :</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="56ad0-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="56ad0-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="56ad0-108">Attribute</span></span>|<span data-ttu-id="56ad0-109">Description</span><span class="sxs-lookup"><span data-stu-id="56ad0-109">Description</span></span>|<span data-ttu-id="56ad0-110">Type</span><span class="sxs-lookup"><span data-stu-id="56ad0-110">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="56ad0-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="56ad0-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="56ad0-112">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="56ad0-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="56ad0-113">C’est le chemin d’accès au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="56ad0-113">This is the file path at compile time.</span></span>|`String`|  
|<span data-ttu-id="56ad0-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="56ad0-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="56ad0-115">Numéro de ligne dans le fichier source dans lequel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="56ad0-115">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="56ad0-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="56ad0-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="56ad0-117">Méthode ou nom de la propriété de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="56ad0-117">Method or property name of the caller.</span></span> <span data-ttu-id="56ad0-118">Consultez la page [les noms de membres](#MEMBERNAMES) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="56ad0-118">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="56ad0-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="56ad0-119">Example</span></span>  
 <span data-ttu-id="56ad0-120">L'exemple suivant indique comment utiliser des attributs d'informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="56ad0-120">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="56ad0-121">À chaque appel à la méthode `TraceMessage`, les informations d'appel sont remplacées par des arguments pour les paramètres optionnels.</span><span class="sxs-lookup"><span data-stu-id="56ad0-121">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="56ad0-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="56ad0-122">Remarks</span></span>  
 <span data-ttu-id="56ad0-123">Vous devez spécifier une valeur par défaut explicite pour chaque paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="56ad0-123">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="56ad0-124">Vous ne pouvez pas appliquer des attributs d'informations de l'appelant aux paramètres qui ne sont pas spécifiés comme facultatifs.</span><span class="sxs-lookup"><span data-stu-id="56ad0-124">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="56ad0-125">Les attributs d'informations de l'appelant ne rendent pas un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="56ad0-125">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="56ad0-126">À la place, ils affectent la valeur par défaut qui est passée si l'argument est oublié.</span><span class="sxs-lookup"><span data-stu-id="56ad0-126">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="56ad0-127">Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="56ad0-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="56ad0-128">Contrairement aux résultats de la <xref:System.Exception.StackTrace%2A>propriété pour les exceptions, les résultats ne sont pas affectés par l’obscurcissement.</xref:System.Exception.StackTrace%2A></span><span class="sxs-lookup"><span data-stu-id="56ad0-128">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="56ad0-129">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="56ad0-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <span data-ttu-id="56ad0-130"><a name="MEMBERNAMES"></a>Noms de membres</span><span class="sxs-lookup"><span data-stu-id="56ad0-130"><a name="MEMBERNAMES"></a> Member Names</span></span>  
 <span data-ttu-id="56ad0-131">Vous pouvez utiliser l'attribut `CallerMemberName` pour éviter de spécifier le nom du membre comme argument de `String` à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="56ad0-131">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="56ad0-132">À l’aide de cette technique, vous évitez le problème qui **refactorisation renommer** ne modifie pas le `String` valeurs.</span><span class="sxs-lookup"><span data-stu-id="56ad0-132">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="56ad0-133">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="56ad0-133">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="56ad0-134">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="56ad0-134">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="56ad0-135">L’implémentation de le <xref:System.ComponentModel.INotifyPropertyChanged>lors de la liaison de données de l’interface.</xref:System.ComponentModel.INotifyPropertyChanged></span><span class="sxs-lookup"><span data-stu-id="56ad0-135">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="56ad0-136">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="56ad0-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="56ad0-137">Sans attribut `CallerMemberName`, vous devez spécifier le nom de la propriété comme littéral.</span><span class="sxs-lookup"><span data-stu-id="56ad0-137">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="56ad0-138">Le graphique suivant affiche les noms des membres qui sont retournés lorsque vous utilisez l'attribut `CallerMemberName`.</span><span class="sxs-lookup"><span data-stu-id="56ad0-138">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="56ad0-139">Les appels se produisent à l'intérieur</span><span class="sxs-lookup"><span data-stu-id="56ad0-139">Calls occurs within</span></span>|<span data-ttu-id="56ad0-140">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="56ad0-140">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="56ad0-141">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="56ad0-141">Method, property, or event</span></span>|<span data-ttu-id="56ad0-142">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="56ad0-142">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="56ad0-143">Constructeur</span><span class="sxs-lookup"><span data-stu-id="56ad0-143">Constructor</span></span>|<span data-ttu-id="56ad0-144">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="56ad0-144">The string ".ctor"</span></span>|  
|<span data-ttu-id="56ad0-145">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="56ad0-145">Static constructor</span></span>|<span data-ttu-id="56ad0-146">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="56ad0-146">The string ".cctor"</span></span>|  
|<span data-ttu-id="56ad0-147">Destructeur</span><span class="sxs-lookup"><span data-stu-id="56ad0-147">Destructor</span></span>|<span data-ttu-id="56ad0-148">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="56ad0-148">The string "Finalize"</span></span>|  
|<span data-ttu-id="56ad0-149">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="56ad0-149">User-defined operators or conversions</span></span>|<span data-ttu-id="56ad0-150">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="56ad0-150">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="56ad0-151">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="56ad0-151">Attribute constructor</span></span>|<span data-ttu-id="56ad0-152">Le nom du membre auquel l'attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="56ad0-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="56ad0-153">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="56ad0-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="56ad0-154">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="56ad0-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="56ad0-155">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="56ad0-155">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56ad0-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56ad0-156">See Also</span></span>  
 <span data-ttu-id="56ad0-157">[Attributs (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="56ad0-157">[Attributes (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="56ad0-158"> [Attributs courants (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="56ad0-158"> [Common Attributes (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span></span>  
<span data-ttu-id="56ad0-159"> [Paramètres facultatifs](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="56ad0-159"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="56ad0-160"> [Concepts de programmation (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="56ad0-160"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span></span>
