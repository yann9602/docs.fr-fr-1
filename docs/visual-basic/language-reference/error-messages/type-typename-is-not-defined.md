---
title: "Type &quot;&lt;typename&gt;&quot; n’est pas défini | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 55b76e9d080a2e2e9fe6e9737a713524ea6409f6
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a><span data-ttu-id="cb57e-102">Type '&lt;typename&gt;' n’est pas défini</span><span class="sxs-lookup"><span data-stu-id="cb57e-102">Type &#39;&lt;typename&gt;&#39; is not defined</span></span>
<span data-ttu-id="cb57e-103">L’instruction a fait référence à un type qui n’a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="cb57e-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="cb57e-104">Vous pouvez définir un type dans une instruction de déclaration, tel que `Enum`, `Structure`, `Class`, ou `Interface`.</span><span class="sxs-lookup"><span data-stu-id="cb57e-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>  
  
 <span data-ttu-id="cb57e-105">**ID d’erreur :** BC30002</span><span class="sxs-lookup"><span data-stu-id="cb57e-105">**Error ID:** BC30002</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cb57e-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="cb57e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="cb57e-107">Vérifiez que la définition de type et sa référence utilisent tous deux la même orthographe.</span><span class="sxs-lookup"><span data-stu-id="cb57e-107">Ensure that the type definition and its reference both use the same spelling.</span></span>  
  
-   <span data-ttu-id="cb57e-108">Assurez-vous que la définition de type est accessible à la référence.</span><span class="sxs-lookup"><span data-stu-id="cb57e-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="cb57e-109">Par exemple, si le type est dans un autre module et a été déclaré `Private`, déplacez la définition de type vers le module de référence ou déclarez-le `Public`.</span><span class="sxs-lookup"><span data-stu-id="cb57e-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>  
  
-   <span data-ttu-id="cb57e-110">Assurez-vous que l’espace de noms du type n’est pas redéfinie dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="cb57e-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="cb57e-111">Dans le cas, utilisez le `Global` (mot clé) pour qualifier complètement le nom de type.</span><span class="sxs-lookup"><span data-stu-id="cb57e-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="cb57e-112">Par exemple, si un projet définit un espace de noms `System`, le <xref:System.Object?displayProperty=fullName>type n’est pas accessible sauf s’il est qualifié avec le `Global` mot clé : `Global.System.Object`.</xref:System.Object?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cb57e-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=fullName> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>  
  
-   <span data-ttu-id="cb57e-113">Si le type est défini, mais la bibliothèque d’objets ou la bibliothèque de type dans lequel il est défini n’est pas enregistré dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], cliquez sur **ajouter une référence** sur la **projet** menu, puis sélectionnez la bibliothèque d’objets appropriée ou la bibliothèque de types.</span><span class="sxs-lookup"><span data-stu-id="cb57e-113">If the type is defined, but the object library or type library in which it is defined is not registered in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>  
  
-   <span data-ttu-id="cb57e-114">Assurez-vous que le type est dans un assembly qui fait partie du profil .NET Framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="cb57e-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="cb57e-115">Pour plus d’informations, consultez [erreurs de ciblage de .NET Framework dépannage](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="cb57e-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb57e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb57e-116">See Also</span></span>  
 <span data-ttu-id="cb57e-117">[Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="cb57e-117">[Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="cb57e-118"> [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb57e-118"> [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md) </span></span>  
<span data-ttu-id="cb57e-119"> [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb57e-119"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md) </span></span>  
<span data-ttu-id="cb57e-120"> [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb57e-120"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="cb57e-121"> [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="cb57e-121"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="cb57e-122"> [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span><span class="sxs-lookup"><span data-stu-id="cb57e-122"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)</span></span>
