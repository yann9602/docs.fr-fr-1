---
title: "Documentation de votre code avec des commentaires XML"
description: "Découvrez comment documenter votre code avec des commentaires de documentation XML et générer un fichier de documentation XML au moment de la compilation."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 02/14/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8e75e317-4a55-45f2-a866-e76124171838
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0cb5725a70d94173c8596f818dcaa6eb2de13bcc
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="documenting-your-code-with-xml-comments"></a><span data-ttu-id="7e7ec-104">Documentation de votre code avec des commentaires XML</span><span class="sxs-lookup"><span data-stu-id="7e7ec-104">Documenting your code with XML comments</span></span>

<span data-ttu-id="7e7ec-105">Les commentaires de documentation XML sont un genre particulier de commentaire, ajouté au-dessus de la définition d’un type ou d’un membre défini par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-105">XML documentation comments are a special kind of comment, added above the definition of any user-defined type or member.</span></span> <span data-ttu-id="7e7ec-106">Ils sont spéciaux, car ils peuvent être traités par le compilateur pour générer un fichier de documentation XML au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-106">They are special because they can be processed by the compiler to generate an XML documentation file at compile time.</span></span>
<span data-ttu-id="7e7ec-107">Le fichier XML généré par le compilateur peut être distribué avec votre assembly .NET pour permettre à Visual Studio et à d’autres IDE d’utiliser IntelliSense pour afficher des informations rapides concernant les types ou les membres.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-107">The compiler generated XML file can be distributed alongside your .NET assembly so that Visual Studio and other IDEs can use IntelliSense to show quick information about types or members.</span></span> <span data-ttu-id="7e7ec-108">De plus, le fichier XML peut être exécuté par l’intermédiaire d’outils tels que [DocFX](https://dotnet.github.io/docfx/) et [Sandcastle](https://github.com/EWSoftware/SHFB) pour générer des sites web de références d’API.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-108">Additionally, the XML file can be run through tools like [DocFX](https://dotnet.github.io/docfx/) and [Sandcastle](https://github.com/EWSoftware/SHFB) to generate API reference websites.</span></span>

<span data-ttu-id="7e7ec-109">Les commentaires de documentation XML, comme tous les autres commentaires, sont ignorés par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-109">XML documentation comments, like all other comments, are ignored by the compiler.</span></span>

<span data-ttu-id="7e7ec-110">Vous pouvez générer le fichier XML au moment de la compilation en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-110">You can generate the XML file at compile time by doing one of the following:</span></span>

- <span data-ttu-id="7e7ec-111">Si vous développez une application avec .NET Core à partir de la ligne de commande, vous pouvez ajouter un [élément DocumentationFile](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) à la section `<PropertyGroup>` de votre fichier projet .csproj.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-111">If you are developing an application with .NET Core from the command line, you can add a [DocumentationFile element](http://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties) to the `<PropertyGroup>` section of your .csproj project file.</span></span> <span data-ttu-id="7e7ec-112">L’exemple suivant génère un fichier XML dans le répertoire du projet avec le même nom de fichier racine que le projet :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-112">The following example generates an XML file in the project directory with the same root filename as the project:</span></span>

   ```xml
   <DocumentationFile>$(MSBuildProjectName).xml</DocumentationFile>
   ```

   <span data-ttu-id="7e7ec-113">Vous pouvez également spécifier le chemin absolu ou relatif exact et le nom du fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-113">You can also specify the exact absolute or relative path and name of the XML file.</span></span> <span data-ttu-id="7e7ec-114">L’exemple suivant génère le fichier XML dans le même répertoire que la version Debug d’une application :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-114">The following example generates the XML file in the same directory as the debug version of an application:</span></span>

    ```xml
   <DocumentationFile>bin\Debug\netcoreapp1.0\App.xml</DocumentationFile>
   ```

- <span data-ttu-id="7e7ec-115">Si vous développez une application à l’aide de Visual Studio, cliquez avec le bouton droit sur le projet, puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-115">If you are developing an application using Visual Studio, right-click on the project and select **Properties**.</span></span> <span data-ttu-id="7e7ec-116">Dans la boîte de dialogue des propriétés, sélectionnez l’onglet **Générer**, puis cochez **Fichier de documentation XML**.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-116">In the properties dialog, select the **Build** tab, and check **XML documentation file**.</span></span> <span data-ttu-id="7e7ec-117">Vous pouvez également changer l’emplacement dans lequel le compilateur écrit le fichier.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-117">You can also change the location to which the compiler writes the file.</span></span> 

- <span data-ttu-id="7e7ec-118">Si vous compilez une application .NET Framework à partir de la ligne de commande, ajoutez l’[option du compilateur /doc](language-reference/compiler-options/doc-compiler-option.md) lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-118">If you are compiling a .NET Framework application from the command line, add the [/doc compiler option](language-reference/compiler-options/doc-compiler-option.md) when compiling.</span></span>  

<span data-ttu-id="7e7ec-119">Les commentaires de documentation XML utilisent des barres obliques triples (`///`) et le corps d’un commentaire au format XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-119">XML documentation comments use triple forward slashes (`///`) and an XML formatted comment body.</span></span> <span data-ttu-id="7e7ec-120">Exemple :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-120">For example:</span></span>

<span data-ttu-id="7e7ec-121">[!code-csharp[Commentaires sur la documentation XML](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-121">[!code-csharp[XML Documentation Comment](../../samples/snippets/csharp/concepts/codedoc/xml-comment.cs)]</span></span>

## <a name="walkthrough"></a><span data-ttu-id="7e7ec-122">Procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="7e7ec-122">Walkthrough</span></span>

<span data-ttu-id="7e7ec-123">Examinons en détail la documentation d’une bibliothèque mathématique très basique visant à faciliter la compréhension/la contribution des nouveaux développeurs, ainsi que son utilisation par des développeurs tiers.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-123">Let's walk through documenting a very basic math library to make it easy for new developers to understand/contribute and for third party developers to use.</span></span>

<span data-ttu-id="7e7ec-124">Voici le code de la bibliothèque mathématique simple :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-124">Here's code for the simple math library:</span></span>

<span data-ttu-id="7e7ec-125">[!code-csharp[Exemple de bibliothèque](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-125">[!code-csharp[Sample Library](../../samples/snippets/csharp/concepts/codedoc/sample-library.cs)]</span></span>

<span data-ttu-id="7e7ec-126">L’exemple de bibliothèque prend en charge quatre opérations arithmétiques principales `add`, `subtract`, `multiply` et `divide` sur des types de données `int` et `double`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-126">The sample library supports four major arithmetic operations `add`, `subtract`, `multiply` and `divide` on `int` and `double` data types.</span></span>

<span data-ttu-id="7e7ec-127">Vous voulez maintenant pouvoir créer un document de référence des API à partir de votre code pour les développeurs tiers qui utilisent votre bibliothèque, mais qui n’ont pas accès au code source.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-127">Now you want to be able to create an API reference document from your code for third party developers who use your library but don't have access to the source code.</span></span>
<span data-ttu-id="7e7ec-128">Comme mentionné précédemment, les balises de documentation XML peuvent être utilisées à cette fin. Vous allez maintenant découvrir les balises XML standard prises en charge par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-128">As mentioned earlier XML documentation tags can be used to achieve this, You will now be introduced to the standard XML tags the C# compiler supports.</span></span>

### <a name="ltsummarygt"></a><span data-ttu-id="7e7ec-129">&lt;summary&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-129">&lt;summary&gt;</span></span>

<span data-ttu-id="7e7ec-130">La balise `<summary>` ajoute des informations succinctes relatives à un type ou un membre.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-130">The `<summary>` tag adds brief information about a type or member.</span></span>
<span data-ttu-id="7e7ec-131">Je vais expliquer son utilisation en l’ajoutant à la définition de la classe `Math` et à la première méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-131">I'll demonstrate its use by adding it to the `Math` class definition and the first `Add` method.</span></span> <span data-ttu-id="7e7ec-132">N’hésitez pas à l’appliquer au reste de votre code.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-132">Feel free to apply it to the rest of your code.</span></span>

<span data-ttu-id="7e7ec-133">[!code-csharp[Balise summary](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-133">[!code-csharp[Summary Tag](../../samples/snippets/csharp/concepts/codedoc/summary-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-134">La balise `<summary>` est très importante, et nous vous recommandons de l’inclure, car son contenu est la principale source d’informations sur les types ou les membres dans IntelliSense ou un document de référence des API.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-134">The `<summary>` tag is very important, and we recommend that you include it because its content is the primary source of type or member information in IntelliSense or an API reference document.</span></span>

### <a name="ltremarksgt"></a><span data-ttu-id="7e7ec-135">&lt;remarks&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-135">&lt;remarks&gt;</span></span>

<span data-ttu-id="7e7ec-136">La balise `<remarks>` complète les informations relatives aux types ou aux membres fournies par la balise `<summary>`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-136">The `<remarks>` tag supplements the information about types or members that the `<summary>` tag provides.</span></span> <span data-ttu-id="7e7ec-137">Dans cet exemple, vous allez simplement l’ajouter à la classe.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-137">In this example, you'll just add it to the class.</span></span>

<span data-ttu-id="7e7ec-138">[!code-csharp[Balise remarks](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-138">[!code-csharp[Remarks Tag](../../samples/snippets/csharp/concepts/codedoc/remarks-tag.cs)]</span></span>

### <a name="ltreturnsgt"></a><span data-ttu-id="7e7ec-139">&lt;returns&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-139">&lt;returns&gt;</span></span>

<span data-ttu-id="7e7ec-140">La balise `<returns>` décrit la valeur de retour d’une déclaration de méthode.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-140">The `<returns>` tag describes the return value of a method declaration.</span></span>
<span data-ttu-id="7e7ec-141">Comme auparavant, l’exemple suivant illustre la balise `<returns>` sur la première méthode `Add`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-141">As before, the following example illustrates the `<returns>` tag on the first `Add` method.</span></span> <span data-ttu-id="7e7ec-142">Vous pouvez effectuer la même opération sur d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-142">You can do the same on other methods.</span></span>

<span data-ttu-id="7e7ec-143">[!code-csharp[Balise returns](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-143">[!code-csharp[Returns Tag](../../samples/snippets/csharp/concepts/codedoc/returns-tag.cs)]</span></span>

### <a name="ltvaluegt"></a><span data-ttu-id="7e7ec-144">&lt;value&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-144">&lt;value&gt;</span></span>

<span data-ttu-id="7e7ec-145">La balise `<value>` est similaire à la balise `<returns>`, excepté que vous l’utilisez pour les propriétés.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-145">The `<value>` tag is similar to the `<returns>` tag, except that you use it for properties.</span></span>
<span data-ttu-id="7e7ec-146">En supposant que votre bibliothèque `Math` a une propriété statique appelée `PI`, voici comment utiliser cette balise :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-146">Assuming your `Math` library had a static property called `PI`, here's how you'd use this tag:</span></span>

<span data-ttu-id="7e7ec-147">[!code-csharp[Balise value](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-147">[!code-csharp[Value Tag](../../samples/snippets/csharp/concepts/codedoc/value-tag.cs)]</span></span>

### <a name="ltexamplegt"></a><span data-ttu-id="7e7ec-148">&lt;example&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-148">&lt;example&gt;</span></span>

<span data-ttu-id="7e7ec-149">La balise `<example>` permet d’inclure un exemple de votre documentation XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-149">You use the `<example>` tag to include an example in your XML documentation.</span></span>
<span data-ttu-id="7e7ec-150">Cela implique l’utilisation de la balise enfant `<code>`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-150">This involves using the child `<code>` tag.</span></span>

<span data-ttu-id="7e7ec-151">[!code-csharp[Balise example](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-151">[!code-csharp[Example Tag](../../samples/snippets/csharp/concepts/codedoc/example-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-152">La balise `code` conserve les sauts de ligne et la mise en retrait pour les exemples plus longs.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-152">The `code` tag preserves line breaks and indentation for longer examples.</span></span>

### <a name="ltparagt"></a><span data-ttu-id="7e7ec-153">&lt;para&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-153">&lt;para&gt;</span></span>

<span data-ttu-id="7e7ec-154">La balise `<para>` permet de mettre en forme le contenu de sa balise parente.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-154">You use the `<para>` tag to format the content within its parent tag.</span></span> <span data-ttu-id="7e7ec-155">`<para>` est généralement utilisée dans une balise, telle que `<remarks>` ou `<returns>`, pour diviser du texte en paragraphes.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-155">`<para>` is usually used inside a tag, such as `<remarks>` or `<returns>`, to divide text into paragraphs.</span></span>
<span data-ttu-id="7e7ec-156">Vous pouvez mettre en forme le contenu de la balise `<remarks>` pour la définition de votre classe.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-156">You can format the contents of the `<remarks>` tag for your class definition.</span></span>

<span data-ttu-id="7e7ec-157">[!code-csharp[Balise para](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-157">[!code-csharp[Para Tag](../../samples/snippets/csharp/concepts/codedoc/para-tag.cs)]</span></span>

### <a name="ltcgt"></a><span data-ttu-id="7e7ec-158">&lt;c&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-158">&lt;c&gt;</span></span>

<span data-ttu-id="7e7ec-159">Toujours concernant la mise en forme, vous utilisez la balise `<c>` pour le marquage d’une partie du texte comme code.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-159">Still on the topic of formatting, you use the `<c>` tag for marking part of text as code.</span></span>
<span data-ttu-id="7e7ec-160">Elle est semblable à la balise `<code>`, mais inline.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-160">It's like the `<code>` tag but inline.</span></span> <span data-ttu-id="7e7ec-161">Elle est utile quand vous voulez afficher un exemple de code rapide comme partie du contenu d’une balise.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-161">It's useful when you want to show a quick code example as part of a tag's content.</span></span>
<span data-ttu-id="7e7ec-162">Mettons à jour la documentation de la classe `Math`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-162">Let's update the documentation for the `Math` class.</span></span>

<span data-ttu-id="7e7ec-163">[!code-csharp[Balise c](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-163">[!code-csharp[C Tag](../../samples/snippets/csharp/concepts/codedoc/c-tag.cs)]</span></span>

### <a name="ltexceptiongt"></a><span data-ttu-id="7e7ec-164">&lt;exception&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-164">&lt;exception&gt;</span></span>

<span data-ttu-id="7e7ec-165">En utilisant la balise `<exception>`, vous informez vos développeurs qu’une méthode peut lever des exceptions spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-165">By using the `<exception>` tag, you let your developers know that a method can throw specific exceptions.</span></span>
<span data-ttu-id="7e7ec-166">Si vous examinez votre bibliothèque `Math`, vous pouvez voir que les deux méthodes `Add` lèvent une exception si une certaine condition est remplie.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-166">Looking at your `Math` library, you can see that both `Add` methods throw an exception if a certain condition is met.</span></span> <span data-ttu-id="7e7ec-167">Il est toutefois moins évident de voir que la méthode `Divide` utilisée avec un entier lève également une exception si le paramètre `b` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-167">Not so obvious, though, is that integer `Divide` method throws as well if the `b` parameter is zero.</span></span> <span data-ttu-id="7e7ec-168">Ajoutez maintenant une documentation d’exception à cette méthode.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-168">Now add exception documentation to this method.</span></span>

<span data-ttu-id="7e7ec-169">[!code-csharp[Balise exception](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-169">[!code-csharp[Exception Tag](../../samples/snippets/csharp/concepts/codedoc/exception-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-170">L’attribut `cref` référence une exception qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-170">The `cref` attribute represents a reference to an exception that is available from the current compilation environment.</span></span>
<span data-ttu-id="7e7ec-171">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-171">This can be any type defined in the project or a referenced assembly.</span></span> <span data-ttu-id="7e7ec-172">Le compilateur émet un avertissement si sa valeur ne peut pas être résolue.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-172">The compiler will issue a warning if its value cannot be resolved.</span></span>

### <a name="ltseegt"></a><span data-ttu-id="7e7ec-173">&lt;see&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-173">&lt;see&gt;</span></span>

<span data-ttu-id="7e7ec-174">La balise `<see>` vous permet de créer un lien interactif vers une page de documentation pour un autre élément de code.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-174">The `<see>` tag lets you create a clickable link to a documentation page for another code element.</span></span> <span data-ttu-id="7e7ec-175">Dans notre prochain exemple, nous allons créer un lien interactif entre les deux méthodes `Add`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-175">In our next example, we'll create a clickable link between the two `Add` methods.</span></span>

<span data-ttu-id="7e7ec-176">[!code-csharp[Balise see](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-176">[!code-csharp[See Tag](../../samples/snippets/csharp/concepts/codedoc/see-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-177">`cref` est un attribut **obligatoire** qui représente une référence à un type ou à ses membres et qui est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-177">The `cref` is a **required** attribute that represents a reference to a type or its member that is available from the current compilation environment.</span></span> <span data-ttu-id="7e7ec-178">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-178">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltseealsogt"></a><span data-ttu-id="7e7ec-179">&lt;seealso&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-179">&lt;seealso&gt;</span></span>

<span data-ttu-id="7e7ec-180">Vous pouvez utiliser la balise `<seealso>` de la même façon que la balise `<see>`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-180">You use the `<seealso>` tag in the same way you do the `<see>` tag.</span></span> <span data-ttu-id="7e7ec-181">La seule différence est que son contenu est généralement placé dans une section "Voir aussi".</span><span class="sxs-lookup"><span data-stu-id="7e7ec-181">The only difference is that its content is typically placed in a "See Also" section.</span></span> <span data-ttu-id="7e7ec-182">Ici, nous allons ajouter une balise `seealso` sous la méthode `Add` utilisée avec un entier pour référencer d’autres méthodes de la classe qui acceptent des paramètres entiers :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-182">Here we'll add a `seealso` tag on the integer `Add` method to reference other methods in the class that accept integer parameters:</span></span>

<span data-ttu-id="7e7ec-183">[!code-csharp[Balise seealso](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-183">[!code-csharp[Seealso Tag](../../samples/snippets/csharp/concepts/codedoc/seealso-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-184">L’attribut `cref` représente une référence à un type ou à ses membres et est disponible à partir de l’environnement de compilation actuel.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-184">The `cref` attribute represents a reference to a type or its member that is available from the current compilation environment.</span></span>
<span data-ttu-id="7e7ec-185">Il peut s’agir de tout type défini dans le projet ou dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-185">This can be any type defined in the project or a referenced assembly.</span></span>

### <a name="ltparamgt"></a><span data-ttu-id="7e7ec-186">&lt;param&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-186">&lt;param&gt;</span></span>

<span data-ttu-id="7e7ec-187">La balise `<param>` permet de décrire les paramètres d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-187">You use the `<param>` tag to describe a method's parameters.</span></span> <span data-ttu-id="7e7ec-188">Voici un exemple sur la méthode `Add` double : le paramètre décrit par la balise est spécifié dans l’attribut `name` **obligatoire**.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-188">Here's an example on the double `Add` method: The parameter the tag describes is specified in the **required** `name` attribute.</span></span>

<span data-ttu-id="7e7ec-189">[!code-csharp[Balise param](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-189">[!code-csharp[Param Tag](../../samples/snippets/csharp/concepts/codedoc/param-tag.cs)]</span></span>

### <a name="lttypeparamgt"></a><span data-ttu-id="7e7ec-190">&lt;typeparam&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-190">&lt;typeparam&gt;</span></span>

<span data-ttu-id="7e7ec-191">Vous utilisez la balise `<typeparam>` exactement comme la balise `<param>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-191">You use `<typeparam>` tag just like the `<param>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="7e7ec-192">Ajoutez une méthode générique rapide à votre classe `Math` pour vérifier si une quantité est supérieure à une autre.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-192">Add a quick generic method to your `Math` class to check if one quantity is greater than another.</span></span>

<span data-ttu-id="7e7ec-193">[!code-csharp[Balise typeparam](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-193">[!code-csharp[Typeparam Tag](../../samples/snippets/csharp/concepts/codedoc/typeparam-tag.cs)]</span></span>

### <a name="ltparamrefgt"></a><span data-ttu-id="7e7ec-194">&lt;paramref&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-194">&lt;paramref&gt;</span></span>

<span data-ttu-id="7e7ec-195">Alors que vous décrivez ce que fait une méthode dans ce qui pourrait être une balise `<summary>`, vous souhaiterez peut-être créer une référence à un paramètre.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-195">Sometimes you might be in the middle of describing what a method does in what could be a `<summary>` tag, and you might want to make a reference to a parameter.</span></span> <span data-ttu-id="7e7ec-196">La balise `<paramref>` est idéale pour cette tâche précise.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-196">The `<paramref>` tag is great for just this.</span></span> <span data-ttu-id="7e7ec-197">Mettons à jour le récapitulatif de notre méthode `Add` double.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-197">Let's update the summary of our double based `Add` method.</span></span> <span data-ttu-id="7e7ec-198">Comme pour la balise `<param>`, le nom du paramètre est spécifié dans l’attribut `name` **obligatoire**.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-198">Like the `<param>` tag the parameter name is specified in the **required** `name` attribute.</span></span>

<span data-ttu-id="7e7ec-199">[!code-csharp[Balise paramref](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-199">[!code-csharp[Paramref Tag](../../samples/snippets/csharp/concepts/codedoc/paramref-tag.cs)]</span></span>

### <a name="lttypeparamrefgt"></a><span data-ttu-id="7e7ec-200">&lt;typeparamref&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-200">&lt;typeparamref&gt;</span></span>

<span data-ttu-id="7e7ec-201">Vous utilisez la balise `<typeparamref>` exactement comme la balise `<paramref>`, mais pour permettre aux déclarations de types ou de méthodes génériques de décrire un paramètre générique.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-201">You use `<typeparamref>` tag just like the `<paramref>` tag but for generic type or method declarations to describe a generic parameter.</span></span>
<span data-ttu-id="7e7ec-202">Vous pouvez utiliser la même méthode générique que celle créée précédemment.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-202">You can use the same generic method you previously created.</span></span>

<span data-ttu-id="7e7ec-203">[!code-csharp[Balise typeparamref](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-203">[!code-csharp[Typeparamref Tag](../../samples/snippets/csharp/concepts/codedoc/typeparamref-tag.cs)]</span></span>

### <a name="ltlistgt"></a><span data-ttu-id="7e7ec-204">&lt;list&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-204">&lt;list&gt;</span></span>

<span data-ttu-id="7e7ec-205">La balise `<list>` vous permet de mettre en forme des informations de documentation sous la forme d’une liste triée, d’une liste non triée ou d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-205">You use the `<list>` tag to format documentation information as an ordered list, unordered list or table.</span></span>
<span data-ttu-id="7e7ec-206">Créez une liste non triée de toutes les opérations mathématiques prises en charge par votre bibliothèque `Math`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-206">Make an unordered list of every math operation your `Math` library supports.</span></span>

<span data-ttu-id="7e7ec-207">[!code-csharp[Balise list](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-207">[!code-csharp[List Tag](../../samples/snippets/csharp/concepts/codedoc/list-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-208">Vous pouvez créer une liste triée ou un tableau en remplaçant l’attribut `type` par `number` ou `table`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-208">You can make an ordered list or table by changing the `type` attribute to `number` or `table`, respectively.</span></span>

### <a name="putting-it-all-together"></a><span data-ttu-id="7e7ec-209">En résumé</span><span class="sxs-lookup"><span data-stu-id="7e7ec-209">Putting it all together</span></span>

<span data-ttu-id="7e7ec-210">Si vous avez suivi ce didacticiel et appliqué les balises à votre code au besoin, votre code doit maintenant ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-210">If you've followed this tutorial and applied the tags to your code where necessary, your code should now look similar to the following:</span></span>

<span data-ttu-id="7e7ec-211">[!code-csharp[Bibliothèque avec balises](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-211">[!code-csharp[Tagged Library](../../samples/snippets/csharp/concepts/codedoc/tagged-library.cs)]</span></span>

<span data-ttu-id="7e7ec-212">À partir de votre code, vous pouvez générer un site web de documentation détaillée complet avec des références croisées interactives.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-212">From your code, you can generate a detailed documentation website complete with clickable cross-references.</span></span> <span data-ttu-id="7e7ec-213">Vous êtes maintenant confronté à un autre problème : votre code est devenu difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-213">But you're faced with another problem: your code has become hard to read.</span></span>
<span data-ttu-id="7e7ec-214">Avec toutes ces informations à parcourir, cela va être un cauchemar pour les développeurs qui veulent contribuer à ce code.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-214">There's so much information to sift through that this is going to be a nightmare for any developer who wants to contribute to this code.</span></span> <span data-ttu-id="7e7ec-215">Heureusement, il existe une balise XML qui peut vous aider à gérer ce problème :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-215">Thankfully there's an XML tag that can help you deal with this:</span></span>

### <a name="ltincludegt"></a><span data-ttu-id="7e7ec-216">&lt;include&gt;</span><span class="sxs-lookup"><span data-stu-id="7e7ec-216">&lt;include&gt;</span></span>

<span data-ttu-id="7e7ec-217">La balise `<include>` vous permet de faire référence à des commentaires se trouvant dans un fichier XML distinct et décrivant les types et les membres de votre code source au lieu de placer des commentaires de documentation directement dans votre fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-217">The `<include>` tag lets you refer to comments in a separate XML file that describe the types and members in your source code, as opposed to placing documentation comments directly in your source code file.</span></span>

<span data-ttu-id="7e7ec-218">Vous allez maintenant déplacer toutes vos balises XML dans un fichier XML distinct nommé `docs.xml`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-218">Now you're going to move all your XML tags into a separate XML file named `docs.xml`.</span></span> <span data-ttu-id="7e7ec-219">Vous pouvez nommer ce fichier comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-219">Feel free to name the file whatever you want.</span></span>

<span data-ttu-id="7e7ec-220">[!code-xml[Exemple de code XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-220">[!code-xml[Sample XML](../../samples/snippets/csharp/concepts/codedoc/include.xml)]</span></span>

<span data-ttu-id="7e7ec-221">Dans le code XML ci-dessus, les commentaires de documentation de chaque membre apparaissent directement dans une balise nommée en fonction de ce qu’il fait.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-221">In the above XML, each member's documentation comments appear directly inside a tag named after what they do.</span></span> <span data-ttu-id="7e7ec-222">Vous pouvez choisir votre propre stratégie.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-222">You can choose your own strategy.</span></span> <span data-ttu-id="7e7ec-223">Maintenant que vous avez vos commentaires XML dans un fichier distinct, voyons comment votre code peut être rendu plus lisible à l’aide de la balise `<include>` :</span><span class="sxs-lookup"><span data-stu-id="7e7ec-223">Now that you have your XML comments in a separate file, let's see how your code can be made more readable by using the `<include>` tag:</span></span>

<span data-ttu-id="7e7ec-224">[!code-csharp[Balise include](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]</span><span class="sxs-lookup"><span data-stu-id="7e7ec-224">[!code-csharp[Include Tag](../../samples/snippets/csharp/concepts/codedoc/include-tag.cs)]</span></span>

<span data-ttu-id="7e7ec-225">Et voilà : notre code est à nouveau lisible, et aucune information de documentation n’a été perdue.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-225">And there you have it: our code is back to being readable, and no documentation information has been lost.</span></span> 

<span data-ttu-id="7e7ec-226">L’attribut `filename` représente le nom du fichier XML contenant la documentation.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-226">The `filename` attribute represents the name of the XML file containing the documentation.</span></span>

<span data-ttu-id="7e7ec-227">L’attribut `path` représente une requête [XPath](https://msdn.microsoft.com/library/ms256115.aspx) au `tag name` présent dans le `filename` spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-227">The `path` attribute represents an [XPath](https://msdn.microsoft.com/library/ms256115.aspx) query to the `tag name` present in the specified `filename`.</span></span>

<span data-ttu-id="7e7ec-228">L’attribut `name` représente le spécificateur de nom dans la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-228">The `name` attribute represents the name specifier in the tag that precedes the comments.</span></span>

<span data-ttu-id="7e7ec-229">L’attribut `id` qui peut être utilisé à la place de `name` représente l’ID de la balise qui précède les commentaires.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-229">The `id` attribute which can be used in place of `name` represents the ID for the tag that precedes the comments.</span></span>

### <a name="user-defined-tags"></a><span data-ttu-id="7e7ec-230">Balises définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e7ec-230">User Defined Tags</span></span>

<span data-ttu-id="7e7ec-231">Toutes les balises décrites ci-dessus représentent celles qui sont reconnues par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-231">All the tags outlined above represent those that are recognized by the C# compiler.</span></span> <span data-ttu-id="7e7ec-232">Toutefois, un utilisateur est libre de définir ses propres balises.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-232">However, a user is free to define their own tags.</span></span>
<span data-ttu-id="7e7ec-233">Des outils tels que Sandcastle permettent de prendre en charge des balises supplémentaires telles que [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) et prennent même en charge la [documentation des espaces de noms](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span><span class="sxs-lookup"><span data-stu-id="7e7ec-233">Tools like Sandcastle bring support for extra tags like [`<event>`](http://ewsoftware.github.io/XMLCommentsGuide/html/81bf7ad3-45dc-452f-90d5-87ce2494a182.htm), [`<note>`](http://ewsoftware.github.io/XMLCommentsGuide/html/4302a60f-e4f4-4b8d-a451-5f453c4ebd46.htm) and even support [documenting namespaces](http://ewsoftware.github.io/XMLCommentsGuide/html/BD91FAD4-188D-4697-A654-7C07FD47EF31.htm).</span></span>
<span data-ttu-id="7e7ec-234">Des outils de génération de documentation personnalisés ou internes peuvent également être utilisés avec les balises standard, et plusieurs formats de sortie, du format HTML au format PDF, peuvent être pris en charge.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-234">Custom or in-house documentation generation tools can also be used with the standard tags and multiple output formats from HTML to PDF can be supported.</span></span>

## <a name="recommendations"></a><span data-ttu-id="7e7ec-235">Recommandations</span><span class="sxs-lookup"><span data-stu-id="7e7ec-235">Recommendations</span></span>

<span data-ttu-id="7e7ec-236">La documentation du code est recommandée pour de nombreuses raisons.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-236">Documenting code is recommended for many reasons.</span></span> <span data-ttu-id="7e7ec-237">Voici quelques bonnes pratiques, des scénarios de cas d’usage généraux et des éléments que vous devez connaître quand vous utilisez des balises de documentation XML dans votre code C#.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-237">What follows are some best practices, general use case scenarios, and things that you should know when using XML documentation tags in your C# code.</span></span>

* <span data-ttu-id="7e7ec-238">Par souci de cohérence, tous les types visibles publiquement et leurs membres doivent être documentés.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-238">For the sake of consistency, all publicly visible types and their members should be documented.</span></span> <span data-ttu-id="7e7ec-239">Si vous devez le faire, faites-le complètement.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-239">If you must do it, do it all.</span></span>
* <span data-ttu-id="7e7ec-240">Les membres privés peuvent également être documentés à l’aide de commentaires XML.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-240">Private members can also be documented using XML comments.</span></span> <span data-ttu-id="7e7ec-241">Toutefois, cela expose le fonctionnement interne (potentiellement confidentiel) de votre bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-241">However, this exposes the inner (potentially confidential) workings of your library.</span></span>
* <span data-ttu-id="7e7ec-242">Au minimum, les types et leurs membres doivent avoir une balise `<summary>`, car son contenu est nécessaire pour IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-242">At a bare minimum, types and their members should have a `<summary>` tag because its content is needed for IntelliSense.</span></span>
* <span data-ttu-id="7e7ec-243">Le texte de la documentation doit être écrit à l’aide de phrases complètes se terminant par un point.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-243">Documentation text should be written using complete sentences ending with full stops.</span></span>
* <span data-ttu-id="7e7ec-244">Les classes partielles sont entièrement prises en charge, et les informations de documentation seront concaténées dans une seule entrée pour ce type.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-244">Partial classes are fully supported, and documentation information will be concatenated into a single entry for that type.</span></span>
* <span data-ttu-id="7e7ec-245">Le compilateur vérifie la syntaxe des balises `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` et `<typeparam>`.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-245">The compiler verifies the syntax of the `<exception>`, `<include>`, `<param>`, `<see>`, `<seealso>` and `<typeparam>` tags.</span></span>
- <span data-ttu-id="7e7ec-246">Le compilateur valide les paramètres qui contiennent des chemins de fichiers et des références à d’autres parties du code.</span><span class="sxs-lookup"><span data-stu-id="7e7ec-246">The compiler validates the parameters that contain file paths and references to other parts of the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e7ec-247">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e7ec-247">See also</span></span>
[<span data-ttu-id="7e7ec-248">Commentaires de documentation XML (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7e7ec-248">XML Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/xml-documentation-comments.md)

[<span data-ttu-id="7e7ec-249">Balises recommandées pour les commentaires de documentation (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7e7ec-249">Recommended Tags for Documentation Comments (C# Programming Guide)</span></span>](programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

