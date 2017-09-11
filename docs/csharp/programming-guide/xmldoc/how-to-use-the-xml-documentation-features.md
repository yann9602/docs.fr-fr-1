---
title: "Guide pratique pour utiliser les fonctionnalités de la documentation XML (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: eeee77db523bc0ad97f425d4ba8076ae5740dfe8
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a><span data-ttu-id="a2917-102">Guide pratique pour utiliser les fonctionnalités de la documentation XML (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a2917-102">How to: Use the XML Documentation Features (C# Programming Guide)</span></span>
<span data-ttu-id="a2917-103">L’exemple suivant montre un type qui a été documenté.</span><span class="sxs-lookup"><span data-stu-id="a2917-103">The following sample provides a basic overview of a type that has been documented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2917-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="a2917-104">Example</span></span>  
 <span data-ttu-id="a2917-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="a2917-105">[!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]</span></span>  
  
 <span data-ttu-id="a2917-106">**// Ce fichier .xml a été généré avec l’exemple de code précédent.**</span><span class="sxs-lookup"><span data-stu-id="a2917-106">**// This .xml file was generated with the previous code sample.**</span></span>  
<span data-ttu-id="a2917-107">**\<?xml version="1.0"?>**</span><span class="sxs-lookup"><span data-stu-id="a2917-107">**\<?xml version="1.0"?>**</span></span>  
<span data-ttu-id="a2917-108">**\<doc>**</span><span class="sxs-lookup"><span data-stu-id="a2917-108">**\<doc>**</span></span>  
 <span data-ttu-id="a2917-109">**\<assembly>**</span><span class="sxs-lookup"><span data-stu-id="a2917-109">**\<assembly>**</span></span>  
 <span data-ttu-id="a2917-110">**\<name>xmlsample\</name>**</span><span class="sxs-lookup"><span data-stu-id="a2917-110">**\<name>xmlsample\</name>**</span></span>  
 <span data-ttu-id="a2917-111">**\</assembly>**</span><span class="sxs-lookup"><span data-stu-id="a2917-111">**\</assembly>**</span></span>  
 <span data-ttu-id="a2917-112">**\<members>**</span><span class="sxs-lookup"><span data-stu-id="a2917-112">**\<members>**</span></span>  
 <span data-ttu-id="a2917-113">**\<member name="T:SomeClass">**</span><span class="sxs-lookup"><span data-stu-id="a2917-113">**\<member name="T:SomeClass">**</span></span>  
 <span data-ttu-id="a2917-114">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-114">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-115">**Insérer ici les informations récapitulatives relatives à la classe.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-115">**Class level summary documentation goes here.\</summary>**</span></span>  
 <span data-ttu-id="a2917-116">**\<remarks>**</span><span class="sxs-lookup"><span data-stu-id="a2917-116">**\<remarks>**</span></span>  
 <span data-ttu-id="a2917-117">**Des commentaires plus longs peuvent être associés à un type ou à un membre** </span><span class="sxs-lookup"><span data-stu-id="a2917-117">**Longer comments can be associated with a type or member** </span></span>  
 <span data-ttu-id="a2917-118">**grâce à la balise remarks\</remarks>**</span><span class="sxs-lookup"><span data-stu-id="a2917-118">**through the remarks tag\</remarks>**</span></span>  
 <span data-ttu-id="a2917-119">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-119">**\</member>**</span></span>  
 <span data-ttu-id="a2917-120">**\<member name="F:SomeClass.m_Name">**</span><span class="sxs-lookup"><span data-stu-id="a2917-120">**\<member name="F:SomeClass.m_Name">**</span></span>  
 <span data-ttu-id="a2917-121">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-121">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-122">**Stocke la propriété name\</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-122">**Store for the name property\</summary>**</span></span>  
 <span data-ttu-id="a2917-123">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-123">**\</member>**</span></span>  
 <span data-ttu-id="a2917-124">**\<member name="M:SomeClass.#ctor">**</span><span class="sxs-lookup"><span data-stu-id="a2917-124">**\<member name="M:SomeClass.#ctor">**</span></span>  
 <span data-ttu-id="a2917-125">**\<summary>Le constructeur de classe.\</summary>** </span><span class="sxs-lookup"><span data-stu-id="a2917-125">**\<summary>The class constructor.\</summary>** </span></span>  
 <span data-ttu-id="a2917-126">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-126">**\</member>**</span></span>  
 <span data-ttu-id="a2917-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="a2917-127">**\<member name="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="a2917-128">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-128">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-129">**Description de la méthode SomeMethod.\</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-129">**Description for SomeMethod.\</summary>**</span></span>  
 <span data-ttu-id="a2917-130">**\<param name="s"> Insérer ici la description du paramètre s.\</param>**</span><span class="sxs-lookup"><span data-stu-id="a2917-130">**\<param name="s"> Parameter description for s goes here\</param>**</span></span>  
 <span data-ttu-id="a2917-131">**\<seealso cref="T:System.String">**</span><span class="sxs-lookup"><span data-stu-id="a2917-131">**\<seealso cref="T:System.String">**</span></span>  
 <span data-ttu-id="a2917-132">**Vous pouvez utiliser l’attribut cref sur n’importe quelle balise pour référencer un type ou un membre** </span><span class="sxs-lookup"><span data-stu-id="a2917-132">**You can use the cref attribute on any tag to reference a type or member** </span></span>  
 <span data-ttu-id="a2917-133">**et le compilateur vérifiera que cette référence existe. \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="a2917-133">**and the compiler will check that the reference exists. \</seealso>**</span></span>  
 <span data-ttu-id="a2917-134">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-134">**\</member>**</span></span>  
 <span data-ttu-id="a2917-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span><span class="sxs-lookup"><span data-stu-id="a2917-135">**\<member name="M:SomeClass.SomeOtherMethod">**</span></span>  
 <span data-ttu-id="a2917-136">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-136">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-137">**Autre méthode quelconque. \</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-137">**Some other method. \</summary>**</span></span>  
 <span data-ttu-id="a2917-138">**\<returns>**</span><span class="sxs-lookup"><span data-stu-id="a2917-138">**\<returns>**</span></span>  
 <span data-ttu-id="a2917-139">**Les résultats retournés sont décrits grâce à la balise returns.\</returns>**</span><span class="sxs-lookup"><span data-stu-id="a2917-139">**Return results are described through the returns tag.\</returns>**</span></span>  
 <span data-ttu-id="a2917-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span><span class="sxs-lookup"><span data-stu-id="a2917-140">**\<seealso cref="M:SomeClass.SomeMethod(System.String)">**</span></span>  
 <span data-ttu-id="a2917-141">**Remarquez l’utilisation de l’attribut cref pour référencer une méthode spécifique \</seealso>**</span><span class="sxs-lookup"><span data-stu-id="a2917-141">**Notice the use of the cref attribute to reference a specific method \</seealso>**</span></span>  
 <span data-ttu-id="a2917-142">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-142">**\</member>**</span></span>  
 <span data-ttu-id="a2917-143">**\<member name="M:SomeClass.Main(System.String[])">**</span><span class="sxs-lookup"><span data-stu-id="a2917-143">**\<member name="M:SomeClass.Main(System.String[])">**</span></span>  
 <span data-ttu-id="a2917-144">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-144">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-145">**Point d’entrée de l’application.**</span><span class="sxs-lookup"><span data-stu-id="a2917-145">**The entry point for the application.**</span></span>  
 <span data-ttu-id="a2917-146">**\</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-146">**\</summary>**</span></span>  
 <span data-ttu-id="a2917-147">**\<param name="args"> Liste d’arguments de la ligne de commande\</param>**</span><span class="sxs-lookup"><span data-stu-id="a2917-147">**\<param name="args"> A list of command line arguments\</param>**</span></span>  
 <span data-ttu-id="a2917-148">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-148">**\</member>**</span></span>  
 <span data-ttu-id="a2917-149">**\<member name="P:SomeClass.Name">**</span><span class="sxs-lookup"><span data-stu-id="a2917-149">**\<member name="P:SomeClass.Name">**</span></span>  
 <span data-ttu-id="a2917-150">**\<summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-150">**\<summary>**</span></span>  
 <span data-ttu-id="a2917-151">**Propriété Name \</summary>**</span><span class="sxs-lookup"><span data-stu-id="a2917-151">**Name property \</summary>**</span></span>  
 <span data-ttu-id="a2917-152">**\<value>**</span><span class="sxs-lookup"><span data-stu-id="a2917-152">**\<value>**</span></span>  
 <span data-ttu-id="a2917-153">**Une balise value sert à décrire la valeur de la propriété\</value>**</span><span class="sxs-lookup"><span data-stu-id="a2917-153">**A value tag is used to describe the property value\</value>**</span></span>  
 <span data-ttu-id="a2917-154">**\</member>**</span><span class="sxs-lookup"><span data-stu-id="a2917-154">**\</member>**</span></span>  
 <span data-ttu-id="a2917-155">**\</members>**</span><span class="sxs-lookup"><span data-stu-id="a2917-155">**\</members>**</span></span>  
<span data-ttu-id="a2917-156">**\</doc>**</span><span class="sxs-lookup"><span data-stu-id="a2917-156">**\</doc>**</span></span>   
## <a name="compiling-the-code"></a><span data-ttu-id="a2917-157">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="a2917-157">Compiling the Code</span></span>  
 <span data-ttu-id="a2917-158">Pour compiler l’exemple, tapez ce qui suit sur la ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="a2917-158">To compile the example, type the following command line:</span></span>  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 <span data-ttu-id="a2917-159">Cela créera le fichier XML XMLsample.xml, que vous pouvez afficher dans votre navigateur ou à l’aide de la commande TYPE.</span><span class="sxs-lookup"><span data-stu-id="a2917-159">This will create the XML file XMLsample.xml, which you can view in your browser or by using the TYPE command.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a2917-160">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="a2917-160">Robust Programming</span></span>  
 <span data-ttu-id="a2917-161">Le début de la documentation XML est symbolisé par trois barres obliques (///).</span><span class="sxs-lookup"><span data-stu-id="a2917-161">XML documentation starts with ///.</span></span> <span data-ttu-id="a2917-162">Lorsque vous créez un projet, les Assistants insèrent quelques lignes de début (///) pour vous.</span><span class="sxs-lookup"><span data-stu-id="a2917-162">When you create a new project, the wizards put some starter /// lines in for you.</span></span> <span data-ttu-id="a2917-163">Le traitement de ces commentaires présente certaines restrictions :</span><span class="sxs-lookup"><span data-stu-id="a2917-163">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="a2917-164">La documentation doit être dans un format XML correct.</span><span class="sxs-lookup"><span data-stu-id="a2917-164">The documentation must be well-formed XML.</span></span> <span data-ttu-id="a2917-165">Si le XML n’est pas correct, un avertissement est généré. En outre, un commentaire indiquant qu’une erreur s’est produite est ajouté au fichier de documentation.</span><span class="sxs-lookup"><span data-stu-id="a2917-165">If the XML is not well-formed, a warning is generated and the documentation file will contain a comment that says that an error was encountered.</span></span>  
  
-   <span data-ttu-id="a2917-166">Les développeurs sont libres de créer leur propre jeu de balises.</span><span class="sxs-lookup"><span data-stu-id="a2917-166">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="a2917-167">Il existe un jeu de balises recommandé (voir la section « Informations supplémentaires »).</span><span class="sxs-lookup"><span data-stu-id="a2917-167">There is a recommended set of tags (see the Further Reading section).</span></span> <span data-ttu-id="a2917-168">Certaines des balises recommandées ont des significations spéciales :</span><span class="sxs-lookup"><span data-stu-id="a2917-168">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="a2917-169">La balise \<param> est utilisée pour décrire les paramètres.</span><span class="sxs-lookup"><span data-stu-id="a2917-169">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="a2917-170">Quand elle est utilisée, le compilateur vérifie que le paramètre existe et que tous les paramètres sont décrits dans la documentation.</span><span class="sxs-lookup"><span data-stu-id="a2917-170">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="a2917-171">Si ce n’est pas le cas, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a2917-171">If the verification failed, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="a2917-172">L’attribut `cref` peut être joint à n’importe quelle balise pour fournir une référence à un élément de code.</span><span class="sxs-lookup"><span data-stu-id="a2917-172">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="a2917-173">Le compilateur vérifie l’existence de cet élément de code.</span><span class="sxs-lookup"><span data-stu-id="a2917-173">The compiler will verify that this code element exists.</span></span> <span data-ttu-id="a2917-174">Si ce n’est pas le cas, le compilateur émet un avertissement.</span><span class="sxs-lookup"><span data-stu-id="a2917-174">If the verification failed, the compiler issues a warning.</span></span> <span data-ttu-id="a2917-175">Le compilateur respecte toutes les instructions `using` lorsqu’il recherche un type décrit dans l’attribut `cref`.</span><span class="sxs-lookup"><span data-stu-id="a2917-175">The compiler respects any `using` statements when it looks for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="a2917-176">La balise \<summary> est utilisée par IntelliSense dans Visual Studio pour afficher des informations supplémentaires sur un type ou un membre.</span><span class="sxs-lookup"><span data-stu-id="a2917-176">The \<summary> tag is used by IntelliSense inside Visual Studio to display additional information about a type or member.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="a2917-177">Le fichier XML ne fournit pas des informations complètes sur le type et les membres (par exemple, il ne contient pas d’informations sur le type).</span><span class="sxs-lookup"><span data-stu-id="a2917-177">The XML file does not provide full information about the type and members (for example, it does not contain any type information).</span></span> <span data-ttu-id="a2917-178">Pour obtenir des informations complètes sur un type ou sur un membre, le fichier de documentation doit être utilisé avec la réflexion sur le type ou sur le membre.</span><span class="sxs-lookup"><span data-stu-id="a2917-178">To get full information about a type or member, the documentation file must be used together with reflection on the actual type or member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2917-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2917-179">See Also</span></span>  
 <span data-ttu-id="a2917-180">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="a2917-180">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="a2917-181">[/doc (Options du compilateur C#)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span><span class="sxs-lookup"><span data-stu-id="a2917-181">[/doc (C# Compiler Options)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) </span></span>  
 [<span data-ttu-id="a2917-182">Commentaires sur la documentation XML</span><span class="sxs-lookup"><span data-stu-id="a2917-182">XML Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)

