---
title: "L’attribut &quot;Extension&quot; peut être appliqué qu’aux déclarations &quot;Module&quot;, &quot;Sub&quot; ou &quot;Function&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
dev_langs:
- VB
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e88241180fe1320bfd1db90a38a9a7560ae3dead
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="0c782-102">L’attribut 'Extension' peut être appliqué qu’aux déclarations 'Module', 'Sub' ou 'Function'</span><span class="sxs-lookup"><span data-stu-id="0c782-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="0c782-103">La seule façon d’étendre un type de données dans Visual Basic consiste à définir une méthode d’extension à l’intérieur d’un module standard.</span><span class="sxs-lookup"><span data-stu-id="0c782-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="0c782-104">La méthode d’extension peut être un `Sub` procédure ou d’un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="0c782-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="0c782-105">Toutes les méthodes d’extension doivent être marquées avec l’attribut d’extension, `<Extension()>`, à partir de la <xref:System.Runtime.CompilerServices?displayProperty=fullName>espace de noms.</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0c782-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace.</span></span> <span data-ttu-id="0c782-106">Éventuellement, un module qui contient une méthode d’extension peut être marqué de la même façon.</span><span class="sxs-lookup"><span data-stu-id="0c782-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="0c782-107">Aucune autre utilisation de l’attribut d’extension n’est valide.</span><span class="sxs-lookup"><span data-stu-id="0c782-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="0c782-108">**ID d’erreur :** BC36550</span><span class="sxs-lookup"><span data-stu-id="0c782-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c782-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0c782-109">To correct this error</span></span>  
  
-   <span data-ttu-id="0c782-110">Supprimez l’attribut d’extension.</span><span class="sxs-lookup"><span data-stu-id="0c782-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="0c782-111">Reconcevez votre extension en tant que méthode, définie dans un module englobant.</span><span class="sxs-lookup"><span data-stu-id="0c782-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c782-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="0c782-112">Example</span></span>  
 <span data-ttu-id="0c782-113">L’exemple suivant définit un `Print` méthode pour le `String` type de données.</span><span class="sxs-lookup"><span data-stu-id="0c782-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="0c782-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c782-114">See Also</span></span>  
 <span data-ttu-id="0c782-115">[Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span><span class="sxs-lookup"><span data-stu-id="0c782-115">[Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md) </span></span>  
<span data-ttu-id="0c782-116"> [Méthodes d’extension](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span><span class="sxs-lookup"><span data-stu-id="0c782-116"> [Extension Methods](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) </span></span>  
<span data-ttu-id="0c782-117"> [Module (instruction)](../../../visual-basic/language-reference/statements/module-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0c782-117"> [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)</span></span>

