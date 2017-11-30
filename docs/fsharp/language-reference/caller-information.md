---
title: "Informations sur l’appelant (F #)"
description: "Décrit comment utiliser les attributs d’Argument appelant Info pour obtenir des informations de l’appelant à partir d’une méthode."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a><span data-ttu-id="2722a-104">Informations sur l’appelant</span><span class="sxs-lookup"><span data-stu-id="2722a-104">Caller information</span></span>

<span data-ttu-id="2722a-105">À l'aide des attributs d'informations de l'appelant, vous pouvez obtenir des informations sur l'appelant d'une méthode.</span><span class="sxs-lookup"><span data-stu-id="2722a-105">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="2722a-106">Vous pouvez obtenir le chemin d'accès du fichier de code source, le numéro de ligne dans le code source, puis le nom du membre de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="2722a-106">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="2722a-107">Ces informations sont utiles pour suivre, déboguer, et créer des outils de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="2722a-107">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="2722a-108">Pour obtenir ces informations, vous utilisez les attributs qui sont appliqués aux paramètres facultatifs, qui a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="2722a-108">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="2722a-109">Le tableau suivant répertorie les attributs d’informations de l’appelant qui sont définies dans le [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) espace de noms :</span><span class="sxs-lookup"><span data-stu-id="2722a-109">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="2722a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2722a-110">Attribute</span></span>|<span data-ttu-id="2722a-111">Description</span><span class="sxs-lookup"><span data-stu-id="2722a-111">Description</span></span>|<span data-ttu-id="2722a-112">Type</span><span class="sxs-lookup"><span data-stu-id="2722a-112">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="2722a-113">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="2722a-113">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="2722a-114">Chemin d’accès complet du fichier source qui contient l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2722a-114">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="2722a-115">C’est le chemin d’accès au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2722a-115">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="2722a-116">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="2722a-116">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="2722a-117">Numéro de ligne dans le fichier source dans lequel la méthode est appelée.</span><span class="sxs-lookup"><span data-stu-id="2722a-117">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="2722a-118">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="2722a-118">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="2722a-119">Méthode ou nom de la propriété de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="2722a-119">Method or property name of the caller.</span></span> <span data-ttu-id="2722a-120">Consultez la section des noms de membres plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2722a-120">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="2722a-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="2722a-121">Example</span></span>

<span data-ttu-id="2722a-122">L’exemple suivant montre comment vous pouvez utiliser ces attributs pour un appelant de la trace.</span><span class="sxs-lookup"><span data-stu-id="2722a-122">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="2722a-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="2722a-123">Remarks</span></span>

<span data-ttu-id="2722a-124">Attributs d’informations de l’appelant est applicable uniquement aux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="2722a-124">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="2722a-125">Vous devez fournir une valeur explicite pour chaque paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="2722a-125">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="2722a-126">Les attributs d’informations d’appelant que le compilateur écrire la valeur appropriée pour chaque paramètre optionnel décoré avec un attribut d’informations de l’appelant.</span><span class="sxs-lookup"><span data-stu-id="2722a-126">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="2722a-127">Les valeurs d'informations de l'appelant sont émises en tant que littéraux en langage intermédiaire (IL) au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2722a-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="2722a-128">Contrairement aux résultats de la [StackTrace](/dotnet/api/system.diagnostics.stacktrace) propriété pour les exceptions, les résultats ne sont pas affectés par l’obfuscation.</span><span class="sxs-lookup"><span data-stu-id="2722a-128">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="2722a-129">Vous pouvez fournir explicitement les arguments facultatifs pour contrôler ou masquer des informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="2722a-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="2722a-130">Noms de membres</span><span class="sxs-lookup"><span data-stu-id="2722a-130">Member names</span></span>

<span data-ttu-id="2722a-131">Vous pouvez utiliser la [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut pour éviter de spécifier le nom du membre comme une `String` argument à la méthode appelée.</span><span class="sxs-lookup"><span data-stu-id="2722a-131">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="2722a-132">À l’aide de cette technique, vous évitez le problème qui ne change pas la refactorisation renommer le `String` valeurs.</span><span class="sxs-lookup"><span data-stu-id="2722a-132">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="2722a-133">Cet avantage est particulièrement utile pour les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2722a-133">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="2722a-134">Utilisation du traçage et des programmes de diagnostic.</span><span class="sxs-lookup"><span data-stu-id="2722a-134">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="2722a-135">Implémentation de la [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) lors de la liaison de données de l’interface.</span><span class="sxs-lookup"><span data-stu-id="2722a-135">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="2722a-136">Cette interface permet à la propriété d'un objet de signaler à un contrôle dépendant que la propriété a été modifiée, afin que ce contrôle puisse afficher les informations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="2722a-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="2722a-137">Sans le [ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribut, vous devez spécifier le nom de propriété comme littéral.</span><span class="sxs-lookup"><span data-stu-id="2722a-137">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="2722a-138">Le graphique suivant affiche des noms qui sont retournés lorsque vous utilisez l’attribut CallerMemberName le membre.</span><span class="sxs-lookup"><span data-stu-id="2722a-138">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="2722a-139">Les appels se produisent à l'intérieur</span><span class="sxs-lookup"><span data-stu-id="2722a-139">Calls occurs within</span></span>|<span data-ttu-id="2722a-140">Résultat de nom de membre</span><span class="sxs-lookup"><span data-stu-id="2722a-140">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="2722a-141">Méthode, propriété ou événement</span><span class="sxs-lookup"><span data-stu-id="2722a-141">Method, property, or event</span></span>|<span data-ttu-id="2722a-142">Le nom de la méthode, la propriété ou l'événement dont l'appel est originaire.</span><span class="sxs-lookup"><span data-stu-id="2722a-142">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="2722a-143">Constructeur</span><span class="sxs-lookup"><span data-stu-id="2722a-143">Constructor</span></span>|<span data-ttu-id="2722a-144">La chaîne « .ctor »</span><span class="sxs-lookup"><span data-stu-id="2722a-144">The string ".ctor"</span></span>|
|<span data-ttu-id="2722a-145">Constructeur statique</span><span class="sxs-lookup"><span data-stu-id="2722a-145">Static constructor</span></span>|<span data-ttu-id="2722a-146">La chaîne « .cctor »</span><span class="sxs-lookup"><span data-stu-id="2722a-146">The string ".cctor"</span></span>|
|<span data-ttu-id="2722a-147">Destructeur</span><span class="sxs-lookup"><span data-stu-id="2722a-147">Destructor</span></span>|<span data-ttu-id="2722a-148">La chaîne « finalize »</span><span class="sxs-lookup"><span data-stu-id="2722a-148">The string "Finalize"</span></span>|
|<span data-ttu-id="2722a-149">Opérateurs définis par l'utilisateur ou conversions</span><span class="sxs-lookup"><span data-stu-id="2722a-149">User-defined operators or conversions</span></span>|<span data-ttu-id="2722a-150">Le nom généré pour le membre, par exemple, « op_Addition ».</span><span class="sxs-lookup"><span data-stu-id="2722a-150">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="2722a-151">Constructeur d'attribut</span><span class="sxs-lookup"><span data-stu-id="2722a-151">Attribute constructor</span></span>|<span data-ttu-id="2722a-152">Le nom du membre auquel l'attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="2722a-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="2722a-153">Si l'attribut est un élément dans un membre (tel qu'un paramètre, une valeur de retour, ou un paramètre de type générique), le résultat est le nom du membre qui est associé à cet élément.</span><span class="sxs-lookup"><span data-stu-id="2722a-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="2722a-154">Aucun membre contenant (par exemple, niveau assembly ou attributs qui sont appliqués aux types)</span><span class="sxs-lookup"><span data-stu-id="2722a-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="2722a-155">Valeur par défaut du paramètre optionnel.</span><span class="sxs-lookup"><span data-stu-id="2722a-155">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2722a-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2722a-156">See also</span></span>
 [<span data-ttu-id="2722a-157">Attributs</span><span class="sxs-lookup"><span data-stu-id="2722a-157">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="2722a-158">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="2722a-158">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="2722a-159">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="2722a-159">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
