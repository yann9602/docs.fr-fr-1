---
title: '&lt;summary&gt; (Guide de programmation C#)'
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <summary>
- summary
dev_langs:
- CSharp
helpviewer_keywords:
- <summary> C# XML tag
- summary C# XML tag
ms.assetid: b4c43d92-2067-4eac-a59a-d32f5248c08b
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: bd96e58494196fcfdeb46e9e59481666ec9466f3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="ltsummarygt-c-programming-guide"></a><span data-ttu-id="c512c-102">&lt;summary&gt; (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c512c-102">&lt;summary&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="c512c-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c512c-103">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c512c-104">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c512c-104">Parameters</span></span>  
 `description`  
 <span data-ttu-id="c512c-105">Résumé de l’objet.</span><span class="sxs-lookup"><span data-stu-id="c512c-105">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c512c-106">Remarques</span><span class="sxs-lookup"><span data-stu-id="c512c-106">Remarks</span></span>  
 <span data-ttu-id="c512c-107">La balise \<summary> doit être utilisée pour décrire un type ou un membre de type.</span><span class="sxs-lookup"><span data-stu-id="c512c-107">The \<summary> tag should be used to describe a type or a type member.</span></span> <span data-ttu-id="c512c-108">Utilisez [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) pour ajouter des informations supplémentaires à une description de type.</span><span class="sxs-lookup"><span data-stu-id="c512c-108">Use [\<remarks>](../../../csharp/programming-guide/xmldoc/remarks.md) to add supplemental information to a type description.</span></span> <span data-ttu-id="c512c-109">Utilisez l’[attribut cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) pour activer des outils de documentation tels que [Sandcastle](https://github.com/EWSoftware/SHFB) afin de créer des liens hypertexte internes aux pages de documentation pour les éléments de code.</span><span class="sxs-lookup"><span data-stu-id="c512c-109">Use the [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) to enable documentation tools such as [Sandcastle](https://github.com/EWSoftware/SHFB) to create internal hyperlinks to documentation pages for code elements.</span></span>  
  
 <span data-ttu-id="c512c-110">Le texte de la balise \<summary> est la seule source d’informations sur le type dans IntelliSense et il est également affiché dans la fenêtre Explorateur d’objets.</span><span class="sxs-lookup"><span data-stu-id="c512c-110">The text for the \<summary> tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser Window.</span></span>  
  
 <span data-ttu-id="c512c-111">Compilez avec [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pour placer les commentaires de documentation dans un fichier en vue de les traiter.</span><span class="sxs-lookup"><span data-stu-id="c512c-111">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span> <span data-ttu-id="c512c-112">Pour créer la documentation finale basée sur le fichier généré par le compilateur, vous pouvez créer un outil personnalisé ou utiliser un outil tel que [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="c512c-112">To create the final documentation based on the compiler-generated file, you can create a custom tool, or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c512c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="c512c-113">Example</span></span>  
 <span data-ttu-id="c512c-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="c512c-114">[!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_1.cs)]</span></span>  
  
 <span data-ttu-id="c512c-115">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="c512c-115">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:DotNetEvents.TestClass">  
            text for class TestClass  
        </member>  
        <member name="M:DotNetEvents.TestClass.DoWork(System.Int32)">  
            <summary>DoWork is a method in the TestClass class.  
            <para>Here's how you could make a second paragraph in a description. <see cref="M:System.Console.WriteLine(System.String)"/> for information about output statements.</para>  
            <seealso cref="M:DotNetEvents.TestClass.Main"/>  
            </summary>  
        </member>  
        <member name="M:DotNetEvents.TestClass.Main">  
            text for Main  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="example"></a><span data-ttu-id="c512c-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="c512c-116">Example</span></span>  
 <span data-ttu-id="c512c-117">L’exemple suivant montre comment effectuer une référence `cref` à un type générique.</span><span class="sxs-lookup"><span data-stu-id="c512c-117">The following example shows how to make a `cref` reference to a generic type.</span></span>  
  
 <span data-ttu-id="c512c-118">[!code-cs[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="c512c-118">[!code-cs[csProgGuideDocComments#11](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/summary_2.cs)]</span></span>  
  
 <span data-ttu-id="c512c-119">L’exemple précédent génère le fichier XML suivant.</span><span class="sxs-lookup"><span data-stu-id="c512c-119">The previous example produces the following XML file.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<doc>  
    <assembly>  
        <name>YourNamespace</name>  
    </assembly>  
    <members>  
        <member name="T:ExtensionMethodsDemo1.A">  
            <summary cref="T:ExtensionMethodsDemo1.C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.B">  
            <summary cref="T:C`1">  
            </summary>  
        </member>  
        <member name="T:ExtensionMethodsDemo1.C`1">  
            <summary cref="T:ExtensionMethodsDemo1.A">  
            </summary>  
            <typeparam name="T"></typeparam>  
        </member>  
    </members>  
</doc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c512c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c512c-120">See Also</span></span>  
 <span data-ttu-id="c512c-121">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="c512c-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="c512c-122">Balises recommandées pour les commentaires de documentation</span><span class="sxs-lookup"><span data-stu-id="c512c-122">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

