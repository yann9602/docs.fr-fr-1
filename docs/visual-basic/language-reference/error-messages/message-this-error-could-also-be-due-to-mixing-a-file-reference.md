---
title: "&lt;message&gt; cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly &quot;&lt;assemblyname&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
dev_langs:
- VB
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c0908b1a13b9b9c54fb533201404987e479c6138
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="0635d-102">&lt;message&gt; cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly '&lt;assemblyname&gt;»</span><span class="sxs-lookup"><span data-stu-id="0635d-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="0635d-103">\<message > cette erreur peut résulter de la combinaison d’une référence de fichier avec une référence de projet à l’assembly '\<assemblyname >.</span><span class="sxs-lookup"><span data-stu-id="0635d-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="0635d-104">Dans ce cas, essayez de remplacer la référence de fichier pour '\<assemblyfilename >' projet '\<projectname1 >' avec une référence de projet à '\<projectname2 >'.</span><span class="sxs-lookup"><span data-stu-id="0635d-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="0635d-105">Code de votre projet accède à un membre d’un autre projet, mais la configuration de votre solution n’autorise pas la [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur à résoudre la référence.</span><span class="sxs-lookup"><span data-stu-id="0635d-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="0635d-106">Pour accéder à un type défini dans un autre assembly, le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur doit avoir une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="0635d-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="0635d-107">Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.</span><span class="sxs-lookup"><span data-stu-id="0635d-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="0635d-108">**ID d’erreur :** BC30971</span><span class="sxs-lookup"><span data-stu-id="0635d-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0635d-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0635d-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="0635d-110">Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer.</span><span class="sxs-lookup"><span data-stu-id="0635d-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="0635d-111">Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="0635d-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="0635d-112">Dans les propriétés de votre projet, ajoutez une référence au projet contenant l’assembly qui définit le type que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="0635d-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0635d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0635d-113">See Also</span></span>  
 <span data-ttu-id="0635d-114">[Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="0635d-114">[Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="0635d-115"> [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="0635d-115"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="0635d-116"> [NIB Guide pratique pour ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="0635d-116"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="0635d-117"> [NIB Comment : modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="0635d-117"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="0635d-118"> [Dépannage de références rompues](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="0635d-118"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
