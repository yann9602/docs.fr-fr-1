---
title: "Guide pratique pour utiliser l’espace de noms My (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: 12
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
ms.openlocfilehash: 56577ff61c3f637c8e5a0969ae75d65d24ddaef7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="2bf08-102">Guide pratique pour utiliser l’espace de noms My (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2bf08-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="2bf08-103">L’espace de noms <xref:Microsoft.VisualBasic.MyServices> (`My` en Visual Basic) permet d’accéder de manière simple et intuitive à un certain nombre de classes .NET Framework, ce qui vous permet d’écrire du code qui interagit avec l’ordinateur, l’application, les paramètres, les ressources, etc.</span><span class="sxs-lookup"><span data-stu-id="2bf08-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="2bf08-104">Bien que conçu à l’origine pour une utilisation avec Visual Basic, l’espace de noms `MyServices` peut être utilisé dans les applications C#.</span><span class="sxs-lookup"><span data-stu-id="2bf08-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="2bf08-105">Pour plus d’informations sur l’utilisation de l’espace de noms `MyServices` de Visual Basic, consultez [Développement avec My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bf08-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="2bf08-106">Ajout d’une référence</span><span class="sxs-lookup"><span data-stu-id="2bf08-106">Adding a Reference</span></span>  
 <span data-ttu-id="2bf08-107">Pour pouvoir utiliser les classes `MyServices` dans votre solution, vous devez d’abord ajouter une référence à la bibliothèque Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2bf08-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="2bf08-108">Pour ajouter une référence à la bibliothèque Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2bf08-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="2bf08-109">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="2bf08-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="2bf08-110">Une fois la boîte de dialogue **Références** affichée, faites défiler la liste et sélectionnez Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="2bf08-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="2bf08-111">Vous pouvez aussi inclure la ligne suivante de la section `using` au début de votre programme.</span><span class="sxs-lookup"><span data-stu-id="2bf08-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     <span data-ttu-id="2bf08-112">[!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bf08-112">[!code-cs[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf08-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2bf08-113">Example</span></span>  
 <span data-ttu-id="2bf08-114">Cet exemple appelle plusieurs méthodes statiques contenues dans l’espace de noms `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="2bf08-114">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="2bf08-115">Pour compiler ce code, une référence à Microsoft.VisualBasic.DLL doit être ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="2bf08-115">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 <span data-ttu-id="2bf08-116">[!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bf08-116">[!code-cs[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]</span></span>  
  
 <span data-ttu-id="2bf08-117">Certaines classes de l’espace de noms `MyServices` ne peuvent pas être appelées à partir d’une application C# : par exemple, la classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> n’est pas compatible.</span><span class="sxs-lookup"><span data-stu-id="2bf08-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="2bf08-118">Dans ce cas particulier, les méthodes statiques, qui font partie intégrante de <xref:Microsoft.VisualBasic.FileIO.FileSystem> et qui sont aussi contenues dans VisualBasic.dll, peuvent être utilisées à la place.</span><span class="sxs-lookup"><span data-stu-id="2bf08-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="2bf08-119">Par exemple, voici comment utiliser une méthode de ce type pour dupliquer un répertoire :</span><span class="sxs-lookup"><span data-stu-id="2bf08-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 <span data-ttu-id="2bf08-120">[!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2bf08-120">[!code-cs[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf08-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bf08-121">See Also</span></span>  
 <span data-ttu-id="2bf08-122">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bf08-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2bf08-123">[Espaces de noms](../../../csharp/programming-guide/namespaces/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bf08-123">[Namespaces](../../../csharp/programming-guide/namespaces/index.md) </span></span>  
 [<span data-ttu-id="2bf08-124">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="2bf08-124">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)

