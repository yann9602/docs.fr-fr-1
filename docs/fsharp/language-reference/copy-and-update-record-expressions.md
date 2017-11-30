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
# <a name="copy-and-update-record-expressions"></a>Copie et mise à jour des expressions d’enregistrement

A *copier et mettre à jour des enregistrement expression* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et retourne l’enregistrement mis à jour.


## <a name="syntax"></a>Syntaxe

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>Remarques
Les enregistrements sont immuables par défaut, pour qu’il n’y a aucune mise à jour un enregistrement existant possibles. Pour créer un enregistrement mis à jour tous les champs d’un enregistrement devra être spécifiées de nouveau. Pour simplifier cette tâche une *copier et mettre à jour des enregistrement expression* peut être utilisé. Cette expression prend un enregistrement existant, crée un nouveau du même type à l’aide des champs spécifiés à partir de l’expression et le champ manquant spécifiées par l’expression.
Cela peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines des valeurs du champ.

Prenons par exemple un enregistrement qui vient d’être créé.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

Si vous deviez mettre à jour uniquement sur les champs de cet enregistrement, vous pouvez utiliser la *copier et mettre à jour des enregistrement expression* comme suit :

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>Voir aussi
[Enregistrements](records.md)

[Informations de référence du langage F#](index.md)
