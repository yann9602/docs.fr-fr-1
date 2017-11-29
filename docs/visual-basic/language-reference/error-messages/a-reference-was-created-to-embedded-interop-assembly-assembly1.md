---
title: "Une référence a été créée pour l’assembly d’interopérabilité incorporé &#39; &lt;assembly1&gt;&#39; en raison d’une référence indirecte à cet assembly à partir d’assembly &#39;&lt; Assembly2&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40059
- bc40059
helpviewer_keywords:
- VBC40059
- BC40059
ms.assetid: 520e39cb-8ab6-46f5-aa00-08afd51b4b7c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bc2fbb044fc839aa24abf3dc1ea864457efb0653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="a-reference-was-created-to-embedded-interop-assembly-39ltassembly1gt39-because-of-an-indirect-reference-to-that-assembly-from-assembly-39ltassembly2gt39"></a>Une référence a été créée pour l’assembly d’interopérabilité incorporé &#39; &lt;assembly1&gt;&#39; en raison d’une référence indirecte à cet assembly à partir d’assembly &#39;&lt; Assembly2&gt;&#39;
Une référence a été créée pour l’assembly d’interopérabilité incorporé '\<assembly1>' en raison d’une référence indirecte à cet assembly à partir de l’assembly '\<assembly2>'. Modifiez la propriété 'Incorporer les types interop' pour l’un des assemblys.  
  
 Vous avez ajouté une référence à un assembly (assembly1) avec une valeur de propriété `Embed Interop Types` égale à `True`. Cela indique au compilateur d’incorporer les informations de type interop à partir de cet assembly. Toutefois, le compilateur ne peut pas incorporer les informations de type interop à partir de cet assembly, car un autre assembly que vous avez référencé (assembly2) fait également référence à cet assembly (assembly1) et a la propriété `Embed Interop Types` définie sur `False`.  
  
> [!NOTE]
>  L’affectation de la valeur `True` à la propriété `Embed Interop Types` d’une référence d’assembly revient à référencer l’assembly en utilisant l’option `/link` pour le compilateur de ligne de commande.  
  
 **ID d’erreur :** BC40059  
  
### <a name="to-address-this-warning"></a>Pour traiter cet avertissement  
  
-   Pour incorporer des informations de type interop pour les deux assemblys, affectez la valeur `True` à la propriété `Embed Interop Types` de toutes les références à assembly1.  
  
-   Pour supprimer cet avertissement, vous pouvez affecter à la propriété `Embed Interop Types` d’assembly1 la valeur `False`. Dans ce cas, les informations de type d’interopérabilité sont fournies par un assembly PIA (PIA).  
  
## <a name="see-also"></a>Voir aussi  
 [/link (Visual Basic)](../../../visual-basic/reference/command-line-compiler/link.md)  
 [Programmation avec des assemblys PIA](http://msdn.microsoft.com/en-us/306fa1d6-0703-4004-9e93-d0a57f1be81e)
