---
title: "Namespace ou le type spécifié dans les Imports&quot; au niveau du projet&lt;qualifiedelementname&gt;&quot; ne contient aucun membre public ou est introuvable | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40057
- bc40057
dev_langs:
- VB
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
caps.latest.revision: 10
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
ms.openlocfilehash: 301e2bd419f0b4723ff76c2bdd2187c4c412e174
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="namespace-or-type-specified-in-the-project-level-imports-39ltqualifiedelementnamegt39-doesn39t-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="16d80-102">Namespace ou le type spécifié dans les Imports' au niveau du projet&lt;qualifiedelementname&gt;' ne contient aucun membre public ou est introuvable</span><span class="sxs-lookup"><span data-stu-id="16d80-102">Namespace or type specified in the project-level Imports &#39;&lt;qualifiedelementname&gt;&#39; doesn&#39;t contain any public member or cannot be found</span></span>
<span data-ttu-id="16d80-103">Namespace ou le type spécifié dans les Imports' au niveau du projet\<qualifiedelementname >' ne contient aucun membre public ou est introuvable.</span><span class="sxs-lookup"><span data-stu-id="16d80-103">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="16d80-104">Assurez-vous que l’espace de noms ou le type est défini et contient au moins un membre public.</span><span class="sxs-lookup"><span data-stu-id="16d80-104">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="16d80-105">Assurez-vous que le nom d’alias ne contient d’autres alias.</span><span class="sxs-lookup"><span data-stu-id="16d80-105">Make sure the alias name doesn't contain other aliases.</span></span>  
  
 <span data-ttu-id="16d80-106">Une propriété Imports d’un projet spécifie un élément conteneur qui ne peut pas être trouvé ou ne définit pas `Public` membres.</span><span class="sxs-lookup"><span data-stu-id="16d80-106">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>  
  
 <span data-ttu-id="16d80-107">A *contenant l’élément* peut être un espace de noms, classe, structure, module, interface ou énumération.</span><span class="sxs-lookup"><span data-stu-id="16d80-107">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="16d80-108">L’élément conteneur contient des membres, tels que des variables, des procédures ou d’autres éléments qui le contient.</span><span class="sxs-lookup"><span data-stu-id="16d80-108">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>  
  
 <span data-ttu-id="16d80-109">L’objectif de l’importation consiste à permettre à votre code pour accéder aux membres de type ou d’espace de noms sans devoir les qualifier.</span><span class="sxs-lookup"><span data-stu-id="16d80-109">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="16d80-110">Votre projet devrez peut-être également ajouter une référence à l’espace de noms ou type.</span><span class="sxs-lookup"><span data-stu-id="16d80-110">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="16d80-111">Pour plus d’informations, consultez « Importation d’éléments conteneurs » dans [références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="16d80-111">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
 <span data-ttu-id="16d80-112">Si le compilateur ne peut pas trouver l’élément conteneur spécifié, il ne peut pas résoudre les références qui l’utilisent.</span><span class="sxs-lookup"><span data-stu-id="16d80-112">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="16d80-113">S’il trouve l’élément mais l’élément n’expose pas `Public` membres, aucune référence peut être réussie.</span><span class="sxs-lookup"><span data-stu-id="16d80-113">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="16d80-114">Dans les deux cas, il n’a aucune signification pour importer l’élément.</span><span class="sxs-lookup"><span data-stu-id="16d80-114">In either case it is meaningless to import the element.</span></span>  
  
 <span data-ttu-id="16d80-115">Vous utilisez la **Concepteur de projet** pour spécifier les éléments à importer.</span><span class="sxs-lookup"><span data-stu-id="16d80-115">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="16d80-116">Utilisez le **espaces de noms importés** section de la **références** page.</span><span class="sxs-lookup"><span data-stu-id="16d80-116">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="16d80-117">Vous pouvez accéder à la **Concepteur de projet** en double-cliquant sur le **mon projet** icône dans **l’Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="16d80-117">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>  
  
 <span data-ttu-id="16d80-118">**ID d’erreur :** BC40057</span><span class="sxs-lookup"><span data-stu-id="16d80-118">**Error ID:** BC40057</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="16d80-119">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="16d80-119">To correct this error</span></span>  
  
1.  <span data-ttu-id="16d80-120">Ouvrez la **Concepteur de projets** et basculez vers le **référence** page.</span><span class="sxs-lookup"><span data-stu-id="16d80-120">Open the **Project Designer** and switch to the **Reference** page.</span></span>  
  
2.  <span data-ttu-id="16d80-121">Dans le **espaces de noms importés** section, vérifiez que l’élément conteneur est accessible à partir de votre projet.</span><span class="sxs-lookup"><span data-stu-id="16d80-121">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>  
  
3.  <span data-ttu-id="16d80-122">Vérifiez que l’élément conteneur expose au moins un `Public` membre.</span><span class="sxs-lookup"><span data-stu-id="16d80-122">Verify that the containing element exposes at least one `Public` member.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16d80-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16d80-123">See Also</span></span>  
 <span data-ttu-id="16d80-124">[Page Références, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="16d80-124">[References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="16d80-125"> [NIB Comment : modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="16d80-125"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="16d80-126"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="16d80-126"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="16d80-127"> [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="16d80-127"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="16d80-128"> [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="16d80-128"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
