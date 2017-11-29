---
title: Error, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cd3245fd3e9e62b1b6443e9787c97808a0d179d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="error-statement"></a><span data-ttu-id="98311-102">Error, instruction</span><span class="sxs-lookup"><span data-stu-id="98311-102">Error Statement</span></span>
<span data-ttu-id="98311-103">Simule la présence d’une erreur.</span><span class="sxs-lookup"><span data-stu-id="98311-103">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98311-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98311-104">Syntax</span></span>  
  
```  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="98311-105">Composants</span><span class="sxs-lookup"><span data-stu-id="98311-105">Parts</span></span>  
 `errornumber`  
 <span data-ttu-id="98311-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="98311-106">Required.</span></span> <span data-ttu-id="98311-107">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="98311-107">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98311-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="98311-108">Remarks</span></span>  
 <span data-ttu-id="98311-109">La `Error` instruction est prise en charge pour la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="98311-109">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="98311-110">Dans le nouveau code, notamment lors de la création d’objets, utilisez la `Err` l’objet `Raise` méthode pour générer des erreurs d’exécution.</span><span class="sxs-lookup"><span data-stu-id="98311-110">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="98311-111">Si `errornumber` est défini, le `Error` instruction appelle le Gestionnaire d’erreurs après les propriétés de la `Err` objet affecté les valeurs par défaut suivantes :</span><span class="sxs-lookup"><span data-stu-id="98311-111">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="98311-112">Propriété</span><span class="sxs-lookup"><span data-stu-id="98311-112">Property</span></span>|<span data-ttu-id="98311-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="98311-113">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="98311-114">Valeur spécifiée en tant qu’argument à `Error` instruction.</span><span class="sxs-lookup"><span data-stu-id="98311-114">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="98311-115">Peut être n’importe quel numéro d’erreur valide.</span><span class="sxs-lookup"><span data-stu-id="98311-115">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="98311-116">Nom du projet Visual Basic actuel.</span><span class="sxs-lookup"><span data-stu-id="98311-116">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="98311-117">Expression de chaîne correspondant à la valeur de retour de la `Error` fonction spécifié `Number`, si cette chaîne existe.</span><span class="sxs-lookup"><span data-stu-id="98311-117">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="98311-118">Si la chaîne n’existe pas, `Description` contient une chaîne de longueur nulle ( » »).</span><span class="sxs-lookup"><span data-stu-id="98311-118">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="98311-119">Le lecteur complet, le chemin d’accès et le nom de fichier du fichier d’aide Visual Basic approprié.</span><span class="sxs-lookup"><span data-stu-id="98311-119">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="98311-120">ID de contexte pour l’erreur correspondant à l’aide de Visual Basic approprié du fichier le `Number` propriété.</span><span class="sxs-lookup"><span data-stu-id="98311-120">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="98311-121">Zéro.</span><span class="sxs-lookup"><span data-stu-id="98311-121">Zero.</span></span>|  
  
 <span data-ttu-id="98311-122">Si aucun gestionnaire d’erreur existe, ou si aucune n’est activée, un message d’erreur est créé et affiché à partir de la `Err` propriétés de l’objet.</span><span class="sxs-lookup"><span data-stu-id="98311-122">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98311-123">Certaines applications hôtes de Visual Basic ne peut pas créer des objets.</span><span class="sxs-lookup"><span data-stu-id="98311-123">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="98311-124">Consultez la documentation de votre application hôte pour déterminer si elle peut créer des classes et des objets.</span><span class="sxs-lookup"><span data-stu-id="98311-124">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98311-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="98311-125">Example</span></span>  
 <span data-ttu-id="98311-126">Cet exemple utilise la `Error` instruction à générer l’erreur numéro 11.</span><span class="sxs-lookup"><span data-stu-id="98311-126">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="98311-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="98311-127">Requirements</span></span>  
 <span data-ttu-id="98311-128">**Namespace :** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="98311-128">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="98311-129">**Assembly :** bibliothèque Visual Basic Runtime (dans Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="98311-129">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98311-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98311-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>  
 <xref:Microsoft.VisualBasic.Information.Err%2A>  
 <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>  
 [<span data-ttu-id="98311-131">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="98311-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)  
 [<span data-ttu-id="98311-132">Resume (instruction)</span><span class="sxs-lookup"><span data-stu-id="98311-132">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="98311-133">Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="98311-133">Error Messages</span></span>](../../../visual-basic/language-reference/error-messages/index.md)
