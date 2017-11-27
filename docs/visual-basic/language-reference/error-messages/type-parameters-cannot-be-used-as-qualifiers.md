---
title: "Les paramètres de type ne peuvent pas être utilisés comme qualificateurs"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32098
- bc32098
helpviewer_keywords: BC32098
ms.assetid: bab05325-dde8-4621-a5f6-368b5b7b2d76
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 58be51e0c05750ee044f0287cde8db037718b4aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-parameters-cannot-be-used-as-qualifiers"></a><span data-ttu-id="3f126-102">Les paramètres de type ne peuvent pas être utilisés comme qualificateurs</span><span class="sxs-lookup"><span data-stu-id="3f126-102">Type parameters cannot be used as qualifiers</span></span>
<span data-ttu-id="3f126-103">Un élément de programmation est qualifié avec une chaîne de qualification qui inclut un paramètre de type.</span><span class="sxs-lookup"><span data-stu-id="3f126-103">A programming element is qualified with a qualification string that includes a type parameter.</span></span>  
  
 <span data-ttu-id="3f126-104">Un paramètre de type représente une exigence pour un type qui doit être fourni lorsque le type générique est construit.</span><span class="sxs-lookup"><span data-stu-id="3f126-104">A type parameter represents a requirement for a type that is to be supplied when the generic type is constructed.</span></span> <span data-ttu-id="3f126-105">Il ne représente pas un type défini spécifique.</span><span class="sxs-lookup"><span data-stu-id="3f126-105">It does not represent a specific defined type.</span></span> <span data-ttu-id="3f126-106">Une chaîne de qualification doit inclure uniquement les éléments qui sont définis au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="3f126-106">A qualification string must include only elements that are defined at compile time.</span></span>  
  
 <span data-ttu-id="3f126-107">Les instructions suivantes peuvent générer cette erreur.</span><span class="sxs-lookup"><span data-stu-id="3f126-107">The following statements can generate this error.</span></span>  
  
```  
Public Function checkText(Of c As System.Windows.Forms.Control)(  
    ByVal badText As String) As Boolean  
  
    Dim saveText As c.Text  
    ' Insert code to look for badText within saveText.  
End Function  
```  
  
 <span data-ttu-id="3f126-108">**ID d’erreur :** BC32098</span><span class="sxs-lookup"><span data-stu-id="3f126-108">**Error ID:** BC32098</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3f126-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="3f126-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="3f126-110">Supprimez le paramètre de type de la chaîne de qualification ou remplacez-le par un type défini.</span><span class="sxs-lookup"><span data-stu-id="3f126-110">Remove the type parameter from the qualification string, or replace it with a defined type.</span></span>  
  
2.  <span data-ttu-id="3f126-111">Si vous devez utiliser un type construit pour rechercher l’élément de programmation qualifié, vous devez utiliser la logique de programme supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="3f126-111">If you need to use a constructed type to locate the programming element being qualified, you must use additional program logic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f126-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f126-112">See Also</span></span>  
 [<span data-ttu-id="3f126-113">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="3f126-113">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="3f126-114">Types génériques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f126-114">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="3f126-115">Liste de types</span><span class="sxs-lookup"><span data-stu-id="3f126-115">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
