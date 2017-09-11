---
title: "Guide pratique pour effectuer une conversion entre un codage hérité et Unicode (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
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
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a><span data-ttu-id="eb1ed-102">Guide pratique pour effectuer une conversion entre un codage hérité et Unicode (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="eb1ed-102">How to: Convert Between Legacy Encodings and Unicode (C# Programming Guide)</span></span>
<span data-ttu-id="eb1ed-103">En C#, toutes les chaînes en mémoire sont encodées au format Unicode (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="eb1ed-103">In C#, all strings in memory are encoded as Unicode (UTF-16).</span></span> <span data-ttu-id="eb1ed-104">Quand vous importez les données d’un support de stockage dans un objet `string`, les données sont automatiquement converties en UTF-16.</span><span class="sxs-lookup"><span data-stu-id="eb1ed-104">When you bring data from storage into a `string` object, the data is automatically converted to UTF-16.</span></span> <span data-ttu-id="eb1ed-105">Si les données contiennent uniquement des valeurs ASCII comprises entre 0 et 127, la conversion ne nécessite aucune intervention supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="eb1ed-105">If the data contains only ASCII values from 0 through 127, the conversion requires no extra effort on your part.</span></span> <span data-ttu-id="eb1ed-106">Toutefois, si le texte source contient des valeurs d’octets ASCII étendus (de 128 à 255), les caractères étendus sont interprétés par défaut en fonction de la page de codes actuelle.</span><span class="sxs-lookup"><span data-stu-id="eb1ed-106">However, if the source text contains extended ASCII byte values (128 through 255), the extended characters will be interpreted by default according to the current code page.</span></span> <span data-ttu-id="eb1ed-107">Pour spécifier que le texte source doit être interprété en fonction d’une page de codes différente, utilisez la classe <xref:System.Text.Encoding?displayProperty=fullName>, comme l’indique l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="eb1ed-107">To specify that the source text should be interpreted according to a different code page, use the <xref:System.Text.Encoding?displayProperty=fullName> class as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb1ed-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb1ed-108">Example</span></span>  
 <span data-ttu-id="eb1ed-109">L’exemple suivant indique comment convertir un fichier texte encodé au format ASCII 8’bits, en interprétant le texte source en fonction de la page de codes Windows 737.</span><span class="sxs-lookup"><span data-stu-id="eb1ed-109">The following example shows how to convert a text file that has been encoded in 8-bit ASCII, interpreting the source text according to Windows Code Page 737.</span></span>  
  
 <span data-ttu-id="eb1ed-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="eb1ed-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1ed-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb1ed-111">See Also</span></span>  
 [<span data-ttu-id="eb1ed-112">Chaînes</span><span class="sxs-lookup"><span data-stu-id="eb1ed-112">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

