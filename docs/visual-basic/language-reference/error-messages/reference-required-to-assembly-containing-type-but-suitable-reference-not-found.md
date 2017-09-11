---
title: "Référence à l’assembly requise &quot;&lt;assemblyidentity&gt;&quot;contenant le type&quot;&lt;typename&gt;», mais une référence appropriée est introuvable en raison de l’ambiguïté entre les projets&lt;projectname1&gt;&quot;et&quot;&lt;projectname2&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
dev_langs:
- VB
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
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
ms.openlocfilehash: bb5375366fa525a0ca9c16944d026ca499062ed8
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="68614-102">Référence à l’assembly requise '&lt;assemblyidentity&gt;'contenant le type'&lt;typename&gt;», mais une référence appropriée est introuvable en raison de l’ambiguïté entre les projets&lt;projectname1&gt;'et'&lt;projectname2&gt;»</span><span class="sxs-lookup"><span data-stu-id="68614-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="68614-103">Une expression utilise un type, comme une classe, une structure, une interface, une énumération ou un délégué, qui est défini en dehors de votre projet.</span><span class="sxs-lookup"><span data-stu-id="68614-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="68614-104">Cependant, des références de projet désignent plusieurs assemblys définissant ce type.</span><span class="sxs-lookup"><span data-stu-id="68614-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="68614-105">Les projets cités produisent des assemblys de même nom.</span><span class="sxs-lookup"><span data-stu-id="68614-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="68614-106">Par conséquent, le compilateur ne peut pas déterminer quel assembly utiliser pour le type auquel vous accédez.</span><span class="sxs-lookup"><span data-stu-id="68614-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="68614-107">Pour accéder à un type défini dans un autre assembly, le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur doit avoir une référence à cet assembly.</span><span class="sxs-lookup"><span data-stu-id="68614-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="68614-108">Il doit s’agir d’une référence unique et non équivoque qui ne provoque pas de références circulaires parmi des projets.</span><span class="sxs-lookup"><span data-stu-id="68614-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="68614-109">**ID d’erreur :** BC30969</span><span class="sxs-lookup"><span data-stu-id="68614-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68614-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="68614-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="68614-111">Identifiez le projet qui produit le meilleur assembly pour votre projet à référencer.</span><span class="sxs-lookup"><span data-stu-id="68614-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="68614-112">Pour prendre cette décision, vous pouvez utiliser des critères, tels que la facilité d’accès au fichier et la fréquence des mises à jour.</span><span class="sxs-lookup"><span data-stu-id="68614-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="68614-113">Dans vos propriétés de projet, ajoutez une référence au fichier contenant l’assembly qui définit le type que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="68614-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68614-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68614-114">See Also</span></span>  
 <span data-ttu-id="68614-115">[Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="68614-115">[Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="68614-116"> [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="68614-116"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="68614-117"> [NIB Guide pratique pour ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="68614-117"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="68614-118"> [NIB Comment : modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="68614-118"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="68614-119"> [Dépannage de références rompues](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="68614-119"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
