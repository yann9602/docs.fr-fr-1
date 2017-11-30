---
title: "Copier et mettre à jour les Expressions d’enregistrement (F #)"
description: "Découvrez comment écrire une 'copie et mise à jour enregistrement expression' qui copie un existant, ces mises à jour spécifié de champs et retourne l’enregistrement mis à jour."
keywords: visual f#, f#, programmation fonctionnelle
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="7484e-104">Copie et mise à jour des expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="7484e-104">Copy and Update Record Expressions</span></span>

<span data-ttu-id="7484e-105">A *copier et mettre à jour des enregistrement expression* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et retourne l’enregistrement mis à jour.</span><span class="sxs-lookup"><span data-stu-id="7484e-105">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>


## <a name="syntax"></a><span data-ttu-id="7484e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7484e-106">Syntax</span></span>

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a><span data-ttu-id="7484e-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="7484e-107">Remarks</span></span>
<span data-ttu-id="7484e-108">Les enregistrements sont immuables par défaut, pour qu’il n’y a aucune mise à jour un enregistrement existant possibles.</span><span class="sxs-lookup"><span data-stu-id="7484e-108">Records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="7484e-109">Pour créer un enregistrement mis à jour tous les champs d’un enregistrement devra être spécifiées de nouveau.</span><span class="sxs-lookup"><span data-stu-id="7484e-109">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="7484e-110">Pour simplifier cette tâche une *copier et mettre à jour des enregistrement expression* peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="7484e-110">To simplify this task a *copy and update record expression* can be used.</span></span> <span data-ttu-id="7484e-111">Cette expression prend un enregistrement existant, crée un nouveau du même type à l’aide des champs spécifiés à partir de l’expression et le champ manquant spécifiées par l’expression.</span><span class="sxs-lookup"><span data-stu-id="7484e-111">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>
<span data-ttu-id="7484e-112">Cela peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines des valeurs du champ.</span><span class="sxs-lookup"><span data-stu-id="7484e-112">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="7484e-113">Prenons par exemple un enregistrement qui vient d’être créé.</span><span class="sxs-lookup"><span data-stu-id="7484e-113">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="7484e-114">Si vous deviez mettre à jour uniquement sur les champs de cet enregistrement, vous pouvez utiliser la *copier et mettre à jour des enregistrement expression* comme suit :</span><span class="sxs-lookup"><span data-stu-id="7484e-114">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="7484e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7484e-115">See Also</span></span>
[<span data-ttu-id="7484e-116">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="7484e-116">Records</span></span>](records.md)

[<span data-ttu-id="7484e-117">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="7484e-117">F# Language Reference</span></span>](index.md)
