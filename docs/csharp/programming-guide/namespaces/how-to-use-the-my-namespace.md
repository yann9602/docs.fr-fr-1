---
title: "Comment : utiliser l'espace de noms My (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f3564c594a5fbb9bd05a956e5c12bbb173d2db51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="717fa-102">Comment : utiliser l'espace de noms My (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="717fa-102">How to: Use the My Namespace (C# Programming Guide)</span></span>
<span data-ttu-id="717fa-103">L’espace de noms <xref:Microsoft.VisualBasic.MyServices> (`My` en Visual Basic) permet d’accéder de manière simple et intuitive à un certain nombre de classes .NET Framework, ce qui vous permet d’écrire du code qui interagit avec l’ordinateur, l’application, les paramètres, les ressources, etc.</span><span class="sxs-lookup"><span data-stu-id="717fa-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="717fa-104">Bien que conçu à l’origine pour une utilisation avec Visual Basic, l’espace de noms `MyServices` peut être utilisé dans les applications C#.</span><span class="sxs-lookup"><span data-stu-id="717fa-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="717fa-105">Pour plus d’informations sur l’utilisation de l’espace de noms `MyServices` de Visual Basic, consultez [Développement avec My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="717fa-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="717fa-106">Ajout d’une référence</span><span class="sxs-lookup"><span data-stu-id="717fa-106">Adding a Reference</span></span>  
 <span data-ttu-id="717fa-107">Pour pouvoir utiliser les classes `MyServices` dans votre solution, vous devez d’abord ajouter une référence à la bibliothèque Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="717fa-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="717fa-108">Pour ajouter une référence à la bibliothèque Visual Basic</span><span class="sxs-lookup"><span data-stu-id="717fa-108">To add a reference to the Visual Basic library</span></span>  
  
1.  <span data-ttu-id="717fa-109">Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le nœud **Références**, puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="717fa-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="717fa-110">Une fois la boîte de dialogue **Références** affichée, faites défiler la liste et sélectionnez Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="717fa-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="717fa-111">Vous pouvez aussi inclure la ligne suivante de la section `using` au début de votre programme.</span><span class="sxs-lookup"><span data-stu-id="717fa-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="717fa-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="717fa-112">Example</span></span>  
 <span data-ttu-id="717fa-113">Cet exemple appelle plusieurs méthodes statiques contenues dans l’espace de noms `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="717fa-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="717fa-114">Pour compiler ce code, une référence à Microsoft.VisualBasic.DLL doit être ajoutée au projet.</span><span class="sxs-lookup"><span data-stu-id="717fa-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_2.cs)]  
  
 <span data-ttu-id="717fa-115">Certaines classes de l’espace de noms `MyServices` ne peuvent pas être appelées à partir d’une application C# : par exemple, la classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> n’est pas compatible.</span><span class="sxs-lookup"><span data-stu-id="717fa-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="717fa-116">Dans ce cas particulier, les méthodes statiques, qui font partie intégrante de <xref:Microsoft.VisualBasic.FileIO.FileSystem> et qui sont aussi contenues dans VisualBasic.dll, peuvent être utilisées à la place.</span><span class="sxs-lookup"><span data-stu-id="717fa-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="717fa-117">Par exemple, voici comment utiliser une méthode de ce type pour dupliquer un répertoire :</span><span class="sxs-lookup"><span data-stu-id="717fa-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](../../../csharp/programming-guide/namespaces/codesnippet/CSharp/how-to-use-the-my-namespace_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="717fa-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="717fa-118">See Also</span></span>  
 [<span data-ttu-id="717fa-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="717fa-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="717fa-120">Espaces de noms</span><span class="sxs-lookup"><span data-stu-id="717fa-120">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)  
 [<span data-ttu-id="717fa-121">Utilisation d’espaces de noms</span><span class="sxs-lookup"><span data-stu-id="717fa-121">Using Namespaces</span></span>](../../../csharp/programming-guide/namespaces/using-namespaces.md)
