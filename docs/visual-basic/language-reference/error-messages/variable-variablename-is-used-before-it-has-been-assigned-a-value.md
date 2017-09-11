---
title: "Variable &quot;&lt;variablename&gt;&quot; est utilisée avant qu’il a reçu une valeur | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
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
ms.openlocfilehash: dfc924ebbebb8b20654156b8871684dcfad6848a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a><span data-ttu-id="2ecd0-102">Variable '&lt;variablename&gt;' est utilisée avant qu’il a reçu une valeur</span><span class="sxs-lookup"><span data-stu-id="2ecd0-102">Variable &#39;&lt;variablename&gt;&#39; is used before it has been assigned a value</span></span>
<span data-ttu-id="2ecd0-103">Variable '\<variablename >' est utilisée avant qu’il a reçu une valeur.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-103">Variable '\<variablename>' is used before it has been assigned a value.</span></span> <span data-ttu-id="2ecd0-104">Cela peut provoquer une exception de référence null au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-104">A null reference exception could result at run time.</span></span>  
  
 <span data-ttu-id="2ecd0-105">Une application a au moins un chemin d’accès possible via son code qui lit une variable avant toute valeur lui est attribuée.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-105">An application has at least one possible path through its code that reads a variable before any value is assigned to it.</span></span>  
  
 <span data-ttu-id="2ecd0-106">Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-106">If a variable has never been assigned a value, it holds the default value for its data type.</span></span> <span data-ttu-id="2ecd0-107">Pour un type de données de référence, cette valeur par défaut est [rien](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="2ecd0-107">For a reference data type, that default value is [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span> <span data-ttu-id="2ecd0-108">Lecture d’une variable de référence qui a la valeur `Nothing` peut entraîner une <xref:System.NullReferenceException>dans certaines circonstances.</xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="2ecd0-108">Reading a reference variable that has a value of `Nothing` can cause a <xref:System.NullReferenceException> in some circumstances.</span></span>  
  
 <span data-ttu-id="2ecd0-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-109">By default, this message is a warning.</span></span> <span data-ttu-id="2ecd0-110">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2ecd0-110">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2ecd0-111">**ID d’erreur :** compilation BC42104</span><span class="sxs-lookup"><span data-stu-id="2ecd0-111">**Error ID:** BC42104</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2ecd0-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2ecd0-112">To correct this error</span></span>  
  
-   <span data-ttu-id="2ecd0-113">Vérifiez votre logique de flux de contrôle et assurez-vous que la variable a une valeur valide avant que le contrôle passe à toute instruction qui le lit.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-113">Check your control flow logic and make sure the variable has a valid value before control passes to any statement that reads it.</span></span>  
  
-   <span data-ttu-id="2ecd0-114">Pour garantir que la variable a toujours une valeur valide doit initialiser dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="2ecd0-114">One way to guarantee that the variable always has a valid value is to initialize it as part of its declaration.</span></span> <span data-ttu-id="2ecd0-115">Consultez « Initialisation » dans [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2ecd0-115">See "Initialization" in [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecd0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ecd0-116">See Also</span></span>  
 <span data-ttu-id="2ecd0-117">[Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2ecd0-117">[Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="2ecd0-118"> [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="2ecd0-118"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="2ecd0-119"> [Dépannage des variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span><span class="sxs-lookup"><span data-stu-id="2ecd0-119"> [Troubleshooting Variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)</span></span>
